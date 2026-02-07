# Afterimage — Project Setup

## Prerequisites

- **Node.js** v18 or later (v20+ recommended)
- **npm** (comes with Node.js)

Check your versions:

```bash
node -v
npm -v
```

---

## 1. Install dependencies

From the project root:

```bash
npm install
```

This installs Astro and everything else listed in `package.json`.

---

## 2. Start the dev server

```bash
npm run dev
```

The site will be available at **http://localhost:4321/**.

The dev server hot-reloads — any changes you save to files in `src/` will instantly reflect in the browser.

---

## 3. Build for production

```bash
npm run build
```

This outputs a fully static site into the `dist/` folder, ready to deploy anywhere (Vercel, Netlify, Cloudflare Pages, GitHub Pages, etc.).

---

## 4. Preview the production build locally

```bash
npm run preview
```

This serves the `dist/` folder locally so you can verify the production build before deploying.

---

## Project structure

```
afterimage/
├── public/
│   └── img/
│       ├── IMG_5357.PNG        # Base portrait (IMAGE ONE)
│       └── burjkhalifa.jpg     # Reveal layer (IMAGE TWO)
├── src/
│   └── pages/
│       └── index.astro         # The entire landing page
├── img/                        # Source images (originals)
├── astro.config.mjs            # Astro configuration
├── package.json                # Dependencies & scripts
└── tsconfig.json               # TypeScript config
```

### Key files

| File | Purpose |
|---|---|
| `src/pages/index.astro` | The single-page portfolio — all HTML, CSS, and JS live here |
| `public/img/` | Static images served at `/img/...` |
| `astro.config.mjs` | Astro settings (output mode, integrations, etc.) |

---

## Swapping images

To change the background images, replace the files in `public/img/` and update the `<img src="...">` paths in `src/pages/index.astro` if the filenames differ.

---

## Updating social links

Open `src/pages/index.astro` and find the `<!-- Bottom-right: Social icons -->` section. Replace the `href` values with your actual profile URLs:

```html
<a href="https://instagram.com/YOUR_HANDLE" ...>
<a href="https://x.com/YOUR_HANDLE" ...>
```

---

## Deploying

This project is configured for Vercel via `@astrojs/vercel` (see `astro.config.mjs`). You can deploy either by connecting the Git repo in the Vercel UI or using the CLI.

### Deploy on Vercel (recommended)

#### Option A — Vercel Dashboard (Git integration)

1. Push this repo to GitHub.
2. In Vercel, click **Add New → Project** and import the repo.
3. Vercel should auto-detect **Astro**.
4. Keep defaults:
   - **Build Command**: `npm run build`
   - **Install Command**: `npm install`
5. Click **Deploy**.

#### Option B — Vercel CLI

```bash
npx vercel
```

Then for a production deployment:

```bash
npx vercel --prod
```

### Environment variables (only if you add APIs later)

If you add server endpoints (e.g., LinkedIn/Tavily integration), set secrets in Vercel:

- Vercel Dashboard: **Project → Settings → Environment Variables**
- Or CLI:

```bash
npx vercel env add TAVILY_API_KEY
```

### Other hosts

You can also deploy to Netlify / Cloudflare Pages, but Vercel is the easiest with the current server build setup.
