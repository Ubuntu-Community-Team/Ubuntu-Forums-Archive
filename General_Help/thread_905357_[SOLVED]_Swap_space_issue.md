---
title: "[SOLVED] Swap space issue"
date: 2008-08-30
forum: General Help
---

### Post by dhimate on 2008-08-30
I resized my swap space today using GParted and Hardy live CD. 

I wanted to reuse the swap space which was previously allocated to Gutsy installation. 

Now when I see the disk status, It shows swap size as 1 GiB. which is correct.

[IMG]http://ajanukarn.googlepages.com/Screenshot--dev-sda-GParted.png[/IMG]


But when I see process monitor it shows only 392.2 MiB

[IMG]http://ajanukarn.googlepages.com/Screenshot-SystemMonitor.png[/IMG]

Why so? :confused:

---

### Post by bodhi.zazen on 2008-08-30
Is the swap partition in your /etc/fstab ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Vivaldi Gloria on 2008-08-30
Post the output of

```
cat /proc/swaps
cat /etc/fstab
sudo fdisk -l
sudo blkid | grep swap

```

EDIT: "Is the swap partition in your /etc/fstab ?" - I was thinking the same thing.

---

### Post by dhimate on 2008-08-30
I appreciate prompt response. Thanks guys. 

Yes the partition is there in /etc/fstab

Contents of /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=a8e9e680-f2d0-45db-a2ca-29e8e3073d61 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda13
UUID=3b2051d4-8ab5-4d74-9bef-b5cda191a607 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



cat /proc/swaps

> Filename				Type		Size	Used	Priority
/dev/sda13                              partition	401584	40248	-1



sudo fdisk -l

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2356    18844245    7  HPFS/NTFS
/dev/sda3            2357       19065   134215042+   f  W95 Ext'd (LBA)
/dev/sda4           19066       19457     3148740   db  CP/M / CTOS / ...
/dev/sda5            4208        6127    15422368+   7  HPFS/NTFS
/dev/sda6   *        2357        2767     3301294+  83  Linux
/dev/sda7            4207        4207        8001   82  Linux swap / Solaris
/dev/sda8            6128       10333    33784663+   7  HPFS/NTFS
/dev/sda9           10334       14536    33760566    7  HPFS/NTFS
/dev/sda10          14537       18739    33760566    7  HPFS/NTFS
/dev/sda11          18740       19065     2618563+  dd  Unknown
/dev/sda12           2768        4073    10490413+  83  Linux
/dev/sda13           4074        4206     1068291   82  Linux swap / Solaris

Partition table entries are not in disk order


sudo blkid | grep swap 
> 
/dev/sda7: TYPE="swap" UUID="948c3740-eb72-47d4-a434-2eae7d437831" 
/dev/sda13: TYPE="swap" UUID="3b2051d4-8ab5-4d74-9bef-b5cda191a607" 

/dev/sda7 was my old swap when I was using Gutsy. /dev/sda13 is my new swap. 
After installing Hardy, I thought I can exend my swap for Hardy by reducing size of sda7 and increasing size of sda 13. Currently I do not have Gutsy installation on my laptop.

---

### Post by Vivaldi Gloria on 2008-08-30
Hmm. I cannot see a problem in your output and I don't know what is causing the problem.

How about you try this: Start live cd and gparted. Delete both swaps and create a new single one. Then learn the uuid of the new partition, edit fstab and change the uuid of the swap line in fstab. Restart. Maybe this could work.

---

### Post by dhimate on 2008-08-30
I did not want to mess with fstab and menu.lst files. That was the precise reason I chose to keep my old swap partition with 8 mb size :) 

Let me wait for some time. Else I will do that. 

Thanks for response.

---

### Post by mc4man on 2008-08-30
Wouldn't hurt to try
> sudo swapoff -a followed by 
> sudo swapon -a or maybe just reboot

---

### Post by dhimate on 2008-09-07
Hi,

I followed Vivaldi's steps and I got my swap space back. Thanks for help.

However now, during boot up, after Ubuntu splash screen, it changes the resolution and starts printing those debug messages which are with [OK] [PASSED] [FAIL] status. I checked menu.lst file. it says "Quiet". I really don't need those debug messages. How to turn them off?

This has started happening after claiming swap space. I don't think there is a relation between swap space and boot configuration. Really confused due to this.

---

### Post by dhimate on 2008-09-21
I got this fixed. 

Please refer to [this]("http://ubuntuforums.org/showthread.php?t=746132") and [this]("https://bugs.launchpad.net/ubuntu/+bug/205990")

Thanks for the help guys. Cheers.

---

