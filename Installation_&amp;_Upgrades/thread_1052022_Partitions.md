---
title: "Partitions"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by Holden99ca on 2009-01-27
Please forgive me if this question has been asked a million times before. I'm pretty new to ubuntu so I'm still a bit skittish. Anyway, I've installed it and it went almost perfectly. I have two hardrives: one 40 gig and the other 80 gig. My plan was to have the 40 gig where the OSs are installed (windows 2000 was already there) and the 80 gig where I put data. It's almost worked out that way. Somehow or other I've ended up dividing the 40 gig in half: half for windows and half for ubuntu (so far so good) but the 80 gig also got divided in half (??!!) and one half has completely disappeared. Thankfully all the data is still there so I'm not worried there--I just appear to have lost half the room on my HD. Advice or suggestions would be most appreciated. BTW, I installed Hardy Heron because 8.10 didn't seem to work properly on my system. Thanks in advance!

---

### Post by sookun on 2009-01-27
live CD?
well the first rule to any installation is to do a BACKUP of god knows how important files..;-) try installing gparted, look for in the Application>ADD/Remove here u search for it and install it. now u have the world most easy to use partition editor infront, u'll see all the partitions(even the one which disapeared)
now before messing things up, ntfs or fat will be the windows, ext3 and swap will be where hardy is and probably the rest is free space( well im just guessing) just select this free space and make another ntfs or fat or ext3, or u can make a logical partition out of it ie u can more partitions 
hope i was not too confusing

---

### Post by caljohnsmith on 2009-01-27
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output. That will give us a better idea what you are referring to.

---

### Post by Holden99ca on 2009-01-27
Thank you! This is the output:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ce44ce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38973689    19486813+   7  HPFS/NTFS
/dev/sda2        38973690    78156224    19591267+   5  Extended
/dev/sda5        38973753    76437269    18731758+  83  Linux
/dev/sda6        76437333    78156224      859446   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ddd980a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    79666334    39833136    7  HPFS/NTFS

---

### Post by caljohnsmith on 2009-01-27
You're right, it looks like your sdb1 partition on the 80 GB sdb drive is only 40 GB now. You could either use gparted (System > Admin > Partition Editor) to resize it to fill the drive again, or I would probably just create another partition with that space and use any way you wish (maybe more data storage). Would that maybe work for you?

---

### Post by Holden99ca on 2009-01-28
> **sookun said:**
> live CD?
well the first rule to any installation is to do a BACKUP of god knows how important files..;-) try installing gparted, look for in the Application>ADD/Remove here u search for it and install it. now u have the world most easy to use partition editor infront, u'll see all the partitions(even the one which disapeared)
now before messing things up, ntfs or fat will be the windows, ext3 and swap will be where hardy is and probably the rest is free space( well im just guessing) just select this free space and make another ntfs or fat or ext3, or u can make a logical partition out of it ie u can more partitions 
hope i was not too confusing

Thank you to both of you. I'm relieved. I've put on gparted and will spend a little time figuring it out. Re: backup, I couldn't agree more. The thing is what were my options? a)spend money I don't have on something to backup onto b)leave things as they are with windows totally crawling at a snails pace or c)switch to ubuntu, hold my breath and cross my fingers. I went with c.

All the best and thanks again!

---

