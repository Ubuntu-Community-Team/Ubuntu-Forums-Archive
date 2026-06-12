---
title: "gparted freezes while scanning a fat32 partition"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by wastvedt on 2009-08-07
Hi.
I've done a bit of research, and haven't found a satisfactory answer, but it could be that this question has already been addressed.
I have a desktop computer which I am converting from XP to Ubuntu 9.04 (yay!). I have succesfully eradicated windows and installed Linux, but the user data is on a separate disk, on a fat32 partition. What I want to do is shrink that partition, create a new ext3 partition on that disk (sdb), and move the data over, then delete the old partition. I've tried using gparted, but the program hangs when it starts to scan the fat32 partition. More accurately, it continues scanning, getting nowhere, for hours on end. I also tried using a gparted live cd, and the same thing happens. Any thoughts? Any more information I should provide? Thanks in advance for the help.
-Trygve

fdisk -l output:
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2   *         125        4866    38090115   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf7307a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        5339       30401   201318516    c  W95 FAT32 (LBA)

---

### Post by Zeroangel on 2009-08-07
Maybe you should launch a windows CD and run the scandisk or chkdsk commands to fix errors on the filesystem, then try. 

The other options are to run gparted from the terminal and see if it out puts any error messages.

You could also try an alternative partitioning program such as qtparted.

---

### Post by wastvedt on 2009-08-11
Sorry for the late reply, but I thought I should give an update on what I tried. I tried using the command line tool "parted", which seemed to work quite well to resize the fat32 partition. It still had errors, though, so as Zeroangel suggested, I ran scandsk using an XP CD. This fixed the errors, but I would not recommend doing that if you can help it. scandsk created several folders with a total of around 70,000 files in them, of the form FILE####.CHK. There are also now a random but large assortment of files on the drive which have disappeared, or have been reduced to a size of 32k. It seems that some of the 70,000 are the missing files, but weeding the few desired files out of that mess will be a pain.
So, for the future, if anyone else has this problem I would highly recommend copying the partition over to another computer or a separate disk, and then erasing and starting over.
For me, does anyone know of a utility for Linux which would look at a file's contents and attach an appropriate file extensions to the filename? It would make finding my files a lot easier. Thanks!
Trygve

---

### Post by Mark Phelps on 2009-08-12
From what you said, you ran chkdsk AFTER you messed with the FAT32 filesystem with the Linux utility.  Not surprised it ended up being trashed.  In future, you would do better running chkdsk BEFORE you use a Linux utility on a FAT32 volume.

As to the second question, looked for that myself and wasn't able to find anything.  I had an NTFS volume crash on me, ended up with a few hundred such CHK files, and wanted to do the same thing as you -- find a way to autoassign filetypes.

---

