---
title: "Multiple boot rework-grub"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by electrocutioner on 2006-02-11
I have been running a dual/triple boot under grub.
Suse linux,or windows,with the windows selection putting me into a windows boot selection screen to go into either winxp or winxp 64 bit.
I'd like to replace the winxp 64 bit partition with a linux partition and experiment with kubuntu.I am concerned that due to the complication of my partition table,a misstep might be quite inconvenient-any suggestions?
 This is my current partition table of a 100 gig drive-
/dev/hda   93.1 gb fujitsu-mhu2100AT
/dev/hda1 51.0 gb HPFS/NTFS             /windows/C
/dev/hda2 21.9 gb Extended
/dev/hda3 792.2 mb Linux Swap           swap
/dev/hda4 19.3 gb    Linux native           /
/dev/hda5 21.9 gb    HPFS/NTFS          /windows/D

 hda5 is what I'd like to change to install ubuntu.I've deleted this from the installer.I'm guessing that i set it as an extended partition.Can I mount this one as '/' as well,or will it conflict with my suse partition?will the grub bootloader from ubuntu recognize multiple installations of linux?

---

### Post by electrocutioner on 2006-02-13
8-[ :-({|=     anybody?

---

