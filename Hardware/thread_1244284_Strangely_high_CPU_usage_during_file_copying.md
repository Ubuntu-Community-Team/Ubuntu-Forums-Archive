---
title: "Strangely high CPU usage during file copying"
date: 2009-08-19
forum: Hardware
---

### Post by dbzdeath on 2009-08-19
Hey,

I noticed recently that my CPU usage goes up to 100% when copying files, this should not be the case as DMA should leave little cpu usage. I first noticed it on my USB flash drive which was copying at only just over 1MB/s and my CPU usage was sitting at 100%(both cores combined), yet there was nothing using the CPU in top. I just tested copying a file from one location to another on the same hard drive (My main SATA drive in my laptop) and a similar result occured, in regards to the CPU usage. 

I've seen a few posts from other people reporting similar issues and there is a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775) that has just been ignored basically.

My details follow. 

model name	: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1986       1967         19          0         27       1095
-/+ buffers/cache:        844       1141
Swap:          972         14        958

$ uname -a
Linux Lappy 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64 GNU/Linux

My laptop is an Asus N50VN. Any help would be much appreciated. By the way, I'm far from a Linux n00b. Please post here if you're experiencing similar issues.

---

