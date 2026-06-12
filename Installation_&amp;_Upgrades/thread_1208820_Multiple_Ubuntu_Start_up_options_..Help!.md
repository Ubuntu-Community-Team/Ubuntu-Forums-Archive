---
title: "Multiple Ubuntu Start up options ..Help!"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by joeylw on 2009-07-09
i have about 5 diggerent ubuntu startup options i was woundering if there is any way to get rid of the multiple options or hide the choices

---

### Post by Shazaam on 2009-07-09
Two ways...
1. Install StartupManager with Synaptic.
2. Manually edit /boot/grub/menu.lst

Using StartupManager you would go to the Advanced tab and enable "Limit number of kernels in the boot menu".

Manual edit of menu.lst...
A. Open terminal (Applications>Accessories>Terminal) and enter this-
```
gksudo gedit /boot/grub/menu.lst
```
(that is a lower case L not the number 1)
b. When it opens use your # key to comment out the unwanted entries like this-
```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		55357815-4cd9-4d5d-8696-234afcd7c0e3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55357815-4cd9-4d5d-8696-234afcd7c0e3 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		55357815-4cd9-4d5d-8696-234afcd7c0e3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=55357815-4cd9-4d5d-8696-234afcd7c0e3 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		55357815-4cd9-4d5d-8696-234afcd7c0e3
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=55357815-4cd9-4d5d-8696-234afcd7c0e3 ro quiet splash vga=771 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		55357815-4cd9-4d5d-8696-234afcd7c0e3
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=55357815-4cd9-4d5d-8696-234afcd7c0e3 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		55357815-4cd9-4d5d-8696-234afcd7c0e3
kernel		/boot/memtest86+.bin
quiet
```
Remember that putting a # in front makes grub IGNORE the line so make sure you put it in the right place.
C. Go to File>Save, Ubuntu normally saves your previous version as menu.lst~ or menu.lstbackup.
You can also uninstall the kernels using Synaptic but it is better to leave them in case an update borks your system.

---

