---
title: "Before I buy a new printer"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by simber on 2005-06-18
Hi you all
Looking some printers that are in the market and checking the compatibility
in linuxprinting.org, i dont find the following models :

the epson stylus c45ux 
the c65,
the samsung ml-1740. 

I just wanted to know if any of you have those printers and if they work in ubuntu

Thank you very much

---

### Post by psoleko on 2005-06-18
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)
I don't see anything about the ml-1740, although Samsung does make Linux drivers for most of its printers. The Epsons are supported by Gimp-Print methinks. 
[http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

---

### Post by David Haas on 2005-06-18
In general, its easier to set up printers that have PPD files already installed in Ubuntu. Looking in /usr/share/cups/model/gimp-print/4.2, where the Epson ppd files are stored, I don't see files for Epson Stylus C45ux or for Epson Stylus C65, though files are available for theC44ux (escp2-c43ux.ppd.gz) and for the C64 (escp2-c64.ppd.gz).  In /usr/share/cups/model/foomatic-ppds/Samsung I don't see a file for the Samsung ML-1740, but 3 files are present for the ML-1750 (Samsung-ML-1750-hpijs.ppd.gz
Samsung-ML-1750-ljet4.ppd.gz, Samsung-ML-1750-pxlmono.ppd.gz). Of course, you could download the files from the Web.
David

---

