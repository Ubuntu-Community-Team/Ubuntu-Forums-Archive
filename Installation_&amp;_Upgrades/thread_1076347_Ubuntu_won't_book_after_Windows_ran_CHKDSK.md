---
title: "Ubuntu won't book after Windows ran CHKDSK"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by mike4604 on 2009-02-21
Hi all,

Last night, windows decided to run CHKDSK upon boot on my hard drive. After this, a lot of files related to my Wubi install were moved to a directory called \found.000 . 

Everything that Grub claims it is missing is in this folder; however, I'm not quite sure where to move the contents of this folder.

As of now, this is my current folder hierarchy in the found.000 directory:

found.000

-dir0000.chk
--root.disk
--swap.disk

-dir0001.chk
--a bunch of GENERIC files

-dir0002.chk
--default (no extension)
--device.map
--menu.lst
--menu.lst~

Thank you for your help in advance,
mike4604

---

### Post by mike4604 on 2009-02-21
Hi everyone,

The following steps were taken in resolving this issue:

1. In the ubuntu directory of root, create a folder called disks, paste root.disk and swap.disk into there. In disks, create another folder called boot. Paste all of the -generic files in there. Then, in boot, create a folder called grub, and populate it with the "defualt", "device.map", and "menu.lst" files.

2. copy the contents of X:\\ubuntu\disks\boot into X:\\ubuntu\install\boot

3. Reboot, it should work. :popcorn:

---

