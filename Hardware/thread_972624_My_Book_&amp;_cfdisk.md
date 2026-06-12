---
title: "My Book &amp; cfdisk"
date: 2008-11-05
forum: Hardware
---

### Post by swbrenton on 2008-11-05
I recently bought a WD My Book 160GB external Harddrive.  After a lot of trial and error I finally have it mounted (I think) and I can see it on the File Browser, Nautilus 2.22.3.  It comes with some files already installed but I don't think I need them.  The files look like they are intended for Windows.  Also the File System used on the My Book is either vfat or msdos (depending on what you read).

I bought this HD to backup files from my computer.

When I issue the fdisk -l command, the HD shows up as /dev/sdf as shown:
[INDENT]Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19457   156288321    c  W95 FAT32 (LBA)[/INDENT]


Would it be a bad idea for me to use cfdisk and reformat this harddrive?  completely erasing all the pre-installed stuff?  I have never run cfdisk, but I have read some about it, and like I always say, "What's the worst that can happen?" :lolflag:

I welcome free advice.
Thanks
Stephen.

---

### Post by wgrant on 2008-11-05
I took a copy of the contents from my 1TB MyBook just in case, then fdisk'd it all away. If you haven't used cfdisk before, you might want to use gparted instead.

---

