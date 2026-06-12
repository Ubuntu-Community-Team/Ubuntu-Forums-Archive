---
title: "[SOLVED] Export from evince (pdf reader)"
date: 2008-08-20
forum: General Help
---

### Post by ofir_k on 2008-08-20
Hello,

How can I export pages from a PDF file to images using evince?

If evince **can't** export to images, how it can be done?

Thanks in advanced,
Ofir

---

### Post by kaibob on 2008-08-21
> **ofir_k said:**
> Hello,

How can I export pages from a PDF file to images using evince?

If evince **can't** export to images, how it can be done?

Thanks in advanced,
Ofir

Evince won't work. The poppler-utils command-line suite, which is in the repo's, contains a utility named pdfimages. I have not used this utility, but it appears to do what you want. It is described in the man page as follows:

[I]This package contains pdftops (PDF to PostScript converter), pdfinfo (PDF document information extractor), pdfimages (PDF image extractor), pdftotext (PDF to text converter), and pdffonts (PDF font analyzer).

Pdfimages saves images from a Portable Document Format  (PDF)  file  as Portable Pixmap (PPM), Portable Bitmap (PBM), or JPEG files. Pdfimages  reads  the  PDF file, scans one or more pages, PDF-file, and writes one PPM, PBM, or JPEG file for each  image,  image-root-nnn.xxx, where  nnn  is  the image number and xxx is the image type (.ppm, .pbm, .jpg).[/I]

---

### Post by ofir_k on 2008-08-21
I managed to export pages from a PDF file to images by opening the PDF file in GIMP.

Just open GIMP and open the PDF file, select the pages you want, select "Images" from "Open pages as" and you are done!

This solution suites only users with a basic technical experience.

End-users won't think about such a solution - they will give up if they won't find an option in evince to export...

Anyway, thank you kaibob for your help!

---

