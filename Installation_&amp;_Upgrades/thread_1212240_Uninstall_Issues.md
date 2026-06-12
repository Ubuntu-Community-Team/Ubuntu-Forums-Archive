---
title: "Uninstall Issues"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by tofangdar on 2009-07-13
Hi, first post, so be gentle.
 
A little while ago I installed Ubuntu 9.04 on a laptop which previously had Win XP Home. I did a full install, with no dual boot.
 
Unfortunately I now need to restore the laptop to its previous Win XP state.
 
So far I have taken the following steps:
 
1) Burned Super Grub Disk iso onto a CD.
2) Set BIOS boot sequence to CDROM/DVD first.
 
I have tried SGD 0.9745 and 0.9795 and neither will boot. 
 
Any assistance you can provide would be greatly appreciated.
 
T

---

### Post by mikewhatever on 2009-07-13
And what does Super Grub cd has to do with Windows? Are you going to reinstall, or are you simply trying to restore the boot loader?

---

### Post by tofangdar on 2009-07-13
I had read somewhere around here that you need to use Super Grub to restore the Windows Master Boot Record, which will then allow reinstallation of the Windows.
 
Please feel free to correct this, if it's a misconception.

---

### Post by mikewhatever on 2009-07-14
Simply put, Super Grub can place the Windows bootloader to the MBR, but that's irrelevant to reinstalling for the following reasons:

- Windows installer will wipe the MBR and place its own data there during the installation

- You have to boot from the installation disk, in which case, the MBR of the hard disk is not involved.

---

### Post by tofangdar on 2009-07-14
mikewhatever,
 
Thanks for the input. After a few hours of head-banging and CD-burning I was coming to the conclusion that a) I was barking up the wrong tree and b) that my oldish (2004) laptop's bios has problems in booting from CD (which is why the machine would boot from neither supergrub disks nor the XP disk.  Unfortunately, it appears that I have the last/latest version of that bios already installed.  
 
So from this point on, it's clear that this is not a problem I need to be sharing with you guys any more, but I'm grateful for the guidance you've provided.
 
T

---

