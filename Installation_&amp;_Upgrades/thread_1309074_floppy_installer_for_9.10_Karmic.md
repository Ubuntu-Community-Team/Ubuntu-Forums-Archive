---
title: "floppy installer for 9.10 Karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by sosabe on 2009-11-01
Hi, everybody.

The fact that Ubuntu floppy installers do not exist is well-known. If we cannot use the cd/dvd installaton or pxeboot installation, we have to use loadlin or grub for the PC on which other Linux distribution, other Ubuntu version or Windows is installed. These methods are pretty difficult.

However, I modified the Fedora floppy installer ([http://www.thisiscool.com/fcfloppy.htm](http://www.thisiscool.com/fcfloppy.htm)) and made a Floppy installer for Ubuntu 9.10 Karmic(i386 desktop version). When you use this installer, you can boot Ubuntu installer and will install Ubuntu via network. I uploaded it on my homepage

[http://sarl-tokyo.com/wiki/index.php?Ubuntu%20Linux%20%28english%20page%29](http://sarl-tokyo.com/wiki/index.php?Ubuntu%20Linux%20%28english%20page%29)

If you use this installer, you have to make the first floppy disk writable. If your PC is too old to support ACPI and the installer does not work well, then you may succeed in installation by modifing the ubnutu.bat file in the first floppy disk as follows.

loadlin linux initrd=initrd.gz
->
loadlin linux noacpi acpi=off initrd=initrd.gz

---

