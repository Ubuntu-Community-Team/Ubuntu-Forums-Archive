---
title: "Epson CX4600"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by dalewis on 2005-06-24
I recently switched from Mepis to Ubuntu and found that my all in one printer/scanner no longer works. In mepis it worked by default even in Gimp. What package do I need to load in order to get my Epson to work? I know that Epkowa is down loadable but would rather use the libusb compatiable deb with Ubuntu if there is one.

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=dalewis]I recently switched from Mepis to Ubuntu and found that my all in one printer/scanner no longer works. In mepis it worked by default even in Gimp. What package do I need to load in order to get my Epson to work? I know that Epkowa is down loadable but would rather use the libusb compatiable deb with Ubuntu if there is one.[/QUOTE]
 [http://www.linuxprinting.org](http://www.linuxprinting.org)

I can't find that particular printer at that site (strange!). Maybe you have an epson stylus CX6400 ? If that's the case look here :
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX6400](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX6400)

according to that page gimprint is the recommended driver.

try installing these packages
cupsys-driver-gimpprint - Gimp-Print printer drivers for CUPS
cupsys-driver-gimpprint-data - Gimp-Print printer drivers for CUPS

by :
$ sudo apt-get install cupsys-driver-gimpprint cupsys-driver-gimpprint-data

you might also want to install documentation and localization by :

$ sudo apt-get install gimpprint-doc  gimpprint-locales

after this go to :
system->administration->printing->new printer and set up your epson stylus cx6400

If you have an 4600 you can try the same thing. Or google a bit to know which is the recommended printer driver.

---

