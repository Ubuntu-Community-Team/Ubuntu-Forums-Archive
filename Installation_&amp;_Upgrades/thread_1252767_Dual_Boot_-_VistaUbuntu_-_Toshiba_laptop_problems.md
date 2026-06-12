---
title: "Dual Boot - Vista/Ubuntu - Toshiba laptop problems"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Cereus on 2009-08-29
Hello,

I have just purchased a Toshiba laptop (Satellite L300D) with Vista installed and I want to make a dual boot. I've done this before with other systems but there is something beyond my experience happening here.

With the Vista installation I have four partitions (factory fresh, there is uncertainty what each partition contains from my readings online). Note, I burned my DVD recovery disks already.

1 - 1.46 GB (EISA Config)
2 - 7.57 GB (Primary Partition, not mounted and empty)
3 - 7.71 GB (Primary Partition, mounted as D: and empty)
4 - ~210 GB (System, boot, Page File, Active, Crash dump, Primary Partition, mounted as C:)

In the Vista partition manager I took this last large partition and split it. Now it is 150 GB and ~60 GB shows up as unallocated.

So far so good, I've read that the Ubuntu installer will identify this free space and use it for the installation. 

However, when I boot from the Ubuntu DVD and go through setup, in the partition manager I only have two options. The partitioner identifies all the partitions (and it calls the 7.6 GB partition the Vista (loader) and also the 150 GB as Vista (loader)).

My two options are: 
1) Automatic in which Ubuntu uses the entire disk and deletes the Vista partitions

2) Manual - but it calls the 60 GB unallocated space as unsuable

Any help would be greatly appreciated.

---

### Post by hal10000 on 2009-08-29
Please post the output of the command [COLOR="Red"]sudo fdisk -l[/COLOR]. (I gues you have booted the live-CD).

---

### Post by xsivone on 2009-08-29
I had the same problem as you trying to install Ubuntu NBR on my netbook.  
Boot from the DVD and go to Ubuntu Live.  When it starts go into partition manager and delete the partition that you want to make unallocated.  Then hit apply and it will unallocate it. 

Then close out, reboot to install and try. Now it gives me option to put in the free space.

I was trying this in the install process and I had the same unusable error.
When I use the partition manager in the Live DVD it works.

I hope this makes sense and helps.

---

### Post by Cereus on 2009-08-29
Results from my fdisk -l command:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27159934

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19899   158300156    7  HPFS/NTFS
/dev/sda3           28407       29413     8083456    7  HPFS/NTFS
/dev/sda4           29413       30402     7940096   17  Hidden HPFS/NTFS

When I go into the partition editor (off the live CD) it says it cannot make another primary partition (it already has four).

So it looks like the Toshiba set-up creates too many partitions and once I delete one I should be able to continue. Too bad other people have found the Toshiba help desk very unhelpful and can't tell what the partitions are for.

At this point I don't know how to proceed. I don't know if I can delete a partition, or if I could make an extended partition and install linux on that. Actually, I don't know anything about primary or extended partitions.

I'm going to do more reading and if anyone has a suggestion or link to offer it would be appreciated.

Cereus

---

### Post by hal10000 on 2009-08-30
Hi,
the best idea is to do as xsivone told you. You will need an extended Partition with two more logical partitions in it, because you need a root partition for your system and a swap partition.
Good luck.

---

### Post by Bucky Ball on 2009-08-30
If you've burned your recovery disks from the hard drive, I would burn them again so you have duplicates and wipe that partition (around 10Gb possibly). When I got my Vista laptop I backed up the recovery partition then wiped the drive, installed Vista from the recovery CD then manual partitioned the rest with Ubuntu.

The recovery partition is usually at the beginning of the drive, the fastest bit. Better to have an operating system there (and swap at the end).

/
/home
/swap

An option is to delete that recovery partition using Vista then resize the Vista partition into the free space. Then delete everything else to free space leaving only the Vista partition at the beginning of the drive. Then you should have no problems with the install. Just remember (and you probably do) Vista WILL NOT see your EXT3 or EXT4 partitions (EXT3 with some persuasion I've heard) so if you want to create a shared NTFS or FAT partition that both OSs can see, factor that in.

Just had another read of your post and yea, that is messy. I would personally start again but that is me. Ideally you'd want Windows on sda1. ;-)

---

