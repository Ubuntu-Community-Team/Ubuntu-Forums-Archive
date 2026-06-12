---
title: "Can't Print PDF Files At All"
date: 2009-03-17
forum: Hardware
---

### Post by web250 on 2009-03-17
This problem just started happening this evening...

I can't print any PDFs from any program (doc reader or adobe). I can print from other programs fine.

Tried restarting both the computer and the printer (HP Deskjet 2300, fairly new). Tried playing around in localhost:631.

What's up?

---

### Post by Domie on 2009-04-11
Same problem...

I can work around this by pdf2ps document.pdf and then print the postscript file, but this is clumsy.

---

### Post by Domie on 2009-04-11
Ah solution... Comes quicker than I thought...

Go to your printer settings, driver settings, miscellaneous: Ghostscript pre-filtering, change from no pre-filtering to something else (I changed it to "convert to PS level 2") and now I can print PDF files in Kubuntu.

---

