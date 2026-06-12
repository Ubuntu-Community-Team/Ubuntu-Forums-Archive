---
title: "libata question"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by vob on 2006-11-27
Hi forum,  

I have been asking <a  href="http://www.ubuntuforums.org/showthread.php?p=1770325#post1770325 ">this</a> question recently, but got no answers so far. The problem is that when my Dell D620 wakes up after suspend, the cdrom is no longer found by kubuntu 6.06 (the drive starts working when a cdrom is inserted, but it's impossible to mount it - yes, it's a data cdrom which is perfectly detected before the suspend).  

My question now is: what will happen, when I manually unload and reload the libata driver from the kernel, or the ata_piix driver, which uses libata (both drivers seem to show up in dmesg). Do I run into losing my HDD as well and make my system ununsable after unloading any of these drivers? Or do you think that this procedure will have noc effect at all on my cdrom drive?  

Thanks for your suggestions!

---

