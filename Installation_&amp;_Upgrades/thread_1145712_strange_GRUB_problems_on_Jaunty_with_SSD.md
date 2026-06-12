---
title: "strange GRUB problems on Jaunty with SSD"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by tecie1980 on 2009-05-01
My system's SATA Solid state device (SSD) encounters GRUB error 22 when I attempt to boot it with multiple conventional hard disks in the system, however it works without incident when I boot the system with the SSD as the only connected SATA device or if I boot from the CD and select "boot from the first hard disk". The SSD is the first detected drive and is configured in my BIOS as the first boot device. 
Background:
I had to reinstall my primary desktop system after the boot drive died. I decided to replace my conventional 160G SATA drive with a 30G Solid state device. 
I have installed Jaunty on it.

I have attempted to rebuild grub twice, following this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 
However the problem was not resolved

At this point I don't think that grub is actually the problem, since it works when it is activated from the CD (wherein it is using my grub config files, as I changed the timeout value and it showed up) or where it is the only device in the system.

Any guidance would be appreciated.

---

