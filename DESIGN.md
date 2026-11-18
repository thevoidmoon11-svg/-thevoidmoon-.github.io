# DESIGN.md — Brajraj Singh Songara · Website Designer

> Design system for the single-page portfolio.
> **Source of truth:** values below are extracted from `index.html` in the repo (`-thevoidmoon-.github.io-main`). Items marked *(recommended)* are not in the code yet and are suggestions.

---

## 1. Brand Overview

| | |
|---|---|
| **Live site** | [https://thevoidmoon11-svg.github.io/-thevoidmoon-.github.io/](https://thevoidmoon11-svg.github.io/-thevoidmoon-.github.io/) |
| **Name** | Brajraj Singh Songara (wordmark `braj` + gradient `saa`; Instagram `@brajsaa_23`) |
| **Role** | Website designer who also builds (design, front-end, motion) |
| **Tagline** | Designing websites people remember. |
| **Positioning** | Clean, modern, high-converting websites, end to end, 1:1 collaboration |
| **Visual language** | Dark monochrome glassmorphism: frosted translucent panels, soft ambient orbs, silver gradient accents |
| **Primary goal** | Turn Instagram link-in-bio traffic into project inquiries |
| **Primary CTA** | Start a project ↗ → `mailto:the.voidmoon11@gmail.com` |
| **Secondary CTA** | View my work → `#work` |

### Principles
1. **Intentional, never default.** Layout, type, motion and color are chosen on purpose.
2. **First three seconds.** Each screen answers: what should this person feel right now?
3. **Premium but fast.** Glass and motion must not cost load speed or scroll smoothness.
4. **The site is the portfolio.** Polish is the proof.
5. **One clear action per viewport.** Contact is always one tap away.

### Voice
First person, confident, plain-spoken, short declarative sentences. Headlines state a belief or benefit. Sentence case. Uppercase letter-spaced eyebrow labels.

---

## 2. Information Architecture

| # | Section | Anchor | Purpose |
|---|---|---|---|
| 1 | Nav | — | Wordmark, anchors, "Say hello" |
| 2 | Hero | top | Availability, H1, subcopy, CTAs, framed video |
| 3 | About | `#about` | Philosophy + 3 stat cards |
| 4 | What I do | `#work` | 4 service cards |
| 5 | Free Tools | `#tools` | 10-slide swipe carousel |
| 6 | Prompt Library | `#prompts` | Why/How steps, copyable prompt, rule of thumb |
| 7 | Contact | `#contact` | Email + Instagram |
| 8 | Footer | — | Copyright, handle |

---

## 3. Design Tokens (from code)

### 3.1 Color

```css
:root{
  --bg:               #06060a;
  --bg-soft:          #0b0b13;
  --glass:            rgba(255,255,255,0.06);
  --glass-border:     rgba(255,255,255,0.14);
  --glass-highlight:  rgba(255,255,255,0.35);
  --violet:           #ffffff;   /* legacy name, now white */
  --cyan:             #b8b8c2;   /* legacy name, now light silver */
  --pink:             #6e6e78;   /* legacy name, now mid grey */
  --text:             #f4f3f8;
  --muted:            #9a97ac;
  --grad: linear-gradient(120deg, #ffffff, #b8b8c2 55%, #6e6e78);
}
```

| Role | Token | Notes |
|---|---|---|
| Page background | `--bg` | Near-black with a cool tint |
| Panels | `--glass` + `--glass-border` | Always paired with blur |
| Top-edge light | `--glass-highlight` | Inset 1px highlight on glass |
| Body text | `--text` | |
| Secondary text | `--muted` | Descriptions, labels, nav links |
| Accent | `--grad` | Gradient text, primary buttons, icon chips, step numbers |
| Eyebrow label | `--cyan` | Section eyebrows |
| Text on gradient | `#0b0b13` | Dark text on primary buttons and chips |

Tag/outline surfaces: `rgba(255,255,255,.05)` fill, `rgba(255,255,255,.10)` border. Footer/nav divider: `rgba(255,255,255,.06)`. Selection: white background.

**Cleanup *(recommended)*:** rename `--violet/--cyan/--pink` to `--accent-1/2/3` (or `--silver-100/300/500`). The names say color but the values are greyscale, which will confuse future edits. One leftover: `.work-card:hover` still uses a violet shadow `rgba(124,92,255,.2)`, which is the only off-palette color in the file; change it to `rgba(255,255,255,.15)` to match.

### 3.2 Typography

Fonts (Google Fonts): **Sora** 300–800 for display, **Inter** 300–600 for body.

| Role | Family | Weight | Size | Other |
|---|---|---|---|---|
| H1 `.title` | Sora | 700 | `clamp(2.3rem, 6.4vw, 5.4rem)` | line-height 1.04, tracking -0.02em, max-width 960px |
| H2 | Sora | 600 | `clamp(1.8rem, 3.6vw, 3rem)` | line-height 1.1, tracking -0.015em |
| H3 (cards) | Sora | 600 | 1.2rem | |
| H4 (steps) | Sora | 600 | 1.05rem | |
| Wordmark | Sora | 700 | 1.05rem | tracking .02em |
| Stat number | Sora | 700 | 2.4rem | gradient text |
| Body | Inter | 400 | 1.05rem | line-height 1.7–1.85, color `--muted` |
| Hero subcopy | Inter | 400 | 1.08rem | max-width 560px |
| Eyebrow label | Inter | 600 | .78rem | uppercase, tracking .16em, `--cyan` |
| Nav link | Inter | 500 | .88rem | tracking .02em |
| Button | Inter | 600 | .92rem | |
| Tag | Inter | 400 | .72rem | |
| Prompt text | Inter | 400 | .94rem | line-height 1.9, `pre-wrap` |

Base: `-webkit-font-smoothing: antialiased`. Add `font-display: swap` is already set via the Google Fonts URL (`display=swap`).

### 3.3 Spacing, radius, elevation

| Token | Value |
|---|---|
| Section padding | `140px 6%` (hero: `150px 6% 90px`) |
| Section head | max-width 640px, margin-bottom 70px |
| Horizontal page gutter | 6% (5% hero on mobile) |
| Card padding | 28–44px (stat 28/30, work 34, step 32, prompt 38, about 44, contact 70/60) |
| Grid gaps | work 28px, steps 24px, about 50px, stats 18px |
| Radius | tag/pill 999px · button 16px · icon chip 14px (step chip 10px) · card 24px · carousel 26px · hero frame 28px (20px mobile) |
| Glass blur | cards `blur(24px) saturate(180%)` · buttons `blur(20px) saturate(180%)` · pill/eyebrow `blur(14px)` · nav (scrolled) `blur(18px) saturate(160%)` |
| Card shadow | `inset 0 1px 0 var(--glass-highlight), 0 20px 60px rgba(0,0,0,.35)` |
| Hero frame shadow | `inset 0 1px 0 var(--glass-highlight), 0 40px 100px rgba(0,0,0,.55)` |
| Button shadow | `inset 0 1px 0 var(--glass-highlight), 0 8px 30px rgba(0,0,0,.35)` |

### 3.4 Motion

Easing everywhere: `cubic-bezier(.16, 1, .3, 1)` (a strong ease-out).

| Pattern | Spec |
|---|---|
| Hero entrance | Staggered `rise` (opacity 0→1, translateY 16–26px→0): eyebrow .1s, H1 .25s, subcopy .4s, actions .55s; frame uses `rise-scale` at .5s (translateY 36px, scale .97) |
| Scroll reveal | `.reveal` fades in and rises 40px over .9s, triggered once by IntersectionObserver at 15% threshold |
| Card hover | `translateY(-8px)`, border to `rgba(255,255,255,.28)` |
| Button hover | `translateY(-3px)`, brighter glass |
| Nav links | Underline grows 0→100% width (gradient) in .3s |
| Nav on scroll | After 40px: padding 24→16px, blur + `rgba(6,6,10,.45)` background |
| Gradient text | H1 `.grad` shifts `background-position` over 6s, infinite |
| Availability dot | White dot with glow, opacity pulse 2s |
| Scroll cue | Line scales in/out, 1.8s loop |
| Ambient orbs | 3 fixed blurred circles (`blur(90px)`, opacity .35/.35/.2) drifting with mouse and scroll via `requestAnimationFrame` |
| Reduced motion | `@media (prefers-reduced-motion: reduce)` disables all animation/transition (already implemented) |

---

## 4. Components

### Ambient orbs
`.orb` fixed, `border-radius:50%`, `pointer-events:none`, `z-index:0`. Sizes 520 / 460 / 380px at top-left, bottom-right, and mid-right. Content sits at `z-index:1+`.

### Navigation
Fixed full-width, transparent at top, glass when scrolled. Left wordmark `braj` + gradient `saa`; center-right links; **Say hello** as a small glass button (10px 20px, .82rem). Below 860px the link list is hidden (only wordmark and Say hello remain).

### Buttons `.btn`
- **Default (glass):** 15px 26px, radius 16, glass fill/border/blur, inset highlight.
- **Primary `.primary`:** `--grad` fill, no border, text `#0b0b13`, white-tinted shadow.
- Labels use a trailing `↗` for outbound intent.

### Hero
Centered column, `min-height:100svh`, gap 44px (30px mobile). Order: availability pill → H1 (two lines, middle phrase "designing websites" uses animated gradient) → subcopy → two buttons → **video frame** → scroll cue. Radial white glow (1000px, 8% white) behind the content.

### Hero video frame
16:9, max-width 960px, radius 28px, glass border, inner vignette (`inset 0 0 60px rgba(0,0,0,.4)`), fake window bar with three 9px dots, `hero.mp4` (`autoplay muted loop playsinline`, `object-position: center top`, `brightness(.88) contrast(1.03) saturate(1.05)`).

### Glass card `.glass-card`
24px radius, glass fill, `--glass-border`, blur 24px, plus a 1px horizontal gradient highlight line along the top edge (`::before`). Base for stat, work, step, prompt, about and contact panels.

### Stat card
Gradient numeral (Sora 700, 2.4rem) over a muted caption. Three stacked: **100%** custom, **Fast**, **1:1**. About layout is a 1.1fr / .9fr grid, single column under 860px.

### Work (service) card
`auto-fit, minmax(300px, 1fr)` grid. Gradient icon chip (52px, radius 14, glyphs ✦ ◈ ◎ ◐) → H3 → description → tag pills pushed to bottom (`margin-top:auto`).

### Tag
Pill, .72rem, 6px 12px, subtle white fill and border, muted text.

### Prompt library
- Intro glass card ("Why AI breaks midway").
- Four **step cards** (`minmax(260px, 1fr)`): gradient number chip (38px, radius 10), H4, then **Why** and **How** lines with bold white labels.
- **Prompt block:** uppercase label, `pre-wrap` prompt text, primary **Copy prompt ↗** button (text flips to "Copied ✓" for 1.8s).
- **Rule box:** 2px left border in `--text`, muted copy, bold lead-in.

### Tools carousel
Max-width 520px, 4:5 slides, radius 26, glass frame. CSS scroll-snap (`x mandatory`, `center`), hidden scrollbar. Round 46px glass arrows offset -22px outside the frame (hidden under 640px). "n / 10" counter and clickable dot row beneath (7px dots, active = white, scale 1.3).

### Contact
Centered glass panel (70px 60px; 50px 24px on mobile): eyebrow, H2, one line of copy, primary email button, then two 48px glass social icon buttons (Instagram, email) that lift and scale on hover.

### Footer
Flex row, space-between, top border `rgba(255,255,255,.06)`, muted .82rem text, wraps on mobile.

---

## 5. Responsive Behavior

| Breakpoint | Changes |
|---|---|
| ≤ 860px | Nav links hidden; About becomes one column; contact panel padding reduced |
| ≤ 760px | Hero padding `120px 5% 60px`, gap 30px; frame radius 20px |
| ≤ 640px | Carousel arrows hidden; carousel takes full width |
| Grids | Work and step grids reflow automatically via `auto-fit/minmax` |

*(recommended)* Add a mobile menu: below 860px the section links disappear and there is no replacement, so visitors can't jump to Tools or Prompts from the nav.

---

## 6. Accessibility

**Already in place:** `lang="en"`, `prefers-reduced-motion` support, `aria-label` on carousel arrows, `alt` text on all 10 slides, `rel="noopener"` on external links, semantic `nav`, `section`, `footer`.

**Gaps *(recommended)*:**
- No `:focus-visible` styles; add a 2px white ring with offset on `.btn`, links, arrows, dots.
- Carousel dots are `div`s with click handlers: make them `<button aria-label="Go to slide n">` and add `aria-live="polite"` to the counter.
- Muted text `#9a97ac` on `#06060a` is about 7:1 (fine), but check it where it sits over the video frame and orbs.
- Add a skip link, `aria-hidden` on orbs and decorative glyphs (✦ ◈ ◎ ◐), and `aria-label` on the video or a `poster`.
- Copy button should announce "Copied" to screen readers (`aria-live`).
- `.reveal` content starts at `opacity:0`: if JS fails the page is blank below the hero; add a `<noscript>` rule that sets `.reveal{opacity:1;transform:none}`.

---

## 7. Performance

Current assets: `hero.mp4` ≈ 3.8 MB, ten slides ≈ 390–480 KB each (≈ 4.4 MB), `index.html` ≈ 31 KB inline CSS/JS. Total ≈ 8.3 MB.

*(recommended)*
- Compress slides to WebP/AVIF (target < 120 KB each) and add `loading="lazy"` plus width/height to every `<img>`.
- Add `poster` and `preload="metadata"` to the hero video; offer a WebM source.
- Pause the orb `requestAnimationFrame` loop when the tab is hidden or reduced motion is on (it currently runs continuously, even though CSS animations are disabled for reduced motion).
- Heavy `backdrop-filter` on many cards is GPU-costly on low-end phones: consider lowering blur on mobile.
- Trim font weights to those used (Sora 400/600/700, Inter 400/500/600).

---

## 8. SEO and Sharing *(recommended; none present today)*

Only `<title>` and viewport exist. Add:
- `<meta name="description">` (~155 chars) matching the hero subcopy.
- Open Graph and Twitter tags with a 1200×630 image so Instagram/WhatsApp previews look right.
- `<link rel="canonical">` to the clean URL (drops `utm_*` and `fbclid`), favicon, `theme-color` `#06060a`.
- JSON-LD `Person` / `ProfessionalService`.
- The repo name `-thevoidmoon-.github.io` starts with a hyphen and isn't a root user site, hence the awkward URL. A custom domain or a repo named `<username>.github.io` gives a cleaner link.

---

## 9. Content Reference

| Where | Copy |
|---|---|
| Hero H1 | Brajraj Singh Songara — **designing websites** people remember. |
| Hero sub | I design and build clean, modern, high-converting websites — from first sketch to the live site your visitors scroll through. |
| About H2 | A designer who builds, not just draws. |
| Work H2 | Website design, end to end. |
| Tools H2 | 10 free design tools, no subscriptions. |
| Prompts H2 | Structure before you build. |
| Contact H2 | Have a website in mind? Let's design it. |
| Email | the.voidmoon11@gmail.com |
| Instagram | @brajsaa_23 |

**Tools carousel (slides):** intro · 1 Background Remover · 2 QR Code Generator · 3 Image Tracer · 4 Palette Generator · 5 Contrast Checker · 6 Image Converter · 7 Visual Identity Formula · 8 Partnerships Calculator · outro (all free, no tracking, open source).

---

## 10. Content and UX Improvements

1. **"Work" has no work.** `#work` shows services. Add a Selected Projects section (screenshots, goal, result) since visitors expect finished sites.
2. Add social proof (testimonials or client results) before the contact panel.
3. Link each of the 10 free tools to its live page or repo, so "open source" is verifiable. Currently they are images only.
4. Rename nav "Work" → "Services" until real projects exist.
5. Add a short inquiry form (budget, timeline, links) with the `mailto:` as fallback.
6. The Prompt Library is Shopify/AI-build advice in a design portfolio: keep it, but add one line on how it connects to the services (for example, "how I keep AI-assisted builds consistent").

---

## 11. Handoff Checklist

Applied in the updated `index.html`:
- [x] Legacy color variables renamed to `--accent-1/2/3`; violet hover shadow fixed
- [x] Mobile navigation menu (toggle, Escape and link-click close, `aria-expanded`)
- [x] Focus-visible styles, skip link, `<main>` landmark, button-based carousel dots, `aria-live` on counter and copy button
- [x] `<noscript>` fallback so `.reveal` content is visible without JS
- [x] Slides re-compressed, lazy-loaded with width/height; hero video has `poster` and `preload="metadata"`; orb loop skipped under reduced motion; unused font weights dropped
- [x] Meta description, Open Graph/Twitter tags (image: `hero-poster.jpg`), canonical, favicon, theme-color

Still open (needs your content or decisions):
- [ ] Real Work / case-studies section, then rename or re-point the "Work" nav link and "View my work" button
- [ ] Testimonials or client results
- [ ] Link each free tool to its live page or repo
- [ ] Inquiry form (optional)
- [ ] Custom domain or a clean repo name (current URL starts with a hyphen)
- [ ] Dedicated 1200×630 social image (the current one is a video frame)

*Last updated: November 2026*
