ProMMISES — Putting it on the internet
======================================

ProMMISES is a self-contained web app. It makes NO external network calls,
so it runs the same whether opened locally or served from a website.

This folder contains everything needed to host it as an installable,
offline-capable Progressive Web App (PWA):

  index.html             the app (same app you already have)
  sw.js                  service worker — caches the app for offline use
  manifest.webmanifest   app metadata (name, colors, icons)
  icon-192.png           app icon
  icon-512.png           app icon

IMPORTANT: keep all of these files together in the SAME folder, and serve
index.html as the entry page. The helper files load by relative path.


-------------------------------------------------
Option A — Drag & drop (easiest, free, ~1 minute)
-------------------------------------------------
1. Go to https://app.netlify.com/drop
2. Drag this entire folder onto the page.
3. You get a public https:// link immediately. Done.

(Cloudflare Pages and Vercel offer the same drag-and-drop style hosting.)


-------------------------------------------------
Option B — GitHub Pages (free, gives a stable URL)
-------------------------------------------------
1. Create a new GitHub repository.
2. Upload all the files in this folder to it.
3. Repo Settings -> Pages -> Source: "Deploy from a branch" -> main / root.
4. Your site appears at https://<username>.github.io/<repo>/


-------------------------------------------------
Option C — Your own web server / intranet
-------------------------------------------------
Copy this folder into any web server's public directory
(Apache, Nginx, IIS, etc.). Visit index.html over http:// or https://.

For local testing you can also run, from inside this folder:
    python3 -m http.server 8080
then open http://localhost:8080


-------------------------------------------------
Installing it as an app
-------------------------------------------------
Once it's served over https:// (any of the options above):
  - Desktop Chrome/Edge: an install icon appears in the address bar.
  - Android Chrome: menu -> "Add to Home screen" / "Install app".
  - iPhone/iPad Safari: Share -> "Add to Home Screen".
After the first visit it is cached and keeps working with no connection.


-------------------------------------------------
Notes
-------------------------------------------------
* Data is stored per-browser/device in that browser's local storage.
  To move data between devices, use the Back up / Restore buttons in the
  app header (they export/import a .json file). The app has no central
  server, which is what keeps it private and fully offline-capable.
* The single index.html still works on its own (double-click to open)
  without the helper files; the service worker simply stays inactive in
  that mode.
