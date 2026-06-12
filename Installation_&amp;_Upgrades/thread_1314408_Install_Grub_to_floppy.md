---
title: "Install Grub to floppy"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by htfntuna on 2009-11-04
With every other Ubuntu version I have installed alongside my primary Win XP (including all dual and multi-boot configurations I have used), I was able to add the boot-loader to (df0). In Ubuntu 9.05, I simply replaced the (hd0) option during install by typing in (fd0) even though this was not an option on the drop-down menu.
 
I followed the same procedure with 9.10 and receive the fatal error that Grub could not be added to (fd0).
 
To be sure, I switched back to XP and formatted the floppy and ran a chkdsk, finding no errors.
 
I do NOT want to modify the boot sector on my hard disks! I have used this method to dual- and multi-boot with both Ubuntu and other Linux distros. To my mind, it is far preferable to simply be able to boot to the floppy when I want to access another OS. Grub on the floppy then merely reads the menu.list to which it points, which I can manually modify as I wish so that I can choose default OS, boot options such as boot order and countdown time, etc.
 
Then, when I want my system to behave as though it is a normal, single-boot system, I merely eject the floppy and Ubuntu sits there quietly until I need it again.
 
So: is 9.10 different in not allowing me to add Grub to my floppy during install? How can I achieve this?

---

