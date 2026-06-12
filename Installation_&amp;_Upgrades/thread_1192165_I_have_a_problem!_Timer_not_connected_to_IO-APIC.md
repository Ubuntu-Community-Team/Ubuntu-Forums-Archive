---
title: "I have a problem! Timer not connected to IO-APIC"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by gatodemian on 2009-06-19
Hello,


When I install Ubuntu 9.04 desktop I have three erros.
Each time that I start ubuntu I have the same errors.

I have Windows XP in C: 25 GB - NTFS
I have Ubuntu in E: 77 GB - FAT32
[B]

Bellow Errors:[/B]

1.- MP-BIOS bug:8254 timer not connected to IO-APIC
2.- (13.212009) ata 5: SRST failed (errno = -16)
3.- (23.224009) ata 5: SRST failed (errno = -16)


**Bellow my computer information:**

AMD Athlon (tm) 64 Processor 3500+
Speed: 2200MHz

Memory:  1280 MB (256 MB dedicated to the Video RAM)

Integrated NVIDIA GeForce 6100 nForce 430



I read at differents blogs that the problem maybe it is because the Integrated NVIDIA.
But each time that I try go at ubuntu I have the same problem.

Can someone help me on this?


Thanks for your time.

---

### Post by gatodemian on 2009-06-20
Please, I need help on this.. I am comming crazy!!

---

### Post by presence1960 on 2009-06-20
Big mistake: Ubuntu cannot be FAT32, FAT16 or NTFS! It has to be either ext2, ext3 or ext4. There are a few others such as rieserfs. JFS which are given for filesystems in the Use as option in the installer, but I would stick with ext2,3 or 4.

If you installed Ubuntu and selected a windows filesystem as the file type your install is toast. I am not even sure if that would be allowed but if it is you had better reinstall this time using a Linux filesystem.

Prior to attempting to undertake an operation such as installing an OS one should become thoroughly familar with what it is they are going to do before attempting to install. Here are a few links for you to check out:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a free pdf Ubuntu Pocket Guide which BTW has a great how to on installation of Ubuntu

**A couple of other things to do : defrag windows at least once or twice prior to installing Ubuntu. Back up your data. Although the partitioning and installation processes usually run error free, there is always the chance something can happen. Do not be the one whining on here that you lost all your data. Back up prior to install. You should back up your data regularly anyways.**

also take a look at this : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
scroll down to the part showing the F6 oprions - try noapic.

---

### Post by mr_raider on 2009-06-21
I get the same error on an hp dv2 with amd neo 1.6GHz CPU and mobility 3400 series.

I AM using ext4. Ubuntu boots just fine, but I have no what idea what the error means.

I also get the ata softreset error, on all my jaunty machines. If it ain't broke, I say leave it :D

---

### Post by gatodemian on 2009-06-21
I am sorry.
I installed linux under ext4... 


I have 3 partitions:

C: Windows (NTFS)
**D: Linux (FAT32) --- ext4 (When I install ubuntu automatically the installer put linux under this category - **ext4**)**
E: Others (FAT32)


I think that is not the problem.

I believe the problem is with the Video integrated (NVIDIA).


thanks guys to help me!

---

### Post by gatodemian on 2009-06-23
Any idea?

:(

---

