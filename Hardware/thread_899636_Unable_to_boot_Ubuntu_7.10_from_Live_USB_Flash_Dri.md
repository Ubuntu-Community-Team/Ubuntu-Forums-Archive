---
title: "Unable to boot Ubuntu 7.10 from Live USB Flash Drive Sandisk Cruzer"
date: 2008-08-24
forum: Hardware
---

### Post by Fastjack77 on 2008-08-24
Hi all,

I'm trying to boot my computer from a USB Flash Drive, but have been unsucessful so far.

- The USB flash drive is an 8-meg Sandisk Cruzer Contour (brand new).
- My BIOS successfully detected the flash drive and is currently set has 1st drive to boot from.
- On my computer, the flash drive is working fine (r/w) on Windows 2000 Pro and Linux 7.10.
- Two partitions exists, one contains the 7.10 Live CD under FAT 16, the other is simply an empty ext2.
- I've tested my flash drive from several USB connectors to check if it may be damaged, and it's not.
- When inserting the flash drive, all partitions get mounted, plus a "virtual" cd appears containing the U3 system (only for windows).
- Keep in mind that I'm new to linux.

Here is how the partition looks like:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          92      738958+   6  FAT16
/dev/sda2              93         996     7261380   83  Linux

When booting from the flash drive, I eventually see a black screen with a white cursor flashing; nothing else happens.

Any suggestions would be really appreciated.

Thanks in advance!

---

### Post by Fastjack77 on 2008-08-24
Should this topic be moved to "Installation & Upgrades" ? If so, please don't hesitate.

---

### Post by Fastjack77 on 2008-10-16
Basically, I'm trying to boot ubuntu from a flashdrive. Any suggestions?

---

