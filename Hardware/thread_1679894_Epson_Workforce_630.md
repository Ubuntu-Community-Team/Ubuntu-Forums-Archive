---
title: "Epson Workforce 630"
date: 2011-02-01
forum: Hardware
---

### Post by mavazz on 2011-02-01
I just bought an Epsom Workforce 630 because the Canon scanner that I had is not compatible with Ubuntu.  I pulled up a SANE list that someone was generous enough to provide me, and it only goes to Workforce 610.  To avoid taking this unit out of the box if it isn't compatible, does anyone know?  It's an all-in-one unit.  Or maybe you can tell me where to get an updated SANE list?

Thanks in advance to those of you who go out of your way to help old ladies!

Mavazz

---

### Post by sisco311 on 2011-02-01
It should work with the drivers provided by Avasys:
[http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

It's also supperted by VueScan, a commercial scanner software:
[http://www.hamrick.com/](http://www.hamrick.com/)

---

### Post by mavazz on 2011-02-01
Okay, I'm stuck on the installation directions. First it had me install an LSB package. The manual asks for version 3.2 but only 4.0 is offered. I'm sure that's fine.

But then it tells me I need to install the driver. On the website it provides what looks like several different drivers, each for different architecture. My computer is an i686. I see a driver for i486, i386, x86_64, amd64, and src. Am I supposed to install all of those, or just one of them? I currently have all of them downloaded on my computer. The manual tells me to install these packages using either the terminal or the package manager. I can't seem to find any of these packages in the package manager, and the directions for installation in the terminal requires knowing specific information to type in, including architecture. So, I'm not really sure what to do right now. I guess I first need to know which architecture package to install, then I need to know how to install it. 

Thank you for your help!

---

### Post by sisco311 on 2011-02-01
For the printer you have to install:
epson-inkjet-printer-workforce-635-nx625-series_1.0.0-1lsb3.2_i386.deb

and for the scanner:
iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
and
iscan-network-nt_1.1.0-2_i386.deb


EDIT:
Oh, and just double click the .deb files one by one; the installation dialog will pop up.

---

### Post by mavazz on 2011-02-02
Thanks for your help!  Took a while, but we got it done!

---

### Post by sisco311 on 2011-02-02
My pleasure!

Don't forget to mark this thread as [SOLVED].

---

### Post by mulceber on 2012-04-30
Hey, sorry to resurrect a dead thread, but I ran into the same problem as the OP - using sisco311's advice, I was able to download the printer drivers, but I can't find where on the site I should find any of the drivers he mentioned for the scanner. Can anyone point me in the right direction?

---

