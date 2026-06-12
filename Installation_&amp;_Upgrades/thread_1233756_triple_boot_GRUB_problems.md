---
title: "triple boot GRUB problems"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Ubun2 Us3r on 2009-08-07
I am running a triple boot on my machine, between XP, Ubuntu and Fedora. For some reason, the GRUB that comes with Ubuntu does not automatically detect the Fedora partition. To fix this, I reconfigured the file /boot/grub/menu.lst and it works fine. But when I run the update manager in Ubuntu, it overwrites the changes to menu.lst. Can anyone help me to either make GRUB auto-detect the Fedora istall, or to stop the update manager to from overwriting menu.lst
Any help appreicated.

---

### Post by Herman on 2009-08-07
Are you placing your Fedora boot entry in the Debian Automagic Kernels List area of your menu.lst file?
Try pasting or typing your Fedora boot entry either above or below the Debian Automagic Kernels list area.
If you want Fedora to appear at the top of your menu, make the entry before the beginning of the Automagic Kernels List.
The beginning and end of the Debian Automagic Kernels List are clearly marked with signs in upper case letters.

Regards, Herman :)

---

