---
title: "Cannot boot Ubuntu"
date: 2008-11-20
forum: General Help
---

### Post by Graham1 on 2008-11-20
Hi

Having used GParted 0.3.9 to reduce my Ubuntu partition from 10GB to 8GB, I am now unable to boot Ubuntu. I use XOSL to select my OS and GRUB is installed on the same partition as Ubuntu (sda2). All I get now is "GRUB _" on a black screen :confused:.

Any ideas what went wrong? 

:)

---

### Post by mikewhatever on 2008-11-20
Ubuntu partition number must have changed. Can you boot from the live cd and post the output of <sudo fdisk -l>.

---

### Post by plucky on 2008-11-20
> Having used GParted 0.3.9 to reduce my Ubuntu partition from 10GB to 8GB,

That would also change the UUID of the partition,so the UUID specified in /etc/fstab and menu.lst will need to be changed.


Good Luck

---

### Post by Graham1 on 2008-11-20
Thanks for the replies guys :). So, if I had used /dev/sda2 instead of the UUID, Ubuntu would have booted? As I had an image, I was able to restore back (having repartitioned to 10GB again). 

On a different note, is it normal for GParted to take around an hour to reduce an ext3 partition from 10GB to 8GB?

:)

---

### Post by plucky on 2008-11-21
> On a different note, is it normal for GParted to take around an hour to reduce an ext3 partition from 10GB to 8GB?


Depends on a number of factors like how full the partition is,how much data it has to move,other disk activity etc.Usually moving the starting point of a partition,means all the data in the partition has to be moved and so it could take a very long time.Just moving the rear of a partition,not so much.

Good Luck

---

### Post by Graham1 on 2008-11-21
> **plucky said:**
> Depends on a number of factors like how full the partition is,how much data it has to move,other disk activity etc.Usually moving the starting point of a partition,means all the data in the partition has to be moved and so it could take a very long time.Just moving the rear of a partition,not so much.

I'm not sure how much data was being moved but I had only just installed Ubuntu. I booted off Parted Magic and then run GParted. My setup is as follows:-

[XP, 10GB-ntfs][Ubuntu, 10GB-ext3][Boot, 100MB-fat][swap, 2GB][Data1, 20GB-ntfs][Data2, 20GB-ext3] 

I was taking 2GB off the beginning of Ubuntu so I could increase XP to 12GB.

:)

---

