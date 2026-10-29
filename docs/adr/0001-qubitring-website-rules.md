# ADR 0001: Qubitring Website Rules

- Status: Accepted
- Date: 2026-10-29
- Decision owners: Qubitring website owner

## Context

The Qubitring website is a public, multilingual consulting site hosted with
GitHub Pages. Its content, legal pages, client references, and responsive
behavior need to remain consistent across languages and devices.

This ADR records the product and implementation rules established for the
website. It describes intended behavior; it does not certify that every
historical page or deployment currently conforms.

## Decisions

### 1. Hosting and page structure

- The canonical public site is `https://qubitring.github.io/`, published from
  the `main` branch of `qubitring/qubitring.github.io`.
- Keep the site static and compatible with GitHub Pages; do not require a
  server-side runtime to render pages.
- English is the default homepage at `/`.
- German, Filipino, and Chinese homepages are available at `/de/`, `/fil/`, and
  `/zh/`, respectively.
- Shared site images belong in `/assets/`; reference logos belong in
  `/assets/references/`.

### 2. Language behavior

- Provide a language selector in the header on each localized page.
- Selecting a language opens the equivalent page in that language, using the
  root path for English and the language paths above for the other versions.
- Keep each language's page content, navigation labels, and legal links in the
  selected language. Do not send a visitor to a missing localized route.
- When adding or changing homepage content, update all four language versions
  in the same change.

### 3. Responsive layout and media

- Support narrow mobile screens, including portrait orientation, without
  horizontal page overflow.
- Constrain hero artwork and other images to their layout containers; intrinsic
  image dimensions must not force a wider grid or page.
- Allow long translated headings and text to wrap on small screens.
- Keep cards and navigation usable at both desktop and mobile sizes.
- Place the hero artwork above the hero text on both desktop and mobile, in
  both visual and document order.
- Preserve the supplied logo artwork and use image formats and file extensions
  that match the actual encoded files.

### 4. Homepage content

- The expertise section contains six competencies:
  1. Digital Transformation & AI
  2. Process Mining & RPA
  3. Payment Architecture & Solutions
  4. SAP / ERP Transformation
  5. M&A IT & Process Integration
  6. Presales and Delivery Scaling
- The sixth competency covers building presales teams, scaling software
  delivery teams in SaaS and on-premises environments, and establishing an
  effective Business as Usual (BAU) organization.
- Keep the expertise count and section heading synchronized with the number of
  cards in every language.
- Do not add back the header consultation button, the hero "discover services"
  button, or the "all services in detail" link that were explicitly removed.
- Keep existing section navigation and contact links functional.

### 5. References and brand assets

- The references section contains four client cards: LINDE PLC, GK SOFTWARE,
  AYE4FIN, and KPMG / CORPORATE.
- Use the supplied client logos in their corresponding cards in every language.
- Display logos inside consistent white logo bars, using contain-style sizing
  so complete marks remain visible without distortion or cropping.
- Do not use a dark tile behind the GK logo; its current supplied logo is
  designed to display on white.
- Keep each client's accompanying case-study text with its corresponding logo.

### 6. Legal pages

- Maintain an Impressum and a privacy page in English, German, Filipino, and
  Chinese.
- Link each localized homepage footer to the matching localized legal pages.
- Use the Q logo from the homepage in the Impressum header.
- Keep legal content aligned with the actual site behavior and contact details;
  do not imply that the text is professional legal advice.

### 7. Changes and verification

- Apply coordinated content or asset changes across all affected locales.
- Publish related page and asset updates together so a deployment does not
  expose pages that point to missing or incorrectly encoded assets.
- After publishing, verify that the GitHub Pages build succeeds.
- Check that `/`, `/de/`, `/fil/`, and `/zh/` load successfully and contain the
  expected localized content.
- For image changes, verify both the public asset response and rendered image.
- For layout changes, check mobile portrait widths and confirm there is no
  horizontal overflow.

## Consequences

- The static structure is simple to host and maintain, but equivalent pages
  require coordinated edits across four files.
- The translation and route rules reduce ambiguity for language switching, but
  every new page must be added to all required localized routes.
- Publishing and checking a complete change set takes longer than updating one
  page, while reducing the risk of broken links, inconsistent translations,
  and partially deployed assets.
