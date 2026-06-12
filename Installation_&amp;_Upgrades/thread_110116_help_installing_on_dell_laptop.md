---
title: "help installing on dell laptop"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by oldmanstan on 2005-12-30
I'm trying to install ubuntu on my girlfriend's dell latitude pIII and having some issues. First: the live cd works just fine, in fact perfectly and i'm typing this from ubuntu running from the live cd on her computer. The problem is with resizing her winxp pro partition. She has one partition, a 20 gig ntfs. The ubuntu installer fails to adjust the partition automatically and every time I go to resize it manually I type the new size, hit enter and it comes back up with the old size. I also tried a freeware windows app but it said it couldn't resize because there were OS files on the drive. gparted will allow me to resize it in the program but then when i hit apply it does its dialog box with the progress bar thing, then says scanning system then pops up with the same old configuration. I've tried both leaving the extra space unallocated AND setting up the ext2 and swap partitions manually in gparted just to see if it would let me. When I set them up in gparted it gave an error message that the new partitions couldn't be created. I know that ntfs is a little weird but this is messed up, anyone got any advice?! I've never dealt with this filesystem before and it's making me crazy. Thanks in advance!

---

### Post by aysiu on 2005-12-30
The only partitioning tool I've found to always work is Mandriva's DiskDrake.
You can find it on the first installer disk of Mandriva or on PCLinuxOS.

---

### Post by Buffalo Soldier on 2005-12-30
Have you tried defragmenting the disk a couple of times? Sometimes that helps.

---

### Post by d11wtq on 2005-12-30
Yeah defragging can help since the filesystem isn't understood completely and file fragments can cause issues -- I'd do this as a precaution anyway.

Personally, the only tool I'd trust to resize an NTFS partition w/out data loss is Powerquest Partition Magic.  AFAIK everything else has been reverse engineered with a bit of hacking around until things "seem to make sense".

---

