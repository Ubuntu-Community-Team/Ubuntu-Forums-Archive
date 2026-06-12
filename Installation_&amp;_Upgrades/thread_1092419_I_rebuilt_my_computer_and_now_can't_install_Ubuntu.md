---
title: "I rebuilt my computer and now can't install Ubuntu"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Zaragon on 2009-03-10
Vista was getting balky on my dual boot computer so I scrubbed all OS's and rebuilt and reinstalled.  Vista is fine, but Ubuntu 8.10 will not install.  after going through uneventful install, reboot results in grub error 22.

I'm thinking hardware incompatability.  Here's what's new:

Asus P5Q3 delux MB, Core 2 Quad Q9400, DDR3, Creative X-Fi Titanium.  Anyone see anything that might make install bomb?

Thanks

Zack

---

### Post by mkvnmtr on 2009-03-10
Have you found out what grub error 22 is? I bet when you do you lill know what to do to fix grub.

---

### Post by Zaragon on 2009-03-10
Error 22 means GRUB can't find nacessary files.  By the way, I also added a new video card: a GeForce 9600 GT set up as PCIE2.

---

### Post by Neo_The_User on 2009-03-10
It means it can't find the kernel binary. Now... you could've just told him that. Binary = vmlinuz located in /boot. Post your menu.lst and all your files in /boot. ls output for /boot, cat output for menu.lst. If you provide me that information I can teach you how to fix it.

---

