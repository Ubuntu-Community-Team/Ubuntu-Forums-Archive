---
title: "SSD access problem"
date: 2016-05-19
forum: Hardware
---

### Post by macstl on 2016-05-19
I bought a 80 GB SSD 2.5" sata II for laptop.  I put it into a external sata enclosure  and format it ext 4 with gparted. It shows up in the list of drives in disk folder app but it won't open up so I can copy and paste files onto it. I tried formatting it as ext3 and fat32 but no change. Im running Ubuntu 12.04 on laptop thinkpad R61
However , it did let me install Ubuntu 16.04 onto it and will boot off it and I can access it from folder app unlike when I just format it.
If I plug in a non-ssd drive it mounts up and opens automatically in file folder app nautilus.
I want to store files on it as a empty drive formatted . Please advise
thanks
Joe Mc

---

### Post by Alcidious on 2016-05-19
You and I are having similar problems... I installed both an SSD and an HDD on a PC Tower. 

It comes down to setting and changing permissions ... something I'm still working on. Essentially, find the disk, find the mountpoint, then change group permissions. 

Check out the following link:
[http://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/](http://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/)

---

### Post by Alcidious on 2016-05-19
Actually, try the following article also: 
[https://ubuntugenius.wordpress.com/2012/06/07/ubuntu-hardware-permissions-how-to-set-ownership-of-drive-or-partition-internal-external-hard-disks/](https://ubuntugenius.wordpress.com/2012/06/07/ubuntu-hardware-permissions-how-to-set-ownership-of-drive-or-partition-internal-external-hard-disks/)

Changing the ownership of the directories worked for me, but these were for my other drives, not the drive where my installation is on (my SSD). Also, I cannot speak for the safety of this as a solution ...

---

### Post by Dennis N on 2016-05-19
> I bought a 80 GB SSD 2.5" sata II for laptop. I put it into a external sata enclosure and format it ext 4 with gparted. It shows up in the list of drives in disk folder app but it won't open up so I can copy and paste files onto it.

To access and use the drive to store your files, your user needs to be the owner of the file system that is mounted. See this thread:

[http://ubuntuforums.org/showthread.php?t=2320063](http://ubuntuforums.org/showthread.php?t=2320063)

In particular, post #2 shows what you need to do. Owner and group are normally both changed, as is done there.

---

### Post by macstl on 2016-05-19
I reformated the drive with fat32 and now it automounts in ubuntu 12.04 Lts which it did'nt before , I can r/w to it ;now . Im not understanding why but I got what I want.
Thanks to all for replying with good info I printed out at work for future reference.

---

### Post by X-RED_Tech on 2016-05-20
FAT32 is old, very limited and definitely not recommended for large drives and/or big files as it support up to 4GB only for a single file. As such, a simple image file from a full single-layer DVD (~4.38GB) cannot be saved in a FAT32 partition.

> [COLOR=#000000]Im not understanding why but I got what I want.[/COLOR]
The reason is because FAT32 does NOT support permissions. And have you really got what you wanted? Naaahhh... You're fooling yourself (read above). You would have done much better just following the previous suggestions in this thread.

---

### Post by macstl on 2016-05-20
> **X-RED_Tech said:**
> FAT32 is old, very limited and definitely not recommended for large drives and/or big files as it support up to 4GB only for a single file. As such, a simple image file from a full single-layer DVD (~4.38GB) cannot be saved in a FAT32 partition.


The reason is because FAT32 does NOT support permissions. And have you really got what you wanted? Naaahhh... You're fooling yourself (read above). You would have done much better just following the previous suggestions in this thread.

OK I will format with ext 4 and follow instructions posted thanks...

---

