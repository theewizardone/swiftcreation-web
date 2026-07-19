# Swift Creations Website

A static two-page site: the main marketing homepage and a connected instant quote calculator.

## What's in this folder

- `index.html` — the main site (hero, services, tech stack, process, pricing, case studies, testimonials, FAQ, contact)
- `quote.html` — the instant quote calculator, linked from the nav bar, hero button, and every pricing card
- `.gitignore` — standard ignores for a static project

No build step, no dependencies, no `package.json` needed — both pages are self-contained HTML/CSS/JS.

## Pushing to GitHub

From inside this folder:

```bash
git init
git add .
git commit -m "Initial site with homepage and instant quote calculator"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

Replace the URL with your actual GitHub repo (create an empty one first on github.com if you haven't).

## Deploying to Vercel

1. Go to [vercel.com/new](https://vercel.com/new) and import the GitHub repo you just pushed.
2. Framework preset: choose **Other** (or leave as detected — Vercel auto-serves static HTML with zero config).
3. Leave build command and output directory blank.
4. Click **Deploy**. Both `index.html` and `quote.html` will be live at your domain (e.g. `yoursite.vercel.app/` and `yoursite.vercel.app/quote.html`).

Because the two pages link to each other with relative paths (`quote.html`, `index.html`), they must stay in the same top-level folder — don't move one into a subfolder without updating the links.

## Dark / light mode

Both pages now have a toggle button (🌙 / ☀️) in the nav bar. On first load, it matches the visitor's system preference (light or dark); clicking it switches for the rest of that visit. It intentionally doesn't remember the choice across page reloads — if you'd like it to persist (e.g. via `localStorage`), that's a small addition, just ask.

## Things to customize before launch

- **Phone/WhatsApp number & email** — currently `+254 798 347 975` and `helloswiftcreations@gmail.com`, used in both files (nav, footer, hero CTA, WhatsApp links, quote result screen).
- **Testimonials** (`index.html`, "Client feedback" section) — currently realistic placeholder personas, not real clients. Swap in real testimonials once you have written permission to use a client's name/quote.
- **Case studies / portfolio** — currently 2 sample case studies. Replace with your real project outcomes and, ideally, real screenshots.
- **Pricing numbers** — set in the `pricing-grid` section of `index.html` and mirrored in the `BASE_PRICE` constant and `typeMap`/`extraMap` objects near the bottom of `quote.html`. If you change one, update the other so the numbers stay consistent across both pages.
- **Team, extended portfolio, blog** — not included in this version yet; say the word if you want these added as additional sections or pages.

## Connecting the quote form to your inbox

Right now, submitting the quote calculator shows the result on-screen and opens WhatsApp with a pre-filled message — but it doesn't email you a copy automatically. The fastest way to add that without a backend:

1. Sign up at [formspree.io](https://formspree.io) (free tier available) and create a form to get an endpoint URL.
2. In `quote.html`, inside the `finalizeQuote()` function, add a `fetch()` POST to that endpoint with the `state` object (name, email, phone, type, speed, extras, total) as the body.

Happy to write that integration in for you — just share which service you'd rather use (Formspree, a Google Sheet via Zapier, or something else).
