# Web Design Standards

These rules apply to every website, landing page, or web app built or restyled in this repo. Follow them by default, without being reminded. Always work through the installed `ui-ux-pro-max` skill (and its companion skills — `design`, `design-system`, `ui-styling`, `brand`, `slides`, `banner-design` in `.claude/skills/`) for style, color, typography, chart, and stack-specific guidance, and apply the rules below on top of it.

## Ground it in the actual subject

Before writing any code, identify the real subject, audience, and primary job of the page. Pull colors, type, and layout choices from that specific brief, not from a generic "modern SaaS" template. A design for a boutique hotel should look nothing like a design for a dev tool.

## Avoid the default AI-generated tells

Do NOT default to any of these unless the brief specifically calls for it:

- Warm cream background (`#F4F1EA`) + serif display + terracotta/clay accent (~`#D97757`)
- Near-black background with one bright acid-green or vermilion accent
- Identical rounded cards with the same soft grey shadow (`rgba(0,0,0,.1)`) and gradient-wash decoration
- Tracked-out ALL-CAPS eyebrow labels above every heading
- Meta strings joined with middle dots ("A · B · C"), or "WORD — fragment" labels with spaced em dashes
- A "→" tacked onto every button/link
- Monospace font for small data labels "because it looks technical"
- Numbered markers (01/02/03) on content that isn't actually a sequence
- Fade-and-slide-up entrance on every section + hover transition on every card

## Process: plan → review → build → critique

1. **Plan first.** Before code, write a compact token system:
   - Color: 4–6 named hex values, chosen for this brief
   - Type: 1–2 typefaces and their roles (don't reach for Inter/system-ui by default)
   - Layout: one-sentence layout concept + ASCII wireframe, with alignment decided (left/center/justified)
   - Principles: what makes this specific page unique
2. **Review the plan against the brief.** If any part reads like the generic default for "a page like this," revise it and say what changed.
3. **Build** following the revised plan.
4. **Screenshot and self-critique.** Take a screenshot (Playwright/Puppeteer if available). Apply the "remove one accessory" rule: cut one decorative element before showing the result. Check: is there one genuinely bold/memorable moment, with everything else quiet around it?

## Technique defaults

### Glassmorphism

- `backdrop-filter: blur(12–20px)` on panels
- Background: semi-transparent white/dark (`rgba(255,255,255,0.08)` on dark, `rgba(255,255,255,0.6)` on light) — never fully opaque
- 1px border, a lighter/brighter shade of the panel's own base color (not plain grey)
- Layer 2–3 panels at different blur/opacity levels for real depth, rather than one blur applied everywhere

### 3D

- Real 3D scenes/objects → Three.js, or react-three-fiber if the project is React
- Lighter "3D-ish" depth (tilt-on-hover cards, layered parallax, scroll-based depth) → plain CSS `perspective()` + `rotateX/rotateY`, no heavy library needed
- Default to the CSS approach unless the brief clearly wants an actual 3D scene — it's lighter weight and loads faster

### Animation

- React project → Framer Motion. Vanilla JS → GSAP.
- One orchestrated moment (a hero load sequence, one scroll-triggered reveal) beats effects scattered on every element.
- Motion should answer something the user did (opened, expanded, confirmed) or land once on load — not decorate every card with a hover wiggle.
- Always respect `prefers-reduced-motion`.

### Gradients

- Derive gradients from the brief's own palette, not the default purple→blue SaaS gradient.
- Subtle mesh/noise gradients read as more expensive than hard two-stop linear gradients.
- Use gradients as one accent, not as background decoration everywhere.

### Layout & typography

- Line length under ~80 characters (serif body text can run slightly longer, with more line-height).
- One typographic accent per headline max — don't bold/italic/color a single word AND use an eyebrow label AND use all-caps on the same page.
- Visual structure (dividers, numbering, borders) should encode real information, not decorate.

## Quality floor (non-negotiable, don't announce it, just do it)

- Responsive down to mobile
- Visible keyboard focus states
- `prefers-reduced-motion` respected
- Color contrast that actually passes accessibility checks
- No conflicting CSS selector specificity between type-based (`.section`) and element-based (`.cta`) rules, especially around spacing

## When the brief doesn't specify

If the brief leaves an axis open (color, type, layout), don't spend that freedom on a default — make a deliberate choice and be ready to explain why it fits this specific project.
