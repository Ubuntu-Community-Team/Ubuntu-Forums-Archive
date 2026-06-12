---
title: "grub menu"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by antel on 2009-08-22
why is it that my grub menu on one computer displays my other OS but also the recovery mode, and all other partitions? on my other computers it simply shows the 2 OS options.

---

### Post by Narada on 2009-08-22
I believe GRUB should attempt to auto-detect all bootable partitions when initially creating the menu... Dunno why it would make entries for your non-bootable partitions, though. If it bothers you it is possible to remove the offending entries from /boot/grub/menu.lst.

---

### Post by drs305 on 2009-08-22
I'm not sure from how you phrased your question. Do you mean why does it show the recovery mode options? And why it shows more than one *kernel* (i.e. multiple entries such as -14, -15, etc)?

If so, these are controlled by options in the menu.lst file. You probably have different settings on different computers.

An easy way to change the settings is with StartUp-Manager. It's a GUI app that will allow you to change the settings without manually editing the system file. 

To learn more about it, including installation and operating tips, click on the "SUM" link in my signature line.

---

