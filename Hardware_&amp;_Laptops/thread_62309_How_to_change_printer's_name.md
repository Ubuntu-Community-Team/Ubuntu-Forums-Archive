---
title: "How to change printer's name?"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-09-04
DOes anyone know how to change name of the printer? I have Stylus Photo 790 and when I installed it the default name is Stylus-Photo-790. I tried gnome-cups-manager, but it does not allow to change the name of the printer, only description.

Help will be very appreciated...

---

### Post by vruum on 2005-09-04
Okay, I'm not sure if there is a graphical tool to do that, but you could change the name in the printers.conf file. open up a terminal and type:

sudo gedit /etc/cups/printers.conf

on of the first lines will look something like this
<Printer Stylus-Photo-790>
simply change the "stylus-photo-790" to the new name, and restart cups

sudo /etc/init.d/cupsys restart

---

### Post by foxy123 on 2005-09-04
[QUOTE=vruum]Okay, I'm not sure if there is a graphical tool to do that, but you could change the name in the printers.conf file. open up a terminal and type:

sudo gedit /etc/cups/printers.conf

on of the first lines will look something like this
<Printer Stylus-Photo-790>
simply change the "stylus-photo-790" to the new name, and restart cups

sudo /etc/init.d/cupsys restart[/QUOTE]
thanks a lot, it helped...

---

### Post by foxy123 on 2005-09-04
[QUOTE=foxy123]thanks a lot, it helped...[/QUOTE]

actually not exactly... I was able to change the name of the printer, but after that I was not able to print to it... it is wierd... should've I done anything else?

---

