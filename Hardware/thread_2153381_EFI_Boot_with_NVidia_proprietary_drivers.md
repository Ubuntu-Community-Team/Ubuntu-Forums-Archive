---
title: "EFI Boot with NVidia proprietary drivers?"
date: 2013-06-10
forum: Hardware
---

### Post by blaz1ngra1n on 2013-06-10
Since macs use EFI, I decided to install Ubuntu via EFI without the CSM-BIOS emulation. However, after running sudo apt-get nvidia-current and sudo nvidia-xconfig, GRUB constantly pauses on a blank screen. When I remove "quiet splash" for verbose boot, it constantly boots to "low graphics mode." I believe this is occurring because the nouveau open source drivers and the nvidia-current are conflicting with each other. Therefore, I would like to remove the nouveau module via the recovery mode. My only problem is how to remove the nouveau module from xorg? Or how do I configure GRUB to ignore these open source drivers when I boot? I would prefer the proprietary drivers, rather than the nouveau. How can I resolve the issue?

---

### Post by blaz1ngra1n on 2013-06-18
I managed to solve the problems by looking in the /lib folder and deleting the nouveau from the gpu folder. I had to configure Xorg.conf with "UseDPLib" "off" under devices, but now I am booting with proprietary drivers.

---

