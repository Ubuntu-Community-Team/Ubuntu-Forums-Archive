---
title: "Disk activity light stays on forever after attempt to Resume from Suspend"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by wbrells on 2006-07-10
Hello!

Even though I'm running a self-built desktop system (see below) it seems that this is the best place to report an unusual problem with Suspend/Resume.

I'm running an up-to-date installation of UBUNTU 6.06 and would really like to get suspend/resume to work (as it does fine under Win2K). After some "fiddling" (see below) it seems that the system is (probably) Suspending OK, but when I attempt to Resume the hard disk starts up & the disk activity light stays on FOREVER. I can't really hear any disk activity taking place, but the system seems "locked up" at that point. With the 'nvidia" driver installed, I just get a text cursor on the screen. (With the 'nv' driver, my monitor showed "No signal".)

I've tried just about all combinations of options in /etc/default/acpi-support and tried removing the 'splash' option in /boot/grub/menu.lst. As far as I can tell, none of these changes made any difference - the disk activity light still stays on permanently!

My system has an EPOX 8RGA+ motherboard witn 512MB of memory and an Nvidia FX5500 AGP video card. The primary disk is a 20GB Western Digital unit and the slave disk is an 80GB Western Digital. (I'm just testing UBUNTU 6.06...)

Can anyone suggest what my next step might be?

Thanks,
Wayne

---

