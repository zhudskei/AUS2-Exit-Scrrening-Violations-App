# AUS2 Screening Kiosk — PWA Install Guide

## What is a PWA?

A Progressive Web App installs from a browser but runs like a native app:
- ✅ Own icon on desktop/taskbar (WWOS logo)
- ✅ Opens in its own window (no address bar, no tabs)
- ✅ Works offline
- ✅ No admin rights needed
- ✅ No Node.js, no build tools, no .exe
- ✅ Auto-updates when you push changes to GitHub Pages

## Deployment (one-time)

### Option A: GitHub Pages (recommended — same as your dashboard)

1. Create a new GitHub repo (e.g., `aus2-screening-kiosk`)
2. Push these files to the repo:
   ```
   index.html
   manifest.json
   sw.js
   icons/icon-192x192.png
   icons/icon-512x512.png
   ```
3. Enable GitHub Pages (Settings → Pages → Deploy from main branch)
4. URL will be: `https://zhudskei.github.io/aus2-screening-kiosk/`

### Option B: Local web server (if GitHub is blocked)

```bash
# Python one-liner (serves current folder on port 8000)
cd AUS2_Screening_Kiosk_PWA
python -m http.server 8000
```
Then navigate to `http://localhost:8000`

**⚠️ Important:** PWA install requires HTTPS or localhost. GitHub Pages gives you HTTPS for free.

## Installing on the Laptop (30 seconds)

1. Open Edge or Chrome
2. Navigate to your GitHub Pages URL (or localhost)
3. Look for the **install icon** in the address bar (⊕ or download arrow)
4. Click it → "Install"
5. Done — WWOS icon appears on desktop

### Alternative install method:
- Edge: Menu (⋯) → Apps → "Install this site as an app"
- Chrome: Menu (⋮) → "Install AUS2 Exit Screening Violations..."

## What Guards See

- Desktop icon: **WWOS logo**
- App opens: Full kiosk, maximized, no browser chrome
- USB scanner works exactly the same (keyboard input)
- Data persists in the app's storage between sessions

## Updating the App

Just push updated files to GitHub Pages. Next time the app loads (or within 24hrs), the service worker fetches the new version automatically. Guards don't need to reinstall.

### Updating the roster:
1. Export new roster from FCLM
2. Regenerate `index.html` with new roster data (ask Quick to do this)
3. Push to GitHub Pages
4. App auto-updates on next load

## Uninstalling

- Right-click the desktop icon → Uninstall
- Or: Edge → Settings → Apps → find the kiosk → Remove

## Troubleshooting

| Issue | Fix |
|-------|-----|
| No install prompt | Make sure you're on HTTPS (GitHub Pages) or localhost |
| App doesn't update | Close and reopen the app, or clear service worker in DevTools |
| Offline not working | Open the app once while online to cache assets |
| Scanner not working | Click the badge input field to focus it first |
