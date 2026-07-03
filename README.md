# Wedding by Dimple — Website

Static wedding photography website built with **Astro + Tailwind CSS**.
No backend/server needed — it builds to plain HTML/CSS/JS that runs on any
static host, including Hostinger shared/Business hosting.

## Pages included

Home, Real Stories, Portfolio, Films, About Us, Services, FAQ, Contact
(with a contact form) — matching the site menu from the requirements doc.

## 1. Local setup

```bash
npm install
npm run dev       # http://localhost:4321
```

## 2. Swap in real photos (important)

Every image in this scaffold is a placeholder from picsum.photos so the
site is fully previewable before you have final assets. Replace them
before launch:

1. Drop your real photos into `src/assets/` (e.g. `src/assets/portfolio/`).
2. Import and use Astro's built-in image component instead of a plain `<img>`:

   ```astro
   ---
   import { Image } from "astro:assets";
   import shot1 from "../assets/portfolio/shot1.jpg";
   ---
   <Image src={shot1} alt="..." width={700} height={950} />
   ```

   Astro will automatically compress and generate optimized WebP versions
   at build time — this is what keeps a photo-heavy site fast.
3. Do a find-and-replace across `src/pages/*.astro` for the
   `https://picsum.photos/seed/...` URLs and swap them for your real,
   optimized images.

## 3. Contact form

The contact form uses [Web3Forms](https://web3forms.com) — free, no
backend required:

1. Go to https://web3forms.com and get a free access key with your email.
2. Open `src/pages/contact.astro` and replace `YOUR_WEB3FORMS_ACCESS_KEY`
   with your real key.

Alternative: if you'd rather keep everything on your own Hostinger
account, a small PHP script (`contact.php` using `mail()` or PHPMailer)
works too, since Hostinger Business supports PHP — ask if you want that
version instead.

## 4. Build for production

```bash
npm run build
```

This outputs static files to `dist/`. That folder is your entire website.

## 5. Deploy to Hostinger

1. Log in to **hPanel** → File Manager (or use an FTP client like
   FileZilla with your Hostinger FTP credentials).
2. Upload everything **inside** `dist/` (not the folder itself) into
   `public_html/`.
3. In hPanel, enable **SSL** (free Let's Encrypt, usually one click).
4. In hPanel, turn on the **CDN** — this caches your images and static
   files at edge locations for faster loads across India.
5. If available on your plan, enable **LiteSpeed Cache** for extra speed
   on repeat visits.

That's it — no Node process, no PM2, no server config needed on Hostinger.

## 6. Optional: auto-deploy with GitHub Actions

If you push this to GitHub, you can set up a GitHub Action to build and
FTP-deploy to Hostinger on every push, instead of uploading manually each
time. Ask if you'd like this workflow file added.
