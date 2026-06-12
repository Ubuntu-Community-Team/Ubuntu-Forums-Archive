---
title: "Wrong HDD size detected, Help? and Grub Geom error"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Ubersci on 2009-05-11
I have had the same problem with Ubuntu and Kubuntu 8.04 and 9.04, when installing it to my second hard drive it detects my 20gb hdd as 60gb hdd. They both install and work fine, but when i reboot i get a error message 'GRUB Geom Error. I have tried checking my BIOS, updating it and put the HDD to Master on my second IDE slot.

The drive is MAXTOR 4K060H3 ATA.

I duel boot vista using EasyBCD with Grub installed to the same locations as Ubuntu\Kubuntu.

Can anyone help?

---

### Post by dandnsmith on 2009-05-11
The GRUB manual says:

The location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls. This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install).

---

