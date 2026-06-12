---
title: "changing screen brightness"
date: 2009-09-07
forum: Hardware
---

### Post by Fittersman on 2009-09-07
Hey, I'm fairly familiar with linux but this one has me stumped.. Maybe someone here will know how to deal with this.

Basically, when I try to change the brightness with the Fn keys, the event is handled properly (ie. linux thinks the brightness is changing), but when you physically look at the screen it is very clear that the brightness has not changed.

If I use the brightness Fn buttons, the value in /proc/acpi/video/EVGA/LCD/brightness is updated, but the screen isnt changing.

I'm using debian (I know.. I know, this is ubuntu forums, but nobody at the debian forum would answer and ubuntu is pretty close) and my laptop is a HP Pavilion DV3-2150US, Intel T6500 | 13.3IN WXGA | Intel GMA 4500MHD

I found a few other DV3 users who have run into this problem, but none have a solution yet. Some are saying it's an acpi event that isn't being handled properly and can't be fixed until a new kernel is released?

Does anyone know what actually controls the brightness levels? Maybe I could look into that a bit further.

---

### Post by dv3500ea on 2009-09-08
I also have this problem but I have heard that it may be fixed in a future version from another dv3 user. [Here]("http://ubuntuforums.org/showthread.php?t=1258788&highlight=HP+DV3") is a thread of hp dv3 problems and solutions.

---

### Post by DigitalAxis on 2009-11-22
It's not an Ubuntu bug, at least.  I've switched to Fedora 11 (better integrated KDE) where it STILL has problems with screen brightness.  I'm hesitant to try Fedora 12 and have things get worse (and no, some of the stuff I use a lot is NOT on the liveCD)

---

### Post by lswb on 2009-11-22
You might try adding "acpi_backlight=vendor" (without quotes) to your kernel command line in grub. It will keep the kernel/video driver from trying to manage the brightness level and just leave it to the hardware.

---

### Post by dannymac64 on 2009-11-29
> **lswb said:**
> You might try adding "acpi_backlight=vendor" (without quotes) to your kernel command line in grub. It will keep the kernel/video driver from trying to manage the brightness level and just leave it to the hardware.

I tried this on my HP dv3 2155mx and it didn't work.  I too would love to know of anything that will correctly adjust the screen brightness.

---

### Post by zeroseven0183 on 2010-10-21
Same issue with me on an HP Pavilion dv3 notebook with Ubuntu 10.04.
Kernel version is already 2.6.32-25 (generic-pae)

---

