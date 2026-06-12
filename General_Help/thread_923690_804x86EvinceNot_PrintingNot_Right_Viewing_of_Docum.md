---
title: "804x86::Evince::Not Printing/Not Right Viewing of Documents (useless for work)"
date: 2008-09-18
forum: General Help
---

### Post by xerman on 2008-09-18
Hello there:

I've been using Ubuntu since 504, and always have had issues with PDF files. Now found this issue:

Initial Conditions:
1- Two Pdf Files 25MB each
2- Each file contains A4 and A3 sized pages
3- All pages have watermark added by third party
4- Files are protected so i am not able to modify
5- For the "experiment" had been used: evince, kpdf, adobe reader.
6- Printer is HP Color Inkjet CP1700d
7- Printer is attached through USB to a server on the network. And CUPS is set properly on server and desktop machines.

Machine Setup:
1- Asus T3P5G965 Barebone with Intel Core2Duo E6400 (Configuration never recommended to anyone based on experience. Unable to get rid of continuous anoying noise)
2- 2GB Ram

Requisites:
1- Print the PDF files correctly (800 pages, 100 A3 single sided and 700 A4 double sided).

Results:
1- A4 sized pages were printed without much effort using kpdf
2- A3 sized pages just 10 came out well. The rest won't come out from printer.

Process:
1- Evince does not visualize correctly Watermark on screen. Watermark has no transparency, so it does when printing so blocks the contents covered by watermark.
1.1.- This is a low level issue if able to print, but:
1.2.- After printing the first range of 10 pages, evince will not print again, and options are the following:
1.2.1.- Evince screen grays out and locks app. Force Quit is the only way to solve it. And starts to eat ram up to 1.7GB
1.2.2.- Evince loads the doc, takes eternally to view it but does not grey out. Printing is allowed, and after selecting print options nothing comes out from printer. Seems not to communicate to printer. Other apps do communicate correctly.
1.2.3.- Visualization in Evince does not match real doc. In drawing pages A3 sized the page is shown as empty and just some lines are seen as if was a 
2- Kpdf does not allow to print A3 sized. What it does is print the page reduced to A4 size. Even changing page size on printing options.
2.1.- Kpdf does show correctly watermark and is used for A4 printing. A3 printing was not possible as what does is reduce the size of page to fit in A4.
2.2.- No locks have been experienced with Kpdf.
2.3.- Kpdf is set in preferences to use all the processor cicles it needs to do the job, and keep everything in ram (presumed to ease the load of documents)
3.- Adobe Reader does not allow to print A3 sized. What it does is print the page reduced to A4 size or crop the A3 page in an A4 page so part of the page is print and the rest is not. Even changing page size on printing options.
3.1.- Adobe Reader locks whenever it wants and does not even show the menu to select options.

Most weird thing is that Evince did print that page range and afterwards did not feel to print again.

This PDF file handling is something linux has still a long way to improve. When having deadlines as this time it is nonsense to face always same issues with PDF printing, this has been like this since first dive into ubuntu. Hope gets better soon.

Best regards.
Xermán

---

