---
title: "MF4150 linux driver help??? deb package where??"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by vkohli on 2008-03-10
Hello all,

I've been through the myriad of posts regarding the linux driver for MF4150. The link to Canon's UK site is down. At least from what I can tell, it has been down for days. Been the asia site and the australia site as well and managed to finally get somewhere. 

These sites have the source files for the UFR II driver only. For the life I me I keep getting errors building from the source. Have gtk installed plus dev. Tried --prefix to /usr. Errors upon errors. 

Apparently, from a post 3 weeks ago there was a deb install. I can't find any rpm or deb package from any of Canon's websites. So, if someone can direct, or can post a link to the deb files it would be very much appreciated. Any other help/hints would be nice as well.

---

### Post by MayOne.Net on 2008-04-29
I just installed my MF4150 this morning Following the advice from this thread, [http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1](http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1)

I went to:
[http://support-au.canon.com.au/](http://support-au.canon.com.au/)

It will ask you to make 4 choices via drop down menus:
choose a category - select all in one printers
choose a product series - select Laser Multi-functions
choose a product model - select Laser imageCLASS MF4140/MF4150
choose a document type - select Drivers & software

You want the: Linux Printer Driver (UFR II) Ver.1.60E 

The file downloaded is
UFR_II_PrinterDriver_for_Linux_Driver_v160.tar.gz.

Buried inside the tarball are the debs: /UFR_II_PrinterDriver_for_Linux_Driver_v160/32-bit_driver/debian/

There are actually two .debs (four if you count the 64 bit versions.)  At first, I only installed one of them and couldn't figure out why it wasn't working. After installing both, it works great.

---

