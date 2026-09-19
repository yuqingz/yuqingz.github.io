# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal academic/portfolio website for Yuqing Zhou (research scientist at Toyota Research Institute of North America), served as a static site from GitHub Pages at `yuqingz.github.io`. There is no build system, package manager, or framework — every page is a single self-contained `.html` file with inline `<style>` and `<script>` tags.

## Development workflow

There is no build/lint/test tooling. To preview changes, open the HTML files directly in a browser (e.g. `open index.html`) or serve the directory locally (e.g. `python3 -m http.server`). Changes go live by committing and pushing to `main`, which GitHub Pages serves directly.

## Site structure

- `index.html` — homepage: bio, research highlights, publications list, services/teaching
- `blog.html` — blog index listing posts (date, title, snippet, link) in reverse-chronological order
- `post/*.html` — individual blog posts, named `YYYY-MM-DD-slug.html`
- `resume.html` — resume/CV page
- `doc/*.pdf` — paper PDFs linked from the publications section (used when no external publisher link exists)
- `img/*.png` / `img/photo.jpeg` — publication figures and profile photo, referenced by year-coded filenames matching each publication (e.g. `img/2025smo.png` for the 2025 SMO paper)
- `sitemap.xml`, `google8601ea6cb8b7a94c.html` — SEO/search console files

## Conventions to follow when editing pages

Every top-level page (`index.html`, `blog.html`, `resume.html`, `post/*.html`) repeats the same scaffolding rather than sharing a layout/template — when adding a new page or post, copy an existing one of the same kind as a starting point rather than building from scratch:

- Google Analytics gtag snippet (`G-ZWT1SW2G39`) is duplicated verbatim at the top of every page's `<head>`.
- A sticky `.top-nav` / `.top-nav-inner` bar with Toyota-red (`#EB0A1E`) background links back to `index.html` (or `blog.html` from a post).
- Shared visual language: `.page` max-width 960px centered container, system font stack, `#fafafa` background, `#0066cc` links. Blog posts additionally load MathJax via CDN (`tex-chtml.js`) for inline math and use a `.solution-box` callout style.
- New blog posts must be added in two places: a new `post/YYYY-MM-DD-slug.html` file, and a corresponding `<li class="post-item">` entry prepended (newest first) to the list in `blog.html`.
- New publications on `index.html` follow the existing `.pub-item` pattern (figure + year/title/authors/venue/links) and expect a matching cover image added to `img/`.
- The site must stay readable on both desktop and mobile. Any layout change (new sections, columns, images) needs a corresponding rule in the existing `@media (max-width: 900px)` / `@media (max-width: 600px)` breakpoints, and should be checked at a narrow viewport (e.g. ~390px) before considering the change done.
