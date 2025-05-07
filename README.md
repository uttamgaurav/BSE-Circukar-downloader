# 📥 BSE Circulars Extractor to Google Sheets

This Google Apps Script automatically extracts circulars from BSE (Bombay Stock Exchange) emails and appends them to a Google Sheet in a structured and searchable format. It handles deduplication, classification, and highlights based on relevance to uTrade.

---

## 🚀 Features

- ✅ Automatically fetches recent circulars from emails with subject:  
  `Consolidated list of BSE circulars`
- ✅ Filters senders: `ba@utradesolutions.com` or `info@bseindia.com`
- ✅ Parses HTML tables inside emails
- ✅ Adds new circulars to Google Sheet
- ✅ Deduplicates using **Circular ID**
- ✅ Adds a **hyperlinked title** pointing to the BSE website
- ✅ Flags circulars not applicable to uTrade (e.g., `Debt` or `Mutual Fund`)
- ✅ Supports **manual override**: if you type `"Y"` in "Applicable to uTrade" column, it turns green
- ✅ Conditional formatting:
  - 🔴 `N` → Red (Not applicable)
  - 🟢 `Y` → Green (if manually added)
- ✅ Auto-run daily at 8:00 AM using a time-based trigger

---

## 📄 Sheet Structure

| Column                      | Description                                        |
|----------------------------|----------------------------------------------------|
| Timestamp                  | When the circular was extracted                    |
| Circular ID                | Unique BSE circular ID                             |
| Title (Linked)             | Title with clickable hyperlink to circular         |
| Asset Class                | Debt / Equity / Mutual Fund etc.                   |
| Applicable to uTrade (Y/N) | Blank if applicable, `N` if not, `Y` if manually set |
| Link                       | Direct URL to circular                             |
| Category                   | Trading / Company Related / Operations etc.        |
| Tag                        | Flags like `⚠️ Suspension`, `⚠️ ESM`, etc.         |

---

## 🔧 Setup Instructions

1. **Create a Google Sheet**  
   Add a sheet/tab named `Auto_BSE_Circulars`

2. **Open Apps Script**  
   Go to `Extensions → Apps Script` and paste the script from [`Code.gs`](./Code.gs)

3. **Set Sheet ID & Name**  
   Update:
   ```js
   const sheetId = 'YOUR_SHEET_ID';
   const sheetName = 'Auto_BSE_Circulars';
