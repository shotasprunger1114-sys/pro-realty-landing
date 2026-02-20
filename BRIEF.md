# Vision Task Brief — Pro Realty Group Landing Page V2

**Owner:** Vision 🤖 (Coding Agent)
**Directed by:** Jarvis ⚡
**Client:** Pro Realty Group (Billy Johair, Broker/Owner)
**Live URL:** https://shotasprunger1114-sys.github.io/pro-realty-landing/
**GitHub Repo:** https://github.com/shotasprunger1114-sys/pro-realty-landing
**Local repo clone target:** `/tmp/prg-v2/` (clone fresh from GitHub)

---

## Your Mission

Upgrade the Pro Realty Group landing page from V1 → V2 with the following changes. Push to GitHub when done. The site auto-deploys via GitHub Pages.

---

## Changes Required

### 1. Logo Fix (High Priority)
- The logo in the nav top-left is too small and barely visible
- **New logos provided** in `assets/`: `logo-black.png` and `logo-black-2.png` (black PRG logos on white background)
- Since the nav is dark navy background, you need a white version of the logo
- Use CSS `filter: invert(1) brightness(2)` on the logo image to make it white on the dark nav — OR create an inverted white PNG using sips: `sips --addIcon -Z 600 assets/logo-black.png` then process with node/canvas, or just use CSS invert
- **Make the logo significantly larger in the nav** — at least 56-64px height (currently 44px and feels small)
- Logo should be `logo-black.png` (the cleaner one with "PRG | Pro Realty Group")

### 2. Headshot Fix (About Section)
- There is unnecessary beige/cream colored space at the bottom of Billy's headshot (the original PNG has a light background that doesn't blend with the white section)
- Fix options (choose best one visually):
  a. Add a CSS gradient fade at the bottom of the photo — `mask-image: linear-gradient(to bottom, black 60%, transparent 100%)` — so the bottom fades to transparent/white
  b. Adjust the `.about-photo-wrap::before` gold accent box to not show the light background
  c. Move the photo positioning so the empty space is cropped/hidden
- **Best approach:** Add `mask-image: linear-gradient(to bottom, black 65%, transparent 100%); -webkit-mask-image: linear-gradient(to bottom, black 65%, transparent 100%);` to `.about-photo-wrap img`
- The about section background is white (`#FFFFFF`) so fading to transparent will blend perfectly

### 3. More Motion & Animation (This is the big one)
Client wants a more modern, engaging, interactive website. Add the following:

#### Hero Section
- **Animated background particles/orbs**: Add 6-8 floating golden orbs/dots in the hero background that drift slowly (CSS animations, no library needed). Use `@keyframes float` with translateX/Y, opacity variations, 8-15s loops. Position them absolutely in the hero.
- **Animated gradient background**: The current static gradient should slowly animate/shift. Add `@keyframes gradientShift` that transitions between 2-3 dark navy hues.
- **Counter animation on ticker**: Already has a ticker — make sure it's smooth. Also add the stat numbers in the hero eyebrow area as animated counters that count up when they enter viewport.

#### General Scroll Animations
- Upgrade all scroll-triggered animations. Currently cards just fade up. Improve to:
  - Pain cards: slide in alternating left/right (odd cards from left, even from right)
  - Benefit cards: stagger with a scale-up effect (scale: 0.92 → 1 with fade)
  - Testimonials: fade up + slight rotation from 2deg → 0deg
  - Process steps: pop in with elastic bounce (use CSS `cubic-bezier(0.175, 0.885, 0.32, 1.275)`)

#### Number Counters
- Add 3-4 animated stat counters in the hero (or as a dedicated stats bar below hero):
  - "100%" commission
  - "$300" flat fee  
  - "24/7" broker availability
  - Make these count up when they enter viewport

#### Hover Effects
- **Benefit cards**: On hover, add a subtle gold shimmer/glow effect (`box-shadow: 0 0 30px rgba(196,149,58,0.2)`) with smooth transition
- **Pain cards**: On hover, border-left color should brighten from dark red to brighter red
- **CTA buttons**: Add a ripple effect on click

#### Parallax
- Add subtle parallax to the hero headline — moves slightly as user scrolls (use JS `window.scrollY` to adjust `transform: translateY()`)
- Add a slow-moving geometric mesh/grid to the hero background that parallaxes with scroll

#### Section Transitions
- Add a decorative SVG wave or angled divider between the hero → pain section (dark → light transition)
- Add angled dividers between the shift → benefits sections

#### Floating Elements
- In the hero, add 2-3 small floating "badge" elements that appear after load delay:
  - One that says "100% Commission" with a check icon
  - One that says "Michigan's #1 Agent-First Brokerage"
  - These should float gently (CSS animation) and feel like social proof popups

### 4. Interactive Calculator Enhancement
- Add a real-time animated number counter on the "Extra money in your pocket" number — when it changes, animate the digits rolling up/down
- Add a bar chart visualization below the result cards showing visual comparison of earnings (PRG bar in gold, Traditional in gray)

### 5. Additional Visual Polish
- Add a subtle animated border/glow to the comparison table PRG column
- Section background textures: add a very subtle diagonal line pattern (SVG pattern) to the off-white sections to add depth
- Footer: add a thin gold gradient line at the very top

---

## Tech Requirements
- **Pure HTML/CSS/JS only** — no external libraries (no GSAP, no Three.js, no heavy deps)
- Lightweight animations using CSS keyframes + vanilla JS IntersectionObserver
- All images are in `assets/` folder (already committed)
- Must remain fast-loading
- Must look clean on mobile (responsive already set up)

---

## Deployment
1. Clone: `git clone https://github.com/shotasprunger1114-sys/pro-realty-landing.git /tmp/prg-v2`
2. Edit `index.html` (main file — everything is in one file)
3. Add/update assets as needed
4. Commit and push to `main` branch
5. GitHub Pages auto-deploys. URL: https://shotasprunger1114-sys.github.io/pro-realty-landing/

---

## Success Criteria
- [ ] Logo is clearly visible and properly sized in nav
- [ ] Billy's headshot bottom space is fixed (faded or cropped)
- [ ] Hero has floating orbs/particles and animated background
- [ ] All scroll animations are upgraded (alternating, staggered, elastic)
- [ ] Stats count up on scroll
- [ ] Hover effects on all cards
- [ ] Section dividers between dark/light transitions
- [ ] Calculator has bar chart visualization
- [ ] Page feels modern, premium, and interactive — like a top-tier recruiting site
- [ ] Pushed to GitHub and live at the URL above

**When done, post a message in #vision-code (Discord channel ID: 1473437027554038008) with the live URL and a brief summary of changes made.**
