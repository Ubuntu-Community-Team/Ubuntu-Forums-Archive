---
title: "Install ubuntu 9.04 desktop edition at laptop"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by CS_Tux on 2009-09-19
Hello mates this is my first time here and Ubuntu generally, I have a laptop(Acer Aspire 6935G) with Windows Vista and a HDD of 320 Gb capacity.
This is separated at 144Gb Acer(C) and 140Gb Data.
I want to install ubuntu 9.04 without lost sth from HDD...I tried to install it normally but i dont have the option of INSTALL THEM SIDE BY SIDE, so i must go through Specify partitions manually but i have 4 sda and i am not sure which i must delete to install ubuntu without worry to delete my files...

---

### Post by dreamingdarkness on 2009-09-19
Got a few options here.
One is, while running Windows, install the WUBI version of Ubuntu. This gives you a 'virtual' back-end Ubuntu filesystem, which can be migrated (ONLY WITH EXTREME PAIN I ADD) to a real version if you like it.
Your other option is to go with a dual-boot setup. One thing you really want to be careful of is changing your Windows partition sizes. The MBR (Master Boot Record) can get messed up. So when you change the size to make space for your Ubuntu/Linux install, do it this way:
1. From within Windows, shrink the partitions you want to re-size and create empty space
2. From the LiveCD of Linux, format that space how you want it

The BEST dual-boot resource I have found is here: all credit goes to the author and maintainer of that site. Make sure you do a few things before you really get into the dual-booting though:
1. Back up irreplacable files to an external drive, USB, or remote storage.
2. Burn and verify a copy of the Ubuntu LiveCD.
3. Optionally also make sure you have a SuperGrubDisk burned
4. Have some time you don't desperately need your PC - it may go smooth, but if not, you don't want to rush.

Best of luck!

---

