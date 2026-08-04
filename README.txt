HeatMatrix v0.1 — Tableau Dashboard Extension (TREX)
====================================================

WHAT'S IN THIS FOLDER
  HeatMatrix.trex   -> the manifest you add to a Tableau dashboard
  index.html        -> the extension itself (single self-contained file)
  README.txt        -> this file

RUN IT (Tableau Desktop, personal use)
  1. Put this folder anywhere on your machine.
  2. Open a terminal in the folder and start a tiny local web server:
        python -m http.server 8765
     (or:  npx http-server -p 8765)
  3. In Tableau Desktop, open a dashboard and drag in an "Extension" object.
  4. Choose "Access Local Extensions" and select HeatMatrix.trex.
  5. Allow the extension when prompted.

FEEDING IT DATA
  Put a worksheet on the dashboard containing exactly the fields you want:
  two dimensions (rows + columns) and one measure. The sheet can be tiny or
  hidden behind the extension. Open the format panel (gear icon, or
  right-click the extension > Configure) > General tab, and pick the sheet,
  row dimension, column dimension, and measure. The heat map re-renders on
  filter changes automatically.

FORMAT PANEL (gear icon / Configure)
  General : worksheet + field mapping, color sequence (Green-White-Red,
            Green-Yellow-Red, reversed variants, two colorblind-safe pairs),
            center point (auto / zero / median / custom), bevel 0-24px,
            cell buffer 0-14px
  Axis    : show/hide row & column labels, label angle, size, color, sorting
  Text    : show values, denomination (auto/none/K/M/B), decimals 0-3,
            prefix ($, EUR, GBP or custom), font (Tableau-compatible list),
            size (auto-fit or fixed), auto-contrast or fixed value color, bold
  Legend  : show/hide, bottom or right, custom title, min/center/max labels

  All settings persist in the workbook via the Tableau settings API.

NOTES
  - Opened directly in a browser (outside Tableau) it shows demo data, which
    is handy for styling without a live dashboard.
  - Internet is needed once at load for the Tableau Extensions API script
    (tableau.github.io). For fully offline use, download
    tableau.extensions.1.latest.js into this folder and change the <script>
    tag at the top of index.html to src="tableau.extensions.1.latest.js".
  - For Tableau Cloud/Server or the Tableau Exchange later, the page must be
    hosted at a public HTTPS URL and the manifest updated to match; Exchange
    submission also wants a real 70x70 icon and a privacy/support page.
