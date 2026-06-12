---
title: "How do I increase Ubuntu partition on XP/Ubuntu dual boot"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by (_8*(l)Homer on 2009-02-15
Hi,

I've been using Ubuntu for about 6 months now, and I totally love it.  When I installed it, I only gave it 8GB of HDD space though.  I have more that I can devote, already partitioned off, but I can't figure out how to increase only the UBUNTU partition.

I have booted from the CD to use GParted.  The problem is that the partitions that show are the NTFS for windows, a couple others that I use for other stuff and the one I want to give to Ubuntu.

The actual Ubuntu partition that I want to increase does not show by its self, it shows as part of the NTFS system.

How could I increase only the Ubuntu partition?


-Joe
__________________________________
HP DV6000
2gb RAM
NV Go7400
320gb HDD
Ubuntu 8.10 Intrepid Ibex -- Generic Kernel

---

### Post by Mark Phelps on 2009-02-15
How about doing a "sudo fdisk -lu" from a terminal and posting the result?

Are you running Ubuntu dual-boot or did you install it using Wubi inside Windows?

---

### Post by (_8*(l)Homer on 2009-02-15
> **Mark Phelps said:**
> How about doing a "sudo fdisk -lu" from a terminal and posting the result?

Are you running Ubuntu dual-boot or did you install it using Wubi inside Windows?


Here is the output from fdisk.

```
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   129596354    64798146    7  HPFS/NTFS
/dev/sda2       129596355   137580659     3992152+   b  W95 FAT32
/dev/sda3       154191870   156296384     1052257+  d7  Unknown
/dev/sda4       137580660   154191869     8305605   83  Linux

Partition table entries are not in disk order
```

I think I used WUBI to install Ubuntu.  I want to combine sda4 (which I formatted as ext3) with the existing Ubuntu partition (not listed, or is part of sda1).

---

### Post by Mark Phelps on 2009-02-15
One of two things is true, either the last partition (sda4) IS the Ubuntu OS, or that OS exists as an app inside of Windows (sda1) -- but not both.  Since you said you formatted the last partition yourself and installed using Wubi, the latter of the two is true.

You can't combine the sda1 and sda4 because they're different types and there are two partitions between them. You could remove sda2 and sda3 -- but only if you know what's in them and don't mind losing them.  You still would not be able to combine the first and last partition, though; you'd have to either expand the NTFS partition or expand the last one.

There are utilities that can convert FAT32 partitions to NTFS and retain the data in the process, but I don't know of any that can change format to/from Ext3 and retain the data. 

To combine partitions of different formats, you would have to back off the contents of one, remove that one, expand the other one to fill the unused space, and restore the removed data to the expanded partition.

---

### Post by (_8*(l)Homer on 2009-02-15
Thanks for all of your help Mark.  Because I used Wubi, I will have to un-install then re-install Ubuntu outside of Windows.  It's not that big of a deal, I just have a lot of customization that I did and found a bunch of software and drivers that I like.

-Joe

---

### Post by Mark Phelps on 2009-02-17
Actually, since you used Wubi, and if what you want is to convert your machine entirely to Ubuntu, there are posts in this forum about how to move a Wubi installation to its own partition.  Once you do that, you can remove the MS Windows partitions, resize the Ubuntu partition, and modify GRUB;s menu -- and then have the whole drive dedicated to Ubuntu.  This can all be done without losing any apps or data.

---

