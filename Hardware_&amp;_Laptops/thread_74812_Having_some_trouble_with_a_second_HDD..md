---
title: "Having some trouble with a second HDD."
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by *daniel on 2005-10-12
I'm trying to get a second hard drive running on my brand-spanking-new Ubuntu box and everything seemed to be going fine. I used fdisk and whatnot to create the partitions, mounted /dev/hdd1, and could read and write to the disk. 

I added it to fstab and then shut the box down (I have three boxes here and a 2-port KVM switch, so you see my problem) to work on later. When I booted her back up again a couple hours later, I got this:

Buffer I/O error on device HDD1, logical block 0


dan (so what in the world does that mean exactly?)

---

### Post by kanem on 2005-10-12
[QUOTE=*daniel]I'm trying to get a second hard drive running on my brand-spanking-new Ubuntu box and everything seemed to be going fine. I used fdisk and whatnot to create the partitions, mounted /dev/hdd1, and could read and write to the disk. 

I added it to fstab and then shut the box down (I have three boxes here and a 2-port KVM switch, so you see my problem) to work on later. When I booted her back up again a couple hours later, I got this:[/QUOTE]
I'm no expert, but I don't think fdisk changes fully take effect until a reboot. If you were reading and writing after the fdisk changes but before a reboot, maybe that could cause a problem. Also, did you actually format the partition as something (ext2, ext3, etc)?

I would try to fdisk it again, format the partitions and reboot and see if the problem is still there.

---

### Post by *daniel on 2005-10-12
[QUOTE=kanem]I'm no expert, but I don't think fdisk changes fully take effect until a reboot. If you were reading and writing after the fdisk changes but before a reboot, maybe that could cause a problem. Also, did you actually format the partition as something (ext2, ext3, etc)?

I would try to fdisk it again, format the partitions and reboot and see if the problem is still there.[/QUOTE]

I thought that might be a problem, too. So I formatted and rebooted without any reading or writing. Lo and behold, the same problem. And yeah, it's an ext3 partition.


dan (and hello, fellow Torontonian!)

---

### Post by kanem on 2005-10-12
[QUOTE=*daniel]I thought that might be a problem, too. So I formatted and rebooted without any reading or writing. Lo and behold, the same problem. And yeah, it's an ext3 partition.


dan (and hello, fellow Torontonian!)[/QUOTE]
Durn. I have no idea then. Sorry.

Go Leafs Go

---

### Post by taygan on 2005-10-18
try enabling dma 

sudo hdparm -d 1 /dev/hdd1 (that's your device right? or /dev/hdd?)

---

