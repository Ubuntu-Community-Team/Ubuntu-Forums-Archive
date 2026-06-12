---
title: "Printer All-in-One"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by John McClane on 2005-04-15
I have an Olivetti JobJet M400, it's the same of HP OfficeJet 6110 but it have a different colours and the name in the memory.
If I use the hpijs the printer work correctly, but this drivers find only the printer and not the scanner. The hpoj drivers are competible with HP OfficeJet 6110 but not with my printer, if I install this drivers and launch the command ptal-init setup they not find my printer.

There are a way to force my printer to use the hpoj drivers?

ps: I connect the printer with usb cable.

---

### Post by neighborlee on 2005-05-06
[QUOTE=John McClane]I have an Olivetti JobJet M400, it's the same of HP OfficeJet 6110 but it have a different colours and the name in the memory.
If I use the hpijs the printer work correctly, but this drivers find only the printer and not the scanner. The hpoj drivers are competible with HP OfficeJet 6110 but not with my printer, if I install this drivers and launch the command ptal-init setup they not find my printer.

There are a way to force my printer to use the hpoj drivers?

ps: I connect the printer with usb cable.[/QUOTE]
---------
as long as your sane ( frontend) and xsane )( backend I think ) are installed then instaling 'hplip' might get this working...thats how I got my HP officjet 5500 all in one working although atm MY problem is that I can't get printing from gimp to work :(SHRUG

l8r
neighborlee

---

### Post by John McClane on 2005-05-29
[QUOTE=neighborlee]---------
as long as your sane ( frontend) and xsane )( backend I think ) are installed then instaling 'hplip' might get this working...thats how I got my HP officjet 5500 all in one working although atm MY problem is that I can't get printing from gimp to work :(SHRUG

l8r
neighborlee[/QUOTE]


with hplip installed xsane don't found my "scanner"

---

### Post by joeh on 2005-05-30
With hplip installed, make sure /etc/sane.d/dll.conf has a line with **hpaio** in it. If not, just add that line at the end of the file.

---

