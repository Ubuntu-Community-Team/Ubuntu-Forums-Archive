---
title: "Dual boot Win7 / EasyBCD problem"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by zmuth734 on 2009-09-26
I am having some problems with dual boot and my EasyBCD, I can get into win7 fine but when I try to boot into ubuntu, it just says:

> BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

Loading new partition

Bootsector from C.H. Hochst&#8222;tter


When I installed ubuntu I installed grub onto the ext3 partition bootsector.

Here is my partition setup:

[IMG]http://i36.tinypic.com/2nulkwo.png[/IMG]

Here is the EasyBCD settings I am using:

[IMG]http://i34.tinypic.com/2dinmrp.png[/IMG]


**Is there any way to ditch the whole easybcd/windows bootloader and install grub onto the MBR of the first disk which contains windows7?**

---

### Post by louieb on 2009-09-26
1st see if will boot at all (use a [Super Grub Disk)]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html") you might be getting if were GRUB a grub error 18, don't know what EasyBCD would call it. 

Anyway there is another problem your Ubuntu partition is only 2.3GB - due to a problem with the install thats the default. You would be able update or add programs until you give it more room.

---

