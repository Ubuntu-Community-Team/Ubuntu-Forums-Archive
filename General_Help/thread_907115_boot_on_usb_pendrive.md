---
title: "/boot on usb pendrive?"
date: 2008-09-01
forum: General Help
---

### Post by _sAm_ on 2008-09-01
Will this work?:

PC with windows, and owner don't want to have Linux on it. The pc have two harddrives. 

Remove the disk witch Windows use and install Ubuntu on disk 2, but install /boot on an USB pendrive. Change BIOS so first boot device will bee USB(the motherboard support this). Connect the disk Windows use.
 
After this windows starts as before, but not if the USB pendrive with /boot is connected, then Ubuntu boots and I can use it.

Will I get problem with Grub?

---

### Post by girishsasikumar on 2008-09-01
Well if u do that I believe you will get a GRUB error at boot. 
You will have to edit the hard disk numbers in /boot/grub/menu.lst because when u install grub without the windows disk, linux drive will be hd0 and when u connect the windows hard disk, windows disk will be hd0 (as it will be primary master) and linux hdd will be hd1.

---

