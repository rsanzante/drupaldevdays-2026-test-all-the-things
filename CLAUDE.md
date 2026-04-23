# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a **reveal.js** presentation framework repository - a tool for creating HTML-based slide presentations. This specific instance contains a DrupalCon Vienna presentation titled "Test all the things!" by Ricardo Sanz Ante.

Ignore all stuff elated on reveal.js, the only important file is index.html where hte presentation redides.

### Presentation Structure

HTML presentations follow this pattern:
```html
<div class="reveal">
  <div class="slides">
    <section>Slide 1</section>
    <section>Slide 2</section>
    <section>
      <section>Vertical 1</section>
      <section>Vertical 2</section>
    </section>
  </div>
</div>
```

Each `<section>` is a slide. Nested `<section>` elements create vertical slides.

Data attributes control behavior:
- `data-state` - Apply custom state/styling
- `data-background-*` - Control slide backgrounds
- `data-transition` - Slide transition effects
- `data-auto-animate` - Auto-animate between slides

### Configuration

Presentations initialize reveal.js in their HTML:
```javascript
Reveal.initialize({
  controls: true,
  progress: true,
  hash: true,
  plugins: [ RevealMarkdown, RevealHighlight, RevealNotes ]
});
```

Modern API (4.0+) supports multiple instances:
```javascript
let deck = new Reveal(document.querySelector('.reveal'), { controls: false });
deck.initialize();
```

### Testing

QUnit tests in `test/*.html` cover:
- Auto-animate functionality
- Plugin system and dependencies
- Multiple instances
- State management
- Grid navigation
- Markdown parsing
- PDF export
- Scroll mode
- iframes and backgrounds

Tests run via Puppeteer with a temporary local server on port 8009.

## Custom Presentation (index.html)

This repository contains a customized presentation with:
- Custom CSS: `assets/css/custom2024.css`
- Custom fonts (Impact, Hennigar from CDN)
- Custom images in `assets/images/`
- DrupalCon Vienna event branding
- White theme base (`dist/theme/white.css`)

When modifying the presentation, edit `index.html` directly. The dev server watches HTML/MD files and reloads automatically.
