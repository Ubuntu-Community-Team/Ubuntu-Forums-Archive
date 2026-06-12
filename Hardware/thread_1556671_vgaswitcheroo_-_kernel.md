---
title: "vgaswitcheroo - kernel"
date: 2010-08-19
forum: Hardware
---

### Post by puchaty on 2010-08-19
Hi, anyone got not 64bit kernel with working vgaswitcheroo working?

I need a deb files :)

Tried a lot of kernels but none of them has kernel/debug/vgaswticheroo.


Thank you

---

### Post by instantepiphany on 2010-09-09
BUMP__

Come on guys, 2 weeks and no answer??
I need this too, I run 64 bit ubuntu 10.04, and have switchable graphics. My problem is there are NO bios options related to the gpus, so i cannot set it through the bios. Ubuntu just uses the integrated intel, which is horrible for games or heavy 3d modelling/sculpting or photoshop. Yet, for some reason, it tells me to install the drivers for my ati radeon 5650 hd 1gb. On reboot, i get a blank screen. help someone!!!!

---

### Post by instantepiphany on 2010-09-23
Puchaty, GREAT NEWS, i have made LOTS of progress.
[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)
that is a link to installing a newer kernel, which includes vga_switcheroo :D
I am on my 5650 RIGHT NOW!! I am really happy. I am actually experiencing slightly lower performance than on the intel card, because i haven't installed the drivers yet. Fingers crossed. Does anyone more experienced know, will my laptop use two sets of drivers, one for each card? e.g i can install drivers while using the discrete card, and that shouldn't change the drivers for the integrated intel? Please reply soon.

---

### Post by Sub101 on 2010-09-23
Take a look here;

[http://wiki.archlinux.org/index.php/Alienware_M11x](http://wiki.archlinux.org/index.php/Alienware_M11x)

I know its arch (and not necessarily your laptop) but the author gives some good tips to using vgaswitcheroo.

---

### Post by instantepiphany on 2010-09-27
All I want to know is, to install drivers for the discrete card, Do i switch the the discrete card, logout and login, and simply install the drivers for the discrete? will that mean when i change back to integrated it will auto switch the the integrated drivers? please reply soon. I want to install the opensource ati drivers, as i have heard that the fglrx ones don't work :(

---

