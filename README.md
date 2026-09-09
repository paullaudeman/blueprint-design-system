# Blueprint

The design system behind [laudeman.io](https://laudeman.io). The palette is navy and aubergine.

An engineering drawing rather than a poster: a faint crosshatched grid under everything, hairline
rules instead of boxes, translucent cards floating over the grid, and monospace labels that read as
annotation rather than headline.

```css
/* Palette - navy + aubergine */
--navy:      #1f3a5f;   /* primary - headings, links, the grid's hue */
--navy-deep: #16293f;   /* hover and pressed */
--plum:      #5e3458;   /* accent, and every focus outline */
--charcoal:  #333333;   /* body */
--slate:     #555555;   /* secondary, metadata, captions */

/* Blueprint surfaces */
--bg:        #f4f5f3;                     /* cool off-white, not cream */
--surface:   rgba(255,255,255,.72);       /* glass over the grid */
--grid-line: rgba(31,58,95,.05);          /* the drafting grid */
--hairline:  #c7cdc0;                     /* every border */
```

Full token set: [`tokens.css`](tokens.css).

---

## Why write it down

The name lived only in a comment at the top of the stylesheet:

```
laudeman.io - Blueprint design system
IBM Plex Sans + Mono, faint engineering grid, hairline
cards, bracketed mono section labels. Palette: navy
+ aubergine from the colour reference doc.
Mobile-first. Single stylesheet by design.
```

That name was load-bearing and unfindable. In September 2026 a redesign was proposed - an ukiyo-e
woodblock skin - that would have replaced the system without noticing it *was* a system. The hex
values were read; the comment naming them was not.

A design system nobody can find is a set of coincidences waiting to be overwritten.

## What it is not

| Not | Why the distinction matters |
|-----|-----------------------------|
| **Flat design** | Absence of `box-shadow` is shared by every flat site since 2013. Here it follows from the drawing metaphor, not from a style trend. |
| **Japanese minimalism** | It is frequently mistaken for it. The one cultural reference on the site is scoped to a single section, beside the practice it refers to. Extending it site-wide would turn homage into costume. |
| **A Swiss grid** | It shares the grammar - IBM Plex descends from Helvetica, which is Swiss - but Swiss composition is asymmetric, and this system still centres its container. See Open questions. |
| **Themeable** | One palette, one stylesheet, by design. There is no dark mode, and adding one is not a small change. |

## Rules

- **Single stylesheet, by design.** One file, mobile-first. Do not split it.
- **Hairlines, not boxes.** 20 of 25 border declarations are `1px`. Weight is the exception.
- **No shadows.** Zero `box-shadow`, zero `text-shadow`. Depth comes from the glass surfaces.
- **Space comes from the dial.** Use `--space-*`, never a raw rem in a gap.
- **Mono is annotation.** Labels, data, captions. Never running text.
- **Colour is structural.** Navy for hierarchy, plum for focus and accent, slate for secondary.
  No decorative colour, and no semantic red or green.

## Two things that will bite you

**`--plum` is not free to change.** Four of its 25 uses are `outline: 2px solid var(--plum)` on
focus. It was chosen - consciously or not - because it is *not* a semantic colour. Swap it for any
red and every focus ring reads as an error state, while contrast on `--bg` drops from roughly
9.1:1 to under 6:1.

**The surfaces are glass.** `--surface` at `.72` means the drafting grid shows through every card.
Warming `--bg` toward cream turns them milky and puts the cool `--hairline` visibly wrong against
it. A ground change is a re-derivation of every token, not a one-line edit.

## Open questions

- **Centring is the least considered line in the system.** `margin-inline: auto` is the web's
  default rather than a decision, and it is the one thing both Swiss and ukiyo-e composition
  reject - in both, negative space is *placed* rather than left over. Weighting content off-axis
  is the cheapest available change with the largest effect, and needs no new tokens.
- **Make the ornament be measurement.** A footer colophon carrying real build figures, and
  dimension lines annotating one project card with that card's true values. Uncopyable, because
  the numbers belong to the site.

---

## Usage

```html
<link rel="stylesheet" href="tokens.css">
```

The type stack expects [IBM Plex Sans and IBM Plex Mono](https://github.com/IBM/plex), which are
open source under the SIL Open Font License.

Take the tokens, take the rules, or take the idea that a design system should say its own name out
loud where someone will find it.

*Recorded September 2026. Token counts drift - re-count before trusting them.*
