# Goudie Works (goudie-works-2026)

Static landing/holding site for the family company. **Astro 5** + **Tailwind v4**, deployed to **Vercel**.

## Commands

- `npm run dev` — local dev server (`astro dev`)
- `npm run build` — production build (`astro build`)
- `npm run preview` — serve the built output locally
- `npx vercel --prod` — build + deploy to production from source (project is linked)

## Structure

- `src/pages/index.astro` — home page listing the trading names (Field Guide, Morning Chorus Records, The Goudies).
- `src/pages/404.astro` — not-found page.
- `src/layouts/BaseLayout.astro` — shared shell. Footer copyright uses `{new Date().getFullYear()}`, so the year updates automatically — never hardcode it.
- `src/assets/*.svg` — logos / favicon.
- `src/styles/global.css` — Tailwind entry + global styles.

## Deployment gotchas

- **Never commit `.vercel/`.** It is gitignored. If Vercel's prebuilt output (`.vercel/output/`) gets committed, Vercel skips `astro build` and serves stale prebuilt files — content updates won't appear despite correct source (deploys finish in ~2s instead of running a real build). This exact bug caused stale-cache issues; the fix was `git rm -r --cached .vercel` plus the gitignore entry.
- `dist/` and `.astro/` are build/cache artifacts — gitignored, never commit.
- `.env*` files are gitignored — never commit secrets.

## Conventions

- Copyright / any "current year" display: use `new Date().getFullYear()`, not a literal, so it never goes stale.
