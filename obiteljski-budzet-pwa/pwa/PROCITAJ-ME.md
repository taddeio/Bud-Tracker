# Obiteljski Budžet — PWA za iPhone

## 📁 Struktura
```
pwa/
├── index.html      ← Aplikacija (React + Recharts)
├── sw.js           ← Service Worker (offline + ažuriranje)
├── manifest.json   ← PWA konfiguracija
├── icon-180.png    ← iOS ikona
├── icon-192.png    ← Android ikona
├── icon-512.png    ← Splash screen ikona
└── PROCITAJ-ME.md  ← Ove upute
```

## 🚀 Kako deployati

### Najjednostavnije: GitHub Pages (besplatno)
1. Napravi novi GitHub repo (npr. `obiteljski-budzet`)
2. Upload-aj SVE fajlove iz ove mape u repo
3. Settings → Pages → Source: "Deploy from branch" → `main` → `/ (root)`
4. Tvoj URL: `https://tvoj-username.github.io/obiteljski-budzet/`

### Alternativa: Netlify / Vercel
1. Drag-and-drop ovu mapu na netlify.com/drop
2. Odmah dobivaš HTTPS URL

## 📱 Dodaj na iPhone Home Screen
1. Otvori URL u **Safari** (mora biti Safari, ne Chrome!)
2. Tap **Share ikon** (kvadrat sa strelicom) ↑
3. Scroll dolje → **"Add to Home Screen"**
4. Imenuj "Budžet" → **Add**
5. App se otvara fullscreen bez Safari trake!

## 🔄 Kako ažurirati bez gubitka podataka

**Podatci su sigurni!** Financijski podaci žive u `localStorage` koji se
NIKAD ne briše prilikom ažuriranja aplikacije.

### Koraci za update:
1. Uredi `index.html` (dodaj feature, popravi bug...)
2. U `sw.js` promijeni verziju: `'budzet-v1'` → `'budzet-v2'`
3. Push/upload na isti URL
4. Korisnici će vidjeti banner: **"Nova verzija dostupna!"**
5. Klik na "Ažuriraj" → app se refresha s novim kodom
6. Svi financijski podatci ostaju netaknuti ✅

### Zašto ovo radi?
- **Service Worker** cachira app fajlove (HTML, JS, CSS, ikone)
- Kad promijeniš `CACHE_VERSION`, SW briše STARI cache i preuzima novi
- **localStorage** je potpuno odvojen od SW cachea
- Čak i bez interneta, app radi s cached verzijom

## 💾 Backup podataka
- U app-u: ⚙️ Postavke → 📥 Preuzmi backup (JSON)
- Za restore: ⚙️ Postavke → 📤 Importiraj backup
- Import je "merge" — ne briše postojeće zapise

## ⚠️ Kada se podatci MOGU izgubiti
- Korisnik ručno obriše Safari cache / podatke stranice
- Korisnik koristi "Reset" unutar appa
- iOS ponekad čisti localStorage za PWA koje se dugo ne koriste (~7 dana neaktivnosti u nekim slučajevima)

**Preporuka:** Redovito preuzimaj backup iz Postavki!
