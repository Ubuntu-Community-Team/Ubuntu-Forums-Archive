---
title: "Canon BJC-2100 Printer"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by mrzud on 2005-09-09
I am having trouble being able to pring with my Canon BJC-2100 Printer.
I am connected via USB.  When using Open Office printer administration, it shows the generic driver installed.  When adding a printer, my printer is not listed.

Should this printer be able to work with the generic driver?
Is there a better driver available?  If so, do you know where I could download it?

linuxprinting.org recommends gimp-print and says it supports the 2100, but I cant seem to get it to work.

Any help is greatly appreciated.

---

### Post by David Haas on 2005-09-09
mrzud--I see that Ubuntu 5.04 contains the PPD file for the Canon BJC-2100 by default, so you should have it. It's "Canon-BJC-2100-bjc600.ppd.gz" (without the quotes) and it's located in the Canon directory at "/usr/share/cups/model/foomatic-ppds/Canon". Did you use the Gnome printer application at System>Administration>Printing? Here, one selects the printer model and then the driver (PPD file). Generally, this is all it takes to install the printer. Of course,  other problems may prevent proper installation. This is especially so with Canon printers and others such as Lexmarks. After selecting the PPD file, Linux should place an unzipped copy at /etc/cups/ppd.
David

---

