---
title: "HP Deskjet 1000 printer on Ubuntu 12.04"
date: 2013-09-08
forum: Hardware
---

### Post by marvinsonhn on 2013-09-08
I just bought an HP printer HP Deskjet 1000 J110 series, connected via USB. The driver is hpcups 3.12.2, detected automatically.

Problems: Printing a page from LibreOffice Writer the printing gets cut off near the end of the page. I checked the paper size, and it's the correct one.

Printing from Abiword doesn't print anything at all. It appears in the queue, but it never gets to print anything.

Printing from Vim, there's an E365 error related with Postcript.

When I accessed my Windows XP partition and printed from Abiword, it worked just fine, although the size of the document in the Print Layout was shorter than in Ubuntu. I had to enlarge the letter size to fill the page.

---

### Post by marvinsonhn on 2013-09-09
I helped myself. I upgraded HPLIP following this [wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html") and made LibreOffice Writer print normally. I also made Vim print by defining the default printer with lpoptions. Abiword still doesn't print though.

---

