---
title: "Cannot access hard drive"
date: 2014-12-20
forum: Hardware
---

### Post by darklaos on 2014-12-20
short story , energy went down during a memtest

keyboard wont work in bios... but i will resolve that later. 
my top priority is gaining access to the hard drive to recover my files....

the keyboard  works after a live cd boot. 

i think the hard drive is fried. but ubuntu recognize it  

there is a capture about what is going on.

help please guys

---

### Post by dave157 on 2014-12-20
Hi there Bummer about the drive man 

Depending on if you have another USB hard drive or memory stick big enough to copy your files that that drive, you could use the live Cd to copy files from your primary drive.

---

### Post by darklaos on 2014-12-20
the problem is that i cant access the disk to copy my stuff.

right now testdisk is running 
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Analyse cylinder  6376/19456: 32%ubuntu@ubuntu:~$ 


  HPFS - NTFS              0   1  1 19455 254 63  312560577
  HPFS - NTFS              0  32 33    12 223 19     204800 [Reservado para el s
  HPFS - NTFS              0  32 33    12 223 19     204800 [Reservado para el s
  HPFS - NTFS             12 223 20 19457  21 20  312371200

---

### Post by Mark Phelps on 2014-12-20
IF the NTFS becomes corrupted (which appears to be the case), Linux won't let you mount the partition -- to prevent further corruption.

You MIGHT be able to recover some of the files and folders using Windows data recovery apps -- since the partitions were Windows filesystems.

To do that, you need to be able to do the following:
1) Remove this drive from your machine
2) Attach the drive to a working Windows PC
3) Download and install "recuva" on the Windows PC
4) Run "recuva" to see what it finds

---

### Post by Reha_Andrew on 2014-12-21
Did you check disk utility. Check for partition errors. May be that was the reason.

---

