---
title: "Hard Drives Mounting Differently Everytime"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by spiderman1369 on 2007-07-11
I have a 120gb SATA Hard Drive with Ubuntu Feisty 7.04 installed on it
I also have a 3Ware 9500S-4LP SATA Raid Controller with (4) 320 GB SATA Drives on it.

My fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=602ab0d3-3c3c-4b62-88a7-a005e4d7f4e4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ae46a0c2-9597-4152-b1f4-9901e0c6073e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /mnt/blackbox_raid_array  ext3   defaults 0 0

Output from fdisk -l:

Disk /dev/sdc: 479.9 GB, 479965741056 bytes
255 heads, 63 sectors/track, 58352 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58352   468712408+  83  Linux

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       13995   112414806   83  Linux
/dev/sdd2           13996       14593     4803435    5  Extended
/dev/sdd5           13996       14593     4803403+  82  Linux swap / Solaris

Why the difference from fstab (/dev/sda1 and /dev/sdb1) to fdisk (/dev/sdd and /dev/sdc)???????

It didn't use to be like this. The raid drives don't mount automatically anymore either. Everytime I reboot the computer, the output from fdisk -l will be different (i.e. different /dev/sd? for both drives)

Yesterday I installed VirtualBox and did the seamless setup with WindowsXP. Which is pretty cool and works pretty good too.  Is that what's causing my "real" hard drives to behave so erratically??

What can I do to keep the hard drives in the fstab line-up???

Any help would be appreciated. I'm a newbie to so assume I know exactly everything your talking about. If you want me to run a command, please type it out.

Thanks!

---

### Post by dbarbour on 2008-01-28
Having the same issues with my drives. Two SATA drives on a PCI controller and an IDE drive. Did you come to a resolution? I went with mounting via UUID, but that's a pain in the ***. The drives shouldn't be mounting differently in the first place.

---

### Post by Daelyn on 2008-01-29
> **dbarbour said:**
> Having the same issues with my drives. Two SATA drives on a PCI controller and an IDE drive. Did you come to a resolution? I went with mounting via UUID, but that's a pain in the ***. The drives shouldn't be mounting differently in the first place.

I agree, I think that is the only "easy" solution to this.

Try find the UUID of the drives (I've forgotten the command) and use them as partition/drive identifications instead of the numbering system.

---

