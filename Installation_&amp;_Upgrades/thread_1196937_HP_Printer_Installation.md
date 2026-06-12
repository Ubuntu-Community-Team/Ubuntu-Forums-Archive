---
title: "HP Printer Installation"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by fusi.eon on 2009-06-25
how do i install a HP Printer in kubuntu using the command "sudo apt-get install . . . " ?

---

### Post by Mark Phelps on 2009-06-27
You use apt-get to install packages, not devices.

The package you want is hplip.  Use apt-get to install that.

Alternatively, you could try installing your printer via CUPS.  Open a browser and enter "localhost:631" and that will bring up the CUPS printer manager, which you can then use to install printers.

---

