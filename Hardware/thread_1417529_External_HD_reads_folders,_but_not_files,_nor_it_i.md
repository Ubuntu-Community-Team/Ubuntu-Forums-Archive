---
title: "External HD reads folders, but not files, nor it is possible to create/copy/move"
date: 2010-02-27
forum: Hardware
---

### Post by Jonh Locke on 2010-02-27
Hello Everyone, 
 
I have an Iomega External Hard Drive of 1TB that has always worked just fine both in Ubuntu and Windows XP. 
About a week ago I was using the external drive on my Windows XP virtual machine (I have Windows XP working under Ubuntu 9.10 via VMware) and for some reason Windows crashed and I had to turn off the External HD without doing safe removal or unmounting it.
Since then i can't do anything with my External HD. If I turn it on using Ubuntu I can read the only the folders, but when I open them I can't see any files in it. Also I can't move/copy any folders to my PC's hard drive.
I would really like to know how can I put the External HD working again without formatting it, because I have files inside it that are really important for me. I appreciate any help I can get.

Thank you in Advance

---

### Post by Jonh Locke on 2010-02-28
One addition:

When I do the sudo fdisk -l command the result doesn't even show my external disk.

Result:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe911e911

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4118    33077803+   c  W95 FAT32 (LBA)
/dev/sda2            4119       12010    63392490   83  Linux
/dev/sda3           12011       12161     1212907+   f  W95 Ext'd (LBA)
/dev/sda5           12011       12161     1212876   82  Linux swap / Solaris

It only shows my Internal disk of 100Gb...

---

