---
title: "Problem with Hard Drive. Partition."
date: 2010-07-24
forum: Hardware
---

### Post by DuckyVader on 2010-07-24
Ok i'm going to try my best to explain this. I have a 250gb hdd on my laptop. Whenever I try to install something it keeps warning me that I have low disk space, but i don't have anything on my laptop that would use that much space. I think it has something to do with the partitions on the disk. I don't know anything about that.

When i go to disk utility and select my hard disk, I see on Volumes it shows one partition says new volume 244gb ext4, then beside it is one that says Extended 5.8gb then below that one are 3 smaller ones 1.5gb Swap Space, 4.0gb ext4, and 242mb Swap Space. I have no clue what this means.

---

### Post by DuckyVader on 2010-07-25
Also when I go to Places>Computer and I try to double click on "250GB Hard Disk: New Volume" it says:

[B]Unable to mount location
[/B]
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found is syslog - try
       dmesg | tail or so


I have no clue to what this means.

---

### Post by DuckyVader on 2010-07-25
Im posting a screenshot of how I see the drive partitions on disk utility.

[[IMG]http://img695.imageshack.us/img695/5458/diskutility.png[/IMG]]("http://img695.imageshack.us/i/diskutility.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by jerrykenny on 2010-07-25
Thats a very unusual partitioning setup you have . . . . 

Also the SMART report reckons the hard drive is on its way out . . . 

I'd make a backup of any data you need from that hard drive pronto.

You might then try a complete reformat of the hard drive with a more orthodox partion table.

---

