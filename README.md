# Point of Sale

A standalone Windows point-of-sale and store management app for everyday retail operations. Manage checkout, stock, purchasing, cash drawers, income, expenses, and reports from one desktop app.

**[Download the latest POS.exe](https://github.com/v2illiam/pos-releases/releases/latest)**

This public repository contains downloadable releases and customer documentation. Application source code is maintained separately. Store data stays on the store's computer; this repository does not receive transactions, settings, or backups.

## Getting started

1. Download **POS.exe** from the latest release's Assets section. The source-code ZIP and TAR downloads are not the app.
2. Put it in a permanent folder that your Windows account can write to, such as `Documents\Point of Sale`.
3. Open it. The app creates its own folders and a new store database automatically.
4. Set your store details, taxes, products, and optional receipt printer and backup email in Settings.

Each store has its own data and configuration. Core checkout and management work offline. Downloading updates and sending email backups require an internet connection.

Existing users: close the old app and replace its executable in the existing app folder, keeping the `saves` folder and other store files. Install this updater-enabled version once manually; later releases can be installed from the app's update prompt.

## New in 1.0.8

- Inventory transfer files preserve category defaults, individual tax exceptions and remaining item setup requirements for a new store.

- Products and Inventory wrap longer values into taller rows while keeping columns aligned.

- Daily Report shows only nonzero stock movements for the selected day, with product names and barcodes.
- Zero-stock inventory imports no longer produce misleading movement entries. Existing stock quantities and transaction history are preserved.

## Added in 1.0.7

- Clear report filenames include the report name and exact date, date range, or snapshot date in day-month-year order, such as 13 SEP 2026. Repeated exports receive a number to preserve earlier files. Purchase Order History honors the selected period.
- Daily Report in Reports: one-click Export Today's Report and a selector for past dates. One styled workbook includes transactions, all saved receipt items, cash/card/EBT and other split payments, cash change, taxes, margins, drawer sessions and payouts, purchases, income, expenses, and stock activity. Open drawers are provisional; historic tax snapshots are preserved.
- Register Quick Add uses the shared tax categories, with fewer readable buttons and the same tax rates and receipt breakdowns.
- Unified product categories and inherited tax rates; edit one category to update every assigned product.
- Reviewed category consolidation with complete backups and protection for existing manual taxes and past receipts.
- Double-click editing in Products and Inventory, including Stock Status.
- Smoother search suggestions with bold names and smaller barcode, stock, and price details.
- Out-of-stock products show $0 inventory value across the app and Excel exports; negative quantities remain visible.

## Features

### Register and checkout

- Barcode scanner entry and product search in the main register field.
- Live suggestions matching product names or barcodes, showing up to six in-stock items; the list adjusts to the number of matches.
- Cart quantities, item discounts, transaction discounts, coupons, cashier names, and sale notes.
- Category tax defaults and transaction tax controls.
- Multiple payment types and split payments recorded against a sale.
- Automatic completion when the balance is paid, plus an explicit option to complete a sale with a balance due and mark its receipt unpaid.
- Saved cart and payment state, with the cart retained when switching screens or themes.
- Cash-change popup after the payment has been saved. Employees acknowledge the change amount with **OK**; **Print receipt** keeps the change window open.
- Receipt choice after other completed payments, with **Yes** or **No** to close the prompt.

Payment methods record how the customer paid. A connected card-processing service is not included.

### Receipts and printing

- Dated receipt images generated and saved for completed transactions.
- Store name, address, phone, footer, and receipt layout settings.
- ESC/POS printer configuration for USB, network, or serial connections, with 58 mm and 80 mm paper options, feed/cut controls, and test printing.
- Receipt images stored in the portable database and available through local receipt folders.

Printer compatibility depends on the device and its Windows configuration.

### Cash drawer and closeout

- Required typed opening cash amount and employee information.
- Cash sales and paid-out tracking, with drawer session history and transaction details.
- Required counted cash at closing, compared with expected cash.
- Over/short calculation and a deposit amount based on counted cash minus opening cash, with a minimum of zero.
- Saved closeout figures and printable drawer receipts.

### Products and inventory

- Product catalog with names, brands, barcodes, categories, sizes, unit types, prices, costs, reorder points, vendors, and images.
- Add, edit, delete, search, and filter products; manage categories and their default tax rates.
- Stock tracking, scan-to-update workflows, stock adjustments, and low-stock/reorder indicators.
- Product detail views and clickable stock alerts.
- Products and Inventory use 50-row pages for large catalogs. Search, filters and totals cover all matching items. Inventory imports run in the background with progress feedback.

### Vendors and purchase orders

- Vendor directory with contact details, representative information, payment terms, and delivery schedules.
- Purchase order creation with products, quantities, expected costs, delivery dates, and image attachments.
- Scan-to-order and inventory receiving workflows.
- Delivery confirmation for quantities actually received, actual unit costs, extra delivery/tax costs, payment method, and invoice reference.
- Partial deliveries with the remaining quantity kept open.
- Stock updates, actual cost updates, a linked **Inventory / Stock** expense, and delivery history saved together.
- Image attachments when receiving a delivery, with expense references and attachments available in order details.
- Late delivery status with days overdue.
- Order-date range selector and **Received**, **Late**, and **Pending** totals for the selected range.

### Income and expenses

- Daily POS sales income updated automatically as transactions are completed.
- Manual income entries alongside sales income, with category, source, payment method, and receipt images.
- Expense entries with category, vendor, date, amount, payment method, and supporting images.
- Purchase order receiving automatically records its linked purchasing expense.
- Search, filters, date ranges, quick date presets, and document/image viewing.

### Dashboard, sales history, and alerts

- Dashboard sales, gross profit, transaction, income/expense, and stock summaries.
- Sales history and analytics with date filters, daily trends, product/category breakdowns, and payment summaries.
- Charts for sales, profit, income, and expenses.
- Notification bell, badge, and headline ticker for stock and delivery alerts, including overdue, due-today, upcoming, and awaiting-review orders.
- Notification shortcuts to relevant screens, with individual and session-wide dismissal.

### Reports and exports

- Inventory snapshot, low-stock, margin, and dead-stock reports.
- Daily sales and sales by product or category.
- Vendor spend, purchase order, income, expense, and income-versus-expense reporting.
- Excel exports with polished headings, consistent colors, readable formatting, and financial totals; CSV exports where offered.
- Full Data Export workbook and access to the local exports folder.

### Automatic saves and backups

- SQLite holds linked sales, inventory, purchasing, settings and drawer records. Receipt documents and attached images live separately under `saves/assets` and are included in complete backup ZIPs.
- Completed changes save immediately. Editors still use their **Save** buttons.
- Startup automatically opens the newest valid saved store; a new installation starts its own store.
- Closing renames the working database to the closing date, preserving existing files if a date name is already taken.
- Automatic verified backups run every 30 minutes and on close, retaining 12 recent, 30 daily and 30 closing snapshots. Manual and safety backups are retained until removed by the owner.
- **Settings → Backups & Import** offers manual backup, verified ZIP restore, an optional second backup folder, and folder shortcuts. Restore preserves the previous store and checks file hashes and database integrity before switching.
- Optional email backup at closing, with local-only close and cancel choices. The local save happens first.
- Enter a store email and automatically use it as both sender and recipient, or choose a different recipient.
- SMTP/TLS configuration and email credentials held in Windows Credential Manager. Gmail requires a generated app password; credentials must be configured again on a different computer.
- Email attachments are complete ZIP packages of the database and its linked files, up to 18 MiB compressed. Larger stores can use local and second-folder backups.

To move a store, save its complete ZIP backup and choose **Restore backup** in the new installation. Keep the package together rather than mixing files from different dates. Older self-contained database saves remain supported.

### Inventory transfers

- Export an inventory-only **.posinventory.json** file for another installation.
- Drop a transfer file into the **imports** folder beside `POS.exe`; the app offers a review when the register is idle. A manual import button is also available in Products and Settings.
- Searchable, paginated preview of new items, duplicate barcodes and held rows, with stock, price, cost and review reasons.
- Leading zeroes remain intact. Existing barcodes/SKUs are skipped, and repeating an import does not add stock twice.
- Complete backup before import; product records and opening stock movements save together. The original source file is preserved.
- Import now and finish missing tax, cost or price on the first scan or register selection. Save once and future scans reuse those details; cancelling leaves the item out of the sale. Earlier inactive imports from 1.0.2 are enabled for this setup automatically. Uncertain barcode matches and unsupported special pricing are still held for review.
- Inventory transfers do not include sales, drawer sessions, email settings, vendor links or images. Use complete backups to move a full store.

### Interface and settings

- Six live themes: **Light, Dark, Midnight, Ocean, Forest, and Amber**.
- Consistent register, management screens, dialogs, calendars, notifications, and chart styling.
- Responsive toolbars, scrollable tables, and dialogs that accommodate their content within the available screen.
- Store details, receipt options, printer setup, theme selection, backup email, and update settings.

### App updates

- Checks this repository's published stable releases automatically and offers **Update now** or **Later**.
- Manual **Check for updates** in **Settings → Updates**.
- Defers installation while a sale or another dialog is active.
- Downloads and verifies the executable against the release's SHA-256 checksum.
- Saves and snapshots the store before replacing the executable, then restarts with the same database.
- Keeps the previous executable and database backup in `.pos-updates`, with recovery if the new app fails its startup check.

An older app without the updater needs one manual installation of the updater-enabled release. Automatic updates do not upload store data to GitHub.

### Large-store performance

- Paged inventory, accounting lists, purchase orders, sales history, report previews and cash-drawer history keep large collections accessible without drawing every row at once.
- Search and totals cover the complete matching dataset. Older sales and stock movements remain available through page controls.
- Background inventory import, Excel export and scheduled/manual complete backups keep the window responsive during those operations.
- Indexed database lookups and limited register suggestion results reduce unnecessary work.

- Cash Drawer includes a calendar/date selector, saved session dates and the currently open drawer session.
- Inventory sub-tabs load on demand, and standard tables use 25-row pages with theme-matched navigation controls.
- The two most recent data screens can be reused for faster navigation, with automatic refresh after store data changes.
