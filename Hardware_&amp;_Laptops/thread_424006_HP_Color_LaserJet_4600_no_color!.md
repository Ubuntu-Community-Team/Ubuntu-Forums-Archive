---
title: "HP Color LaserJet 4600 no color?!"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by mommebu on 2007-04-26
Installing the above printer in Feisty unfortunately results in wonderful GRAYSCALE prints, in fact looking in the configuration window shows "Color Model" "Grayscale" with the only other option being "grayscael inverted".
A look into the ppd file in /etc/cups/ppd/ confirms these options.
In case anybody knows, why a driver for a color laser printer is configured as grayscale even excluding the color options???
One year ago installing dapper the printer worked without troubles, though I don't believe this is a ubuntu specific issue, but rather a badly updated cups driver...

Any hint/help appreciated...

---

### Post by mommebu on 2007-04-30
Mangaed to recover the old driver file, in case a.body else needs it, let me know...

---

### Post by ramjet_1953 on 2007-04-30
This link should point you in the right direction:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_4600](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_4600)

If you want the additional control that HPLIP offers, make sure that you install python-qt3 and python-qt-gl using the Synaptic package manager.

Regards,
Roger 8)

---

### Post by Käferthias on 2007-05-07
Same Problem here. I "solved" it by using the HP C-Lj 4650 - driver.

---

