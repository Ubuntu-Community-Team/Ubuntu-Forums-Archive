---
title: "Printing to custom page size"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by bertvv on 2007-04-16
I want to print to index cards of 12.5x7.5 cm (about 3x5in). When selecting page setup from a print dialog, or Ubuntu's printer management tool, I can only choose from a limited number of page sizes (A3/4/5, Letter, Legal, ...), but the one I want is not there. It appears to be impossible to select a custom page size or to add new page sizes.

I can set the page size to 3x5in (not 12.5x7.5cm) in the CUPS web interface, but not in Ubuntu's printer management tool. Besides, that's not what I want. The default page size should be A4, but I want to be able to print to paper with other, custom, sizes.

A related question: When I have an OpenOffice document with paper size set to A5, why do I have to change the printer settings in the Print dialog manually to A5? If I don't do anything, the page is printed on A4, with the contents moved to the top left corner of the page.


Some information about the printer setup: it's a HP Laserjet 1100 printer attached to a Windows XP box and shared on my LAN. I have installed the drivers from HP instead of the limited MS drivers bundled with XP.

---

### Post by Scunizi on 2007-04-16
Depends on the driver.  What I've found is the default paper size is controlled in CUPS and the printer setup options are there for looks.  Drives me crazy too.

---

### Post by bertvv on 2007-04-17
Yes, I forgot to mention the drivers used by CUPS. I tried out the hpijs and the (recommended) ljet4 drivers. Both show similar behaviour.

---

