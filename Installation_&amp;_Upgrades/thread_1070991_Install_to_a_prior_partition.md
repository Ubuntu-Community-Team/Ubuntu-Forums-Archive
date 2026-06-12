---
title: "Install to a prior partition"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by womble3367 on 2009-02-15
I need to install Ubuntu to an existing partition that I created when I first formatted my HDD. It is my 3rd partition or 2nd one in the extended partition. Here is the output of sudo fdisk-l :


Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67286728

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6374 51199123+ 7 HPFS/NTFS
/dev/sda2 6375 91201 681372877+ f W95 Ext'd (LBA)
/dev/sda5 6375 12748 51199123+ 7 HPFS/NTFS
/dev/sda6 12749 25496 102398278+ 6 FAT16
/dev/sda7 25497 38244 102398278+ 7 HPFS/NTFS
/dev/sda8 38245 50992 102398278+ 7 HPFS/NTFS
/dev/sda9 50993 91201 322978761 7 HPFS/NTFS
ubuntu@ubuntu:~$ 

I would like to install Ubuntu on /dev/sda6....it has not been formatted with FAT16.

I have been unable to get by Ubuntu wanting to partitioning my last partition. 

NOTE: I originally posted this to Absolute Beginner Talk and Taurus was helping me, but has not responded for close to 2 weeks. So I thought I would try here.

Thanks for any help.

---

### Post by zvacet on 2009-02-15
Can you give as link with your previous post so that way we will not start from begining.And maybe Taurus join again.

---

### Post by womble3367 on 2009-02-16
Here is the thread that I posted previously.

[http://ubuntuforums.org/showthread.php?t=1053479](http://ubuntuforums.org/showthread.php?t=1053479)

---

### Post by Elfy on 2009-02-16
You will also need to have a swap partition so I would first open the partition editor on the livecd.

Delete sda6 and then create 2 new partitions - 1 for the install, format (to ext3 if you want as default) and 1 for swap - when you have done that you can start the install.

Once you reach partitioning - choose manual - pick the new ext3 partition - Edit the partition - pick / as themountpoint and ext3 as the Use As 

Close the edit partition window and continue

Swap will be dealt with by the installer if it is there and can be ignored.

---

### Post by womble3367 on 2009-02-22
Forestpixie, thanks for the information. I followed your direction and am now am using Ubuntu.

---

