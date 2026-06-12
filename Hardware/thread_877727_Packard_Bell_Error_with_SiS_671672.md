---
title: "Packard Bell Error with SiS 671/672"
date: 2008-08-02
forum: Hardware
---

### Post by Mery on 2008-08-02
Hi
My first thread so I want to say Hello to everybody :D.

Now about my problem. I have a Packard Bell MH35-U-073 Notebook with Pentium Dual Core T2370 1,73GHz, 3GB DDR2, SiS 671/672 motherboard with integrated SiS Mirage3 graphics, Seagate Momentus 160GB SATA. Installed Ubuntu 8.04. I defeat problems with running the Ubuntu on this notebook by adding the ```
"noapic" "nolapic" "acpi=off"
``` when runing the install and later at the kernel in /boot/menu/grub.lst
Now I try to install a 2D graphic driver (3D driver still don`t exist??) following this thread:
[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)
I downloaded the package, copy the drivers to ```
/usr/lib/xorg/modules/drivers/
``` and try to run:
```
sudo dpkg-reconfigure xserver-xorg
```
I answer some questions about language, keyboard and I back to console with error:
```
FATAL: Error inserting battery (/lib/modules/2.6.24-20-generic/kernel/drivers/acpi/battery.ko): 
No such device
```
How skip this error? I see the same error while system is loading (I hate the splash). How successfully install drivers for SiS Mirage3 graphic in my notebook?

---

### Post by Mery on 2008-08-05
Nobody can help??

---

