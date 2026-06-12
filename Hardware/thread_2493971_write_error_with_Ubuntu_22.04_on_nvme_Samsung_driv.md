---
title: "write error with Ubuntu 22.04 on nvme Samsung drive"
date: 2024-01-01
forum: Hardware
---

### Post by paluan-luca on 2024-01-01
Happy new year to everybody.
I'm using Ubuntu 22.04 LTS on the following configuration
Ryzen 7 5800
Aorus 570 Elite
32Gb ram
Geforce GTX 770
1Tb Samsung 970 evo

I often use VMWare virtual machine without issues except some I/O errors writing on samsung disk which requires me to restart the system.
I suspected the drive had some problems although SMART capabilities report the drive healthy.
So I replaced it with 1Tb samsung 980 pro, but I haven't resolve the issue.

I often got the the write error to the disk while I'm using a virtual machine and at the same time I 'm using firefox browser on the host, 
but very rarely it happened just using firefox alone.
The samsung 970 evo requires me to restart the system after the issue happens, and after ext4 journal repairs file system it correctly works.
The samsung 980 pro has more complicated issues because sometimes it is similar ti the 970 evo, but a couple of time i could not boot the system anymore:
once restarting multiple times in recovery mode I don't know how I finally could regularly boot, but last time I had to disconnect the drive from the motherboard to let it work again as the issue has never happened.

I checked both the drive with Samsung Magician on a windows system and are reported healthy

Thanks in advance for all the answers and advices

---

