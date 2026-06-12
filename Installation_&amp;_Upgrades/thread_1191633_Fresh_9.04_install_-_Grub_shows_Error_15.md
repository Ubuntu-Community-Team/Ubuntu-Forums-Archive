---
title: "Fresh 9.04 install - Grub shows Error 15"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by garuff on 2009-06-19
Hi,
First posting here so bear with me if I'm revisiting the same old stuff (Sorry!)...
 
So... been playing around with Ubuntu on a work laptop, had no real trouble with it, figured I'd stick an old hard disk in my box at home and dual boot vista (I know...) and Ubuntu. So the setup is:
 
First Disk (SATA) - partition 1: Vista Partition 2: Downloads/unsorted Data
Second Disk (SATA) - Whole Disk: Data Backup
Third Disk (IDE) - For Ubuntu (set up with 16gb partition, Ext3, mount point /, and 4gb partition for swap file)
 
3rd disk is new to the system, stuck it in and booted up the live CD, installed with setup as above, removed CD and rebooted... to find 'Error 15' whilst GRUB was loading.
 
BIOS set to 1st HD, windows boots as you'd expect, BIOS set to 3rd HD, Error 15.
 
Now I'm guessing it's to do with MBR's, and not sure if I should have changed the advanced option relating to boot loader at the end of the installation setup...
Any thoughts greatly appreciated!
Thanks :KS

---

### Post by BbUiDgZ on 2009-06-19
try [this (CLICK ME)](http://www.supergrubdisk.org/) it might help.

---

### Post by garuff on 2009-06-19
thanks for the link, I'll give that a whirl just to see if I can get it working.

Any advice on what the issue might be and how to fix it manually still appreciated though (I'm one of those people who likes to 'tinker'!)...
Cheers

---

### Post by garuff on 2009-06-21
Right... so downloaded SuperGrub disk but no joy... the trouble is I'm not too sure how it needs to be setup, so don't really know what to change!! Any ideas anyone?!

---

