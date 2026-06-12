---
title: "printer not printing (canon pixma ip1800)"
date: 2009-08-22
forum: Hardware
---

### Post by rhythmiccycle on 2009-08-22
i found linux drivers at the Australian canon website here:

[http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=Printers&series=Colour+Bubble+Jet+Printers&model=PIXMA+iP1800&menu=Download](http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=Printers&series=Colour+Bubble+Jet+Printers&model=PIXMA+iP1800&menu=Download)

(couldn't find them at the US site) 

i ran:

J Printer Driver Ver. 2.70 for Linux (rpm Package for iP1800 series)

using alian

the printer shows, up but it will say "missing-cups-filter"

then i go into system->admin->printer

and right click on the printer icon, and check the box "enable"

that makes the "missing-cups-filter" message go away, but when i hit print, the computer says the job finished printing, but nothing happens, the printer doesn't move at all (btw it is turned on and pluged in, I checked)

what do i do?

---

### Post by rhythmiccycle on 2009-08-22
i deleted the printer and then tried to add it again and was told that i need to install "pstoscnonij" program

---

### Post by rhythmiccycle on 2009-08-22
i got it to work!!

i found this page:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP_1800](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP_1800)

under the notes it says

> 
 Notes

How to make this printer work in Ubuntu Intrepid 8.10:

1. sudo ln -s /etc/init.d/cups /etc/init.d/cupsys 

2. install two debs as described at [http://deviantcode.wordpress.com/2008/10/07/ubuntu-linux-canon-ip18002500-printer-drivers/](http://deviantcode.wordpress.com/2008/10/07/ubuntu-linux-canon-ip18002500-printer-drivers/) 

3. install [http://launchpadlibrarian.net/11424336/libxml1_1.8.17-14.1_i386.deb](http://launchpadlibrarian.net/11424336/libxml1_1.8.17-14.1_i386.deb) 

4. sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3


i did those steps, i'm using ubuntu 9, not 8. but it still did the trick.

---

