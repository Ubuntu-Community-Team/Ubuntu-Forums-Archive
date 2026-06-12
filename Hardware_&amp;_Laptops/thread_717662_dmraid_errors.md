---
title: "dmraid errors"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by xnszxdotnet on 2008-03-07
I have five hard drives in my system. the 320gb IDE is the main one with ubuntu installed on it. I would like to use the two 500gb sata drives and the two 750gb sata drive with my raid controller to storage all my movies and music. I'm trying to follow the fakeraid how to at :

[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

and I'm getting errors on the first step. I seem to not to be able to see the last drive in Partition editor the "sde" to format it. the "fdisk -u -l /dev/sde" command gives me a cannot open. I did the command with all of the sd drives and they all say "cannot open". i'm lost at what to do. here are my files from the dmraid -rD command. any help would help. 

lspci shows:
...
00:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
...

thanx

---

### Post by tormod on 2008-03-07
Cannot open? You are using "sudo", right? What does "ls -l /dev/sd*" say? Can you please attach "dmesg" output?

---

### Post by xnszxdotnet on 2008-03-07
```

booger@services:~$ sudo ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2008-03-06 15:56 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-03-06 15:57 /dev/sda1
brw-rw---- 1 root disk 8,  5 2008-03-06 15:56 /dev/sda5
brw-rw---- 1 root disk 8, 16 2008-03-06 21:49 /dev/sdb
brw-rw---- 1 root disk 8, 17 2008-03-06 21:52 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2008-03-06 20:56 /dev/sdc
brw-rw---- 1 root disk 8, 33 2008-03-06 20:59 /dev/sdc1
brw-rw---- 1 root disk 8, 48 2008-03-07 07:37 /dev/sdd
brw-rw---- 1 root disk 8, 53 2008-03-07 07:44 /dev/sdd5
brw-rw---- 1 root disk 8, 64 2008-03-07 08:18 /dev/sde


```


```
booger@services:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38643   310399866   83  Linux
/dev/sda2           38644       38913     2168775    5  Extended
/dev/sda5           38644       38913     2168743+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00056266

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051a54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b57f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001    5  Extended
/dev/sdd5               1       91201   732571969+  83  Linux

```

fdisk doesn't even show the sde drive??

here is the dmesg as a txt

---

### Post by tormod on 2008-03-10
Your dmesg is full of errors. Seems like you have a hardware problem. Either the sde disk itself, or on the same bus or the controller.

---

