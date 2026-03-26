# JS Sports Arena Website

This is the static HTML website for **JS Sports Arena** — located at 75 Anderson Rd, Smeaton Grange NSW.

---

## 🌐 Environments

| Environment | URL | Branch |
|---|---|---|
| Staging (test site) | https://website-8bea9e1b.diy.uih.mybluehost.me | `staging` |
| Production (live site) | https://jssportsarena.com.au | `main` |

Whenever you push code, it automatically deploys to the right site — **no manual uploads needed**.

---

## 💻 Day-to-Day Workflow

### 1. Make sure you're on the staging branch before making any changes
```
git checkout staging
```

### 2. Make your changes (edit HTML files, add images, etc.)

### 3. Save and deploy to staging
```
git add . && git commit -m "describe what you changed" && git push
```
Your changes will automatically appear on the staging site within 1–2 minutes.

### 4. Check the staging site
Open https://website-8bea9e1b.diy.uih.mybluehost.me and make sure everything looks good.

### 5. When you're happy — push to production (live site)
```
git checkout main && git merge staging && git push && git checkout staging
```
Your changes will automatically appear on https://jssportsarena.com.au within 1–2 minutes.

> **Always go back to `staging` after going live** — the last line `git checkout staging` does this for you.

---

## 🖼️ Adding Images & Videos

Images and videos are **not stored in GitHub** (they're too large). Instead:

1. Place image/video files in the `/images/gallery/` folder on your local machine
2. Update the HTML to reference them (Claude can help with this)
3. **Manually upload** the same files to Bluehost via File Manager at the same path

Supported formats: `.jpg`, `.png`, `.webp`, `.mp4`, `.MOV`

---

## 📁 File Structure

```
jssportsarena/
├── index.html          ← Home page
├── about.html          ← About page
├── book-courts.html    ← Book Courts page
├── contact.html        ← Contact page
├── gallery.html        ← Gallery page
├── rates.html          ← Rates page
├── privacy.html        ← Privacy Policy
├── terms.html          ← Terms & Conditions
├── images/
│   └── gallery/        ← All images and videos go here
├── public/
│   ├── js-sports-logo.png
│   └── js-favicon.png
└── .github/
    └── workflows/
        ├── deploy.yml          ← Auto-deploys main → production
        └── deploy-staging.yml  ← Auto-deploys staging → staging site
```

---

## 🔑 GitHub Secrets (already configured)

These are stored securely in GitHub and used for auto-deployment. **Do not share these.**

| Secret | Purpose |
|---|---|
| `FTP_SERVER` | Bluehost FTP server address |
| `FTP_USERNAME` | Bluehost FTP username |
| `FTP_PASSWORD` | Bluehost FTP password |
| `FTP_SERVER_DIR` | Production folder path (`public_html/`) |
| `FTP_SERVER_DIR_STAGING` | Staging folder path (`public_html/website_8bea9e1b/`) |

---

## 🆘 Common Issues

**Changes not showing on the site?**
- Wait 1–2 minutes after pushing
- Check GitHub → Actions tab to see if the deploy succeeded
- Hard refresh the browser (Cmd+Shift+R on Mac)

**Accidentally pushed to main instead of staging?**
- Don't panic — just make your fix on staging and merge again

**Image not showing on site?**
- Make sure you uploaded the file to Bluehost File Manager
- Check the filename matches exactly (case-sensitive on the server)
- e.g. `Card1-Courts.jpg` ≠ `card1-courts.jpg`
