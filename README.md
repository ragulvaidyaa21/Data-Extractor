# Browser Data Extractor

Mobile-friendly browser tool to upload Excel, CSV, or PDF files, filter and sort data, open clickable links, export eight formats.

A single-file web app. Everything runs in your browser, and your files are never uploaded to a server.

## Features

- **Upload** `.xlsx`, `.xls`, `.csv`, or `.pdf` by drag-and-drop or the Browse button
- **Multiple sheets** shown as tabs
- **Clickable hyperlinks** read from Excel cells (for example a "Resume Path" column) and opened in a new tab
- **Search and filter**: global keyword search, per-column filters, and a numeric range filter
- **Sort** by clicking any column header
- **Show or hide columns** with checkboxes
- **Pagination** with 100 to 5,000 rows per page
- **Export** the filtered, visible data as CSV, XLSX, JSON, TSV, PDF, HTML, XML, or SQL
- **Mobile friendly**: collapsible filters, touch scrolling, and a bottom-sheet export menu

## Getting started

1. Download `data-extractor.html`.
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari, or a mobile browser).
3. Drop a file onto the upload area.

No install or build step is needed. An internet connection is required the first time to load the libraries from a CDN.

## How to use

| Task | How |
|---|---|
| Search everything | Type in **Keyword Search** |
| Filter one column | Type in that column's **Filter** box |
| Filter by number | Choose a numeric column, then enter Min and/or Max |
| Hide a column | Untick it under **Show / Hide Columns** |
| Sort | Click a column header (click again to reverse) |
| Open a link | Click the blue **Link ↗** in the table |
| Export | Click **Export** and choose a format |

On phones, tap **☰ Filters** to show or hide the filter panel.

## How links work

Excel stores a link as a hidden URL behind the cell's displayed text. A plain table read only returns the text, such as "Link". This app also reads the hidden URL (`cell.l.Target`) and renders it as an `<a>` tag.

- Only `http`, `https`, `mailto`, and `tel` links are accepted. Others, such as `javascript:`, are ignored.
- Cells containing a plain `https://...` address are linked automatically.
- In exports, link cells contain the real URL. In the PDF export the text stays short and is clickable.

## Export notes

- Exports include only the **visible columns** and **filtered rows**.
- CSV files start with a UTF-8 marker so Excel reads special characters correctly.
- PDF files are A4 landscape.
- SQL export creates a `CREATE TABLE` statement (all columns as `TEXT`) followed by `INSERT` statements.

## Built with

- [SheetJS](https://sheetjs.com/) 0.18.5 for reading and writing Excel files
- [pdf.js](https://mozilla.github.io/pdf.js/) 3.4.120 for reading PDFs
- [jsPDF](https://github.com/parallax/jsPDF) 2.5.1 and jsPDF-AutoTable 3.8.2 for PDF export
- Plain HTML, CSS, and JavaScript, with no framework

## Limitations

- PDF import is text-based. It splits rows by vertical position, so complex layouts or scanned PDFs may not extract cleanly.
- Very large files (tens of thousands of rows) can be slow on phones. Use a smaller rows-per-page setting.
- Links are read from `.xlsx` and `.xls` files only. CSV has no hyperlink data.
- Link URLs come straight from the file. If the source system issues expiring links, they may stop working later.

## Project structure

```
data-extractor.html   # the whole app (HTML + CSS + JS)
README.md
```
