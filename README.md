# SKKNI TIK Knowledge Base — RAG Ready

## Struktur

- `documents/` → **5 Markdown untuk ingestion RAG**
- `source-pdf/` → arsip PDF asli, **jangan di-ingest**
- `manifest.json` → indeks dokumen dan unit kompetensi
- `README.md` → aturan penggunaan

## Struktur setiap Markdown

Setiap file memiliki:

1. YAML frontmatter tingkat dokumen.
2. Daftar unit kompetensi.
3. Pendahuluan/kerangka SKKNI.
4. Setiap unit kompetensi sebagai blok `##`.
5. Metadata unit:
   - Kode Unit
   - Judul Unit
   - Halaman awal PDF
6. Subbagian:
   - Deskripsi Unit
   - Elemen Kompetensi dan Kriteria Unjuk Kerja
   - Batasan Variabel
   - Panduan Penilaian
7. Machine-readable Unit Index.

## Integritas sumber

Yang dilakukan:
- normalisasi whitespace/layout;
- penambahan heading;
- penambahan metadata;
- penambahan penanda halaman.

Yang TIDAK dilakukan:
- tidak membuat unit baru;
- tidak mengganti kode unit;
- tidak mengubah substansi KUK;
- tidak meringkas batasan variabel;
- tidak menambahkan pengetahuan dari luar dokumen.

## Untuk n8n

Pada tahap ingestion nanti, ambil hanya:

`documents/*.md`

Folder `source-pdf/` dipertahankan sebagai arsip/audit.

Metadata `decree_number`, `decree_year`, `field`, `subfield`, `source_file`, `unit_code`, dan `unit_title` sebaiknya diteruskan ke metadata vector store pada tahap berikutnya.
