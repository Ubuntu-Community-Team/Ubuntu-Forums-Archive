---
title: "Needed drivers for ATI RADEON XPRESS 200M"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by davidmoises on 2005-09-22
I have suse 10 intalled in my Presario M2000 (AMD sempron processor) but I can't find support for the video card- ATI RADEON XPRESS 200M. Ati sais that the manufacturer will provide the appropiate drivers but HP has none. Finally, there are some projects on sf.net that provide opensource drivers for differnt ATI video cards, but none seem to support the Randeon Xpress 200M.
Thanks for any information you might provide.

---

### Post by locutus42 on 2005-09-22
There are a few other laptops with these same chips and so there are threads and forums discussing how to get the ATI driver installed.

In these forums, look for stuff on the R4000 and otherwise, google for zv6000 and R4000.

I've had problems with ATIs drivers except the 8.13.4 driver and the Ubuntu 2.6.10 kernel.

I'm also disappointed to here ATI still saying to go elsewhere for support but atleast they are releasing drivers. And with all the laptops starting to turn out with the Radeon 200M chips, they're going to have to start considering full support for Linux. I hope.

---

### Post by zhensel on 2005-09-23
The 200M page at ATI's site does not link to linux drivers, but the latest driver [release notes](http://www2.ati.com/drivers/linux/linux_8.16.20.html) explicitely mention 200M support.  I believe the 200M can be had in many configurations (some with video memory, some only with shared memory), so I think ATI is hesitant to guarantee success on any particular hardware configuration that people have thrown together for such a young card.

People have had [trouble](http://ubuntuforums.org/showthread.php?t=64234&page=12&pp=10) with these drivers, though... particularly with widescreen displays.

I'm hoping it'll work well with the next release since my MSI-1013 is coming in the mail in a few days.

---

