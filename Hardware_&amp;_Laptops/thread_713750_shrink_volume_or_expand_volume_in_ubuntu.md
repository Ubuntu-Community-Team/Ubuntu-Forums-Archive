---
title: "shrink volume or expand volume in ubuntu"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by soumen08 on 2008-03-03
I run vista and gutsy and i've just created some free space on my windows drive. if i shrink that volume to create some "free space" can any of u help me to merge it with my current Z:\ or Linux drive? I had only 10 gigs and i need to install a few games.. Thanks for help :)

---

### Post by chewearn on 2008-03-03
Sure, post the output of:
```
sudo fdisk -l
```

Then, a bit of explanation which partition is which (if it is not obvious from fdisk output).  Then, tell us what you want to do.

Of course, if you know how to use a partitioning tool, then go ahead and run that.  My favorite partition tool [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by soumen08 on 2008-03-05
Thanks the output i get is:-
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56cc390a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3191    25631676    7  HPFS/NTFS
/dev/sda2            3192        8486    42532087+   f  W95 Ext'd (LBA)
/dev/sda3            8487        9729     9984397+  83  Linux
/dev/sda5            3192        8424    42030693+   7  HPFS/NTFS
/dev/sda6            8425        8486      497983+  82  Linux swap / Solaris

So what do i do now?

---

### Post by soumen08 on 2008-03-05
i want to take some space out of sda5 and put it into the ext3 drive. I dont know which that one is

---

### Post by chewearn on 2008-03-05
Your ext3 partition is /dev/sda3.  Use a windows partition editor tool (e.g. Partition Magic) to resize sda5 (NTFS file system).  Then, boot into a liveCD to resize sda3.  I recommend Gparted LiveCD; download from here:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

You might be able to use the Gparted LiveCD to resize the NTFS partition.  However, while the Gparted LiveCD website says it can handle NTFS partition, I can't guarantee how safe is it to use for this purpose, as I have no personal experience with this use case.

**Back-up all important data before you attempt the operations.**

---

