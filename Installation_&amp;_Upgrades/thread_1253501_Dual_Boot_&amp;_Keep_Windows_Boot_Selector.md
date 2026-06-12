---
title: "Dual Boot &amp; Keep Windows Boot Selector"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by FalconXR6Turbo on 2009-08-30
Hi guys,

I've been interested in Ubuntu for a while now and have been installing, playing around with, uninstalling, re-installing, etc, etc, it.

It may sound strange, but I want to dual boot W7 and Ubuntu (W7 installed first) but I want to keep the W7 boot selector (don't like GRUB sorry...it looks bad and confuses the missus...). 

Can this be done ? 

I really want to have Ubuntu (Jaunty) on my laptop permanently, but have decided that I will keep it only if I can dual boot using the W7 boot selector (to keep the peace...). 

Thanks in advance.

Cheers,

Turbo.

---

### Post by ithinkitschad on 2009-08-30
> **FalconXR6Turbo said:**
> Hi guys,

I've been interested in Ubuntu for a while now and have been installing, playing around with, uninstalling, re-installing, etc, etc, it.

It may sound strange, but I want to dual boot W7 and Ubuntu (W7 installed first) but I want to keep the W7 boot selector (don't like GRUB sorry...it looks bad and confuses the missus...). 

Can this be done ? 

I really want to have Ubuntu (Jaunty) on my laptop permanently, but have decided that I will keep it only if I can dual boot using the W7 boot selector (to keep the peace...). 

Thanks in advance.

Cheers,

Turbo.

You could always hide the grub menu and have w7 boot by default. Then when you want to boot into Ubuntu, you could press escape and boot into it. I dont think thats what your looking for though because thats still with grub.

---

### Post by dandnsmith on 2009-08-30
If W7 is anything like XP as far as the booting on your laptop (not guaranteed), then you can do it if you manage to get a copy of the grub boot code and invoke it from the W7 boot menu. You'd have to do something like install grub to the partition, and copy the code from there.

I found the info by googling, but don't have the pointers to hand.

---

### Post by Mark Phelps on 2009-08-30
> **dandnsmith said:**
> If W7 is anything like XP as far as the booting... 
It's not -- not at all like XP.  Windows 7 reuses the Vista boot loader, which was designed entirely new for Vista.

If you want to boot Ubuntu from an MS Windows boot menu. you need to install EasyBCD.  You can download that, as well as read through How-to's, at the NeoSmart Technology forums.

---

### Post by FalconXR6Turbo on 2009-09-03
Hey guys,

After searching I found an easy guide to follow.

It even has pictures.

Pictures are good... :D

Here's the link; [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

---

