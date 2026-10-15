# Lucky Pokédex v1.0.0: nasazení zdarma (GitHub Pages + Firebase)

Výsledek: web na adrese `https://TVOJE-JMENO.github.io/lucky-pokedex/`, kterou otevřou všichni hráči z mobilu i počítače bez přihlášení a můžou si ji dát na plochu jako aplikaci. Vše je zdarma.

## Co je v balíčku
- `index.html`: celá aplikace
- `manifest.webmanifest`, `sw.js`, `icon-*.png`, `apple-touch-icon.png`: instalace na plochu a offline mód
- `firestore.rules`: pravidla databáze
- `zaloha-pocatecni.json`: tvoje současná data (David, Petr, Tom, Eevee, Vivillon)

## Krok 1: Databáze (Firebase)
1. Jdi na https://console.firebase.google.com a přihlas se Google účtem.
2. **Add project** → název třeba `lucky-pokedex` → Google Analytics vypni → Create.
3. V levém menu **Build → Firestore Database → Create database**.
   Vyber region v Evropě (např. `eur3` nebo `europe-west3`) a režim **Production**.
4. Záložka **Rules**: smaž obsah, vlož obsah souboru `firestore.rules` a dej **Publish**.

## Krok 2: Propojení aplikace s databází
1. Ve Firebase klikni na ozubené kolečko → **Project settings** → dole **Your apps** → ikona webu `</>`.
2. Pojmenuj aplikaci, **Register app** (hosting nezapínej). Zobrazí se kód `firebaseConfig = { apiKey: ..., projectId: ..., ... }`.
3. Otevři `index.html` v textovém editoru (Poznámkový blok stačí), najdi řádek `const FIREBASE_CONFIG={apiKey:"VLOZ_SEM",...}` a přepiš hodnoty z Firebase (apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId). Ulož.

## Krok 3: Web na GitHubu
1. Na https://github.com si založ účet (zdarma).
2. **New repository** → název `lucky-pokedex` → **Public** → Create.
3. **uploading an existing file** → přetáhni všechny soubory z této složky (včetně upraveného `index.html`) → **Commit changes**.
4. **Settings → Pages** → Source: **Deploy from a branch** → Branch `main` / `(root)` → Save.
5. Po 1 až 2 minutách se nahoře ukáže adresa webu. To je odkaz pro všechny.

## Krok 4: Naplnění daty
1. Otevři odkaz → záložka **Nastavení** → **Obnovit ze zálohy** → vyber `zaloha-pocatecni.json` → potvrď.
2. Teď mají všichni stejná data. Pošli odkaz Petrovi a Tomovi.

## Jednodušší varianta hostingu místo GitHubu (krok 3)
Na https://app.netlify.com/drop přetáhni celou složku s upravenými soubory. Dostaneš hned odkaz. Aby web nezmizel, musíš se přihlásit účtem zdarma a web si "převzít". Zbytek (Firebase, záloha, ikona na ploše) je stejný.

## Krok 5: Ikona na ploše
- **iPhone (Safari):** Sdílet → **Přidat na plochu**.
- **Android (Chrome):** menu ⋮ → **Nainstalovat aplikaci / Přidat na plochu**.
- **PC (Chrome/Edge):** ikona instalace v adresním řádku.

## Dobré vědět
- **Zabezpečení:** pravidla jsou otevřená. Kdo zná odkaz, může číst i zapisovat. Odkaz posílej jen kamarádům. Přihlášení přes e-mail se dá přidat později.
- **Zálohy:** v Nastavení stáhni zálohu před většími změnami.
- **Aktualizace:** nový `index.html` nahraj na GitHub (Add file → Upload files) a přepiš starý. Aplikace se po obnovení stránky sama aktualizuje.
- **Limity zdarma (Firebase Spark):** 50 000 čtení a 20 000 zápisů denně, pro 3 až 10 hráčů bohatě stačí.
