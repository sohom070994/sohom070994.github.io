# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Site

This is **Gargi Deshpande's academic portfolio website** — a one-page Jekyll site built on the [Shahada Academic Jekyll Theme](https://github.com/avicndugu/jekyll-shahada-theme). It is deployed via GitHub Pages at the domain specified in `CNAME`.

## Development Commands

```bash
# Install dependencies
bundle install

# Run local dev server (available at http://localhost:4000)
bundle exec jekyll serve

# Build static site (outputs to _site/)
bundle exec jekyll build
```

> Note: `_config.yml` is NOT hot-reloaded. Restart the server after editing it.

## Architecture

All content is data-driven — almost nothing is hard-coded in HTML templates.

### Content Layer (edit these to update the site)

- **`_data/hometext.yml`** — The single source of truth for all page content: bio, projects, teaching, education, publications, work experience, contact links, and awards. Each top-level key corresponds to a section include.
- **`_data/navigation.yml`** — Navigation bar links (section anchors). To add/remove nav items, edit this file.
- **`assets/pdf/`** — PDF files (resume, etc.). The resume path is referenced in `_data/hometext.yml` under `header.buttons`.
- **`assets/images/`** — Profile photo and icon images. Profile image path is set in `_data/hometext.yml` under `header.image`.

### Template Layer

- **`_layouts/default.html`** — Base layout: wraps nav + content + footer.
- **`_layouts/home.html`** — Defines section order by listing `{% include %}` calls. To reorder or hide sections, edit here.
- **`_includes/*.html`** — One file per section (hero, education, publications, work, projects, teaching, awards, contact, nav, footer, head). Each reads from `site.data.hometext`.
- **`index.md`** — Entry point; uses the `home` layout. Contains no content itself.

### Styling

- **`_sass/`** — Contains Bootstrap SCSS and custom overrides. Sass is compiled to `assets/main.css` at build time (`_config.yml` sets `sass.style: :compressed`).

### Sections toggleable via YAML comments

Several sections exist in `_data/hometext.yml` but are commented out (news, affiliations). To enable them: uncomment the data in `hometext.yml` and uncomment the corresponding `{% include %}` line in `_layouts/home.html`.
