# Selvalakshmi Fireworks POS — Fresh standalone prototype

This is a new, independent POS project. It does not modify or connect to the existing website.

## Run locally
Open `index.html` in a modern browser. Excel import uses SheetJS from a CDN, so an internet connection is required for `.xlsx` and `.xls` parsing. CSV import/export and core UI work in-browser.

## Included prototype modules
- Dashboard, POS billing, inventory, Excel import, purchases, sales reports, users/roles screen, store settings
- Product add/edit, stock deduction on sale, stock addition on purchase
- Excel/CSV import preview and validation, duplicate SKU detection, optional update of existing SKUs, import template download
- CSV export of product catalogue and sales register

## Important production notes
This is a browser-based prototype. Data is stored in browser localStorage and is not shared between devices, backed up to cloud, or protected by server-side authentication. Do not use it as the live system for real transactions until a production backend (e.g. Supabase/Postgres), authentication/role enforcement, server-side validation, backups, GST invoice rules, and hardware testing are implemented. Sample catalogue rows are demo data and should be replaced.

## Deploy as a fresh Vercel project
1. Create a new Git repository and upload the contents of this folder.
2. In Vercel, import that repository as a **new project** (do not select or overwrite the existing project).
3. Framework preset: Other; build command: leave blank; output directory: `.`.
4. Deploy. Add your new domain/subdomain only to this new project.

## POS billing updates
- Change each cart item's quantity before saving; quantities are checked against available stock.
- Apply a per-item discount (₹) in the cart's Discount column, plus an optional overall bill discount.
- Use **Save & Print 58mm** to save the sale and open a compact receipt print view.
- For a mini Bluetooth thermal printer, pair it with the Android device in Bluetooth settings and select it from the Android print/share system flow where supported. Browser-based Bluetooth printer support varies by printer model and Android print service; this version uses the system print dialog rather than a direct ESC/POS Bluetooth connection.
