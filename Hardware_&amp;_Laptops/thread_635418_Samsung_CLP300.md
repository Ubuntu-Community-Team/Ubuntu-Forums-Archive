---
title: "Samsung CLP300"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by ellis rowell on 2007-12-08
Does anyone know if the Samsung CLP300 Laser Printer will work with Ubuntu. It says it's compatible with Red Hat, Fedora and Mandriva, nothing about Ubuntu.

I don't want to go back to Windoze but it seems that it is the only way to use three printers that I have. Canon Pixma IP1600 inkjet, Brother DCP135C inkjet printer/scanner and a Minolta Magicolour 2400W Laser. I have TurboPrint, Foomatic and Cups but none of them have drivers for these that work.

---

### Post by linuxwizard on 2007-12-08
You can get the Brothers driver here
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

Look over this
[http://www.openprinting.org/show_printer.cgi?recnum=Samsung-CLP-300](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-CLP-300)
Should be able to get driver here
[http://www.samsung.com/us/support/download/supportDownMain.do](http://www.samsung.com/us/support/download/supportDownMain.do)

According to this looks like use the ip2200 driver
[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600)

Minolta Magicolour 2400W Laser
[http://www.openprinting.org/show_printer.cgi?recnum=Minolta-magicolor_2400W](http://www.openprinting.org/show_printer.cgi?recnum=Minolta-magicolor_2400W)
Driver
[http://sourceforge.net/projects/m2300w/](http://sourceforge.net/projects/m2300w/)

---

### Post by ellis rowell on 2007-12-09
I was thinking of buying a CLP300, I have a Minolta M2400W already and have spent hours trying to get it working with the above driver to no avail. I have also tried to get the Canon IP1600 to work but all prints send half a page blank then starts to print the page and runs out of paper.

Sorry, it looks as though MS has got me shackled. Do they run Guantamo?

---

### Post by linuxwizard on 2007-12-09
Samsung has really picked up the pace in supporting linux. I have seen articles where Samsung is including linux driver on a cd with new printers. If you are looking for a new printer look at HP very well supported in linux.

---

### Post by jmoellers on 2007-12-28
> **ellis rowell said:**
> Does anyone know if the Samsung CLP300 Laser Printer will work with Ubuntu. It says it's compatible with Red Hat, Fedora and Mandriva, nothing about Ubuntu.

I don't want to go back to Windoze but it seems that it is the only way to use three printers that I have. Canon Pixma IP1600 inkjet, Brother DCP135C inkjet printer/scanner and a Minolta Magicolour 2400W Laser. I have TurboPrint, Foomatic and Cups but none of them have drivers for these that work.

I have the very same printer and it works ... but only locally, no network printing from another Kubuntu (7.04 -> 7.10 :confused:). No photo quality, though, but b/w and color both work.
Go to [www.linuxprinting.org](www.linuxprinting.org), search the database for the Samsung CLP-300. They refer to a package foo2zjs.tar.gz (dunno exactly where it sits). Follow the directions given.

---

