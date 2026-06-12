---
title: "Problems with Brother HN-5070N printer"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by henriette_holm on 2005-08-15
Hi.
I have a Brother HL-5070N printer connected to a switch and with a static ip number. I'm not quite sure how to do the setup in Ubuntu. I choose "New Printer" followed "network printer" - after that I'm not sure about what to do. I've tried choosing "Unix Printer", typing the ip number in "Host" and then I can print the test page but nothing else.

Any suggestions?

-Henriette

---

### Post by David Haas on 2005-08-15
Henriette--I see that Ubuntu comes with PPD files for the Brother HL-5070N printer, so this printer should work well with Ubuntu. They are in the Brother directory at /usr/share/cups/model/foomatic-ppds/Brother:
Brother-HL-5070N-hl1250.ppd.gz
Brother-HL-5070N-hpijs.ppd.gz
Brother-HL-5070N-lj5gray.ppd.gz
Brother-HL-5070N-ljet4.ppd.gz
Brother-HL-5070N-Postscript.ppd.gz
Brother-HL-5070N-pxlmono.ppd.gz
I don't know if they differ and if so which would be best for you, but some other Forum members should know this.
I have had no experience with network printers, but the easiest way to install the drivers for printers is with the Gnome Printing application (System>Administration>Printing in the menu bar on top).After selecting your printer, select the PPD file by clicking through the directories listed above. I hope this note orients you better.
David

---

### Post by henriette_holm on 2005-08-16
Hi. I already tried that but thanks for your help. My problem is not finding a driver - it's the setup. I'm not sure what to choose where.

-Henriette

---

