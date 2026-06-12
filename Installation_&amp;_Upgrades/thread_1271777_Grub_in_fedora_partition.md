---
title: "Grub in fedora partition?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by Blacklightbulb on 2009-09-21
I had Ubuntu installed in one partition and about 40Gb free space. On those 40GB I installed LVM partition for fedora but didn't install the fedora Grub bootloader.

What I want to do is install Grub on the LVM partiton for fedora and all it's kernel updates. Then I want create a link on the menu list in the GRUB (installed in the MBR) to link to the GRUB installed in the fedora partition? How can I do this?

EDIT: OK so I managed to install grub on separate boot partition for fedora and I chainloaded it trough the GRUB (installed in the MBR). However now when I try to access the Fedora Grub I go immediately into grub edit mode (grub>). This seems to be caused by the fact that I have no menu.lst in the grub file on the fedora boot partiton?

How is that possibe? How can I get it back?
Help!!

---

### Post by Blacklightbulb on 2009-09-21
Solved thanks!

---

