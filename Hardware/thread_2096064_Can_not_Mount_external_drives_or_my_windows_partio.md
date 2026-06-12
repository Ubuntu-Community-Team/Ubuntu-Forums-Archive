---
title: "Can not Mount external drives or my windows partion"
date: 2012-12-18
forum: Hardware
---

### Post by cj360 on 2012-12-18
Hello, I've been reading these forums a lot since I installed Ubuntu for android related tasks and finally decided to make an account.

Here's some of my pc info: I've been running Ubuntu 12.04 on my Asus K53S for a couple months no issues. My HDD is about ~750 GB so I split that in half for the partitions as android source code can be greedy for space. (about 350~ per half) And since I have 6GB of ram I gave it a 5GB for swap partition. 

The issue is that recently since I've previously had windows 7 on my other partition I've removed it and upgraded to Windows 8. I put in my recovery cd after I set up windows to re-install grub. I noticed that the windows 8 partition wouldn't mount in natilus anymore. I did find a fix, but I didn't save the page it was on (damit) and it didn't last after a reboot. Now my usb drive won't mount either, nor does my elements 1TB external drive mount.


Here's the output of 'sudo fdisk -lu' and 'sudo blkid':

```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000ba50f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *     9875456   734130175   362127360    7  HPFS/NTFS/exFAT
/dev/sda3       734132222  1461817343   363842561    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1449142272  1461817343     6337536   82  Linux swap / Solaris
/dev/sda6       734132224  1449142271   357505024   83  Linux

Partition table entries are not in disk order
andrew@andrew-K53SD:~$ sudo blkid
/dev/sda2: UUID="9EACBEB8ACBE8A73" TYPE="ntfs" 
/dev/sda5: UUID="19445913-1923-495b-a150-d98dbb35f859" TYPE="swap" 
/dev/sda6: UUID="b7d507c4-9bb3-4086-a2d7-89bebfdd3d8b" TYPE="ext4"
```












Thanks in advance

---

