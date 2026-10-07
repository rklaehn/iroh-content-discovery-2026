# iroh global content discovery talk 2026

A ~10 minute talk version of the [iroh global content discovery][post] blog
post. Markdown slide deck built into a single self-contained HTML file with
the animated SVG diagrams from [iroh.computer][iroh-computer] inlined.

## Build

```
cargo run          # index.md -> docs/index.html
```

To preview, open `docs/index.html` in a browser.

## Export

```
./export-pdf.sh
```

Writes `iroh.pdf`, one page per slide, via a headless Chromium-based browser
(Brave/Chrome/Edge — whatever is installed). Animated diagrams are frozen at
their initial frame; the HTML file stays the real presentation.

## Present

Arrow keys / space / click to navigate, `f` for fullscreen, `r` to restart
the current slide's animations (they also restart automatically on slide
entry). The slide number is in the URL hash, so reloading keeps your place.

## Editing

- `index.md` — the slides, separated by `---`. Fenced code blocks are
  syntax-highlighted at build time. Images referencing local `.svg` files
  are inlined into the output (ids get namespaced per slide so SMIL
  animations don't collide), local `.png` files are inlined as data URIs.
  `![w:900](x.svg)` pins the display width; `<!-- center -->` centers a
  slide. Reference-style link definitions are shared across all slides.
- `scripts/*.gen.py` — the SVG generators, copied from the
  [iroh.computer repo][iroh-computer]. Edit and run e.g.
  `python3 scripts/announce-peer-dht.gen.py`; each writes its SVG to
  `public/animations/`, then rebuild with `cargo run`.

[post]: https://www.iroh.computer/blog/iroh-global-content-discovery
[iroh-computer]: https://github.com/n0-computer/iroh.computer
