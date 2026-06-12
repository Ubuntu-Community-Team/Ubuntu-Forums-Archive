---
title: "printer won't print PDF's"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by donkyhotay on 2007-03-27
I have an epsonRX500 printer that works fine until I attempt to print a PDF file. Anytime I print a PDF file it simply comes out as garbage. Problem persists regardless of the program I use (evince, xpdf, acroread). Text files and images work without any hassles whatsoever. Anyone have a suggestion on how to resolve this?

---

### Post by s0cket on 2007-03-27
Tried a different PDF viewer yet?  That would be my first troubleshooting step.  There are a few different PDF viewing packages.

---

### Post by donkyhotay on 2007-03-27
as I mentioned problem persists regardless of the program I use to view the file (evince, acroread, xpdf).

---

### Post by m83 on 2007-03-27
Do you have the same problem with other PDF files? I also had a problem with a stubborn PDF that won't print and I resolved it by printing to Cups-PDF and then printing the resulting PDF.

---

### Post by kerry_s on 2007-03-27
I find the best solution for PDF printing is using xpp(sudo apt-get install xpp) use that for the printer. just replace the printer command to xpp.

---

### Post by donkyhotay on 2007-03-27
Issue happens on all PDF's (I did test others) and happened even with I used xpp.

---

### Post by donkyhotay on 2007-03-27
After messing around a bunch I found the problem. Apparently for some reason CUPS is unable to print most PDF files I downloaded from the internet if I select "all" pages for the range when printing to any printer, even a "PDF printer". I found that if I printed a specific range of pages it will print just fine (even if this range happens to be all the pages within the PDF). For files I will only use once this is fine. For files I plan on using over and over again I print to PDF and simply replace the original file.

---

