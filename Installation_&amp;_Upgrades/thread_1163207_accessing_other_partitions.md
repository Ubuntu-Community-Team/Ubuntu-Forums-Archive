---
title: "accessing other partitions"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by dreamer565 on 2009-05-18
How do you get Ubuntu to mount or recognize other partitions on the same drive?
 
For example, in my machine i have 2 internal drives and 1 external.  if i boot off a partion on the external drive, then I can see at least 1 partition on the internal drives.  (there is basically only 1 partition to see on either). but i have other partitions and space to create partitions on my external drive, but how do i get it to see them or mount them within ubuntu.  I am looking for gui method is there one?
 
what's the easiest way to do that.  And/or resize existing partitions while inside ubuntu.

---

### Post by logos34 on 2009-05-18
maybe all you need to do is create a mount point and add entries to fstab.

Post the output of 

sudo fdisk -l

cat /etc/fstab

sudo blkid

---

### Post by shaloken on 2009-05-18
With my ubuntu, I just need to go on Places>>Computer and I see all my partition, even my external drive.
When I when to use one of them, I must double click on them to mount them (if it's not done before) and I can use them after

---

### Post by dreamer565 on 2009-05-19
@ logos34 here's the output you suggested -

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbc1cbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb0bbb0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14588   117178078+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002db5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      120949   971522811    c  W95 FAT32 (LBA)
/dev/sdc2          120950      121601     5237190    5  Extended
/dev/sdc5          121276      121579     2441848+  83  Linux
/dev/sdc6          121580      121601      176683+  82  Linux swap / Solaris
/dev/sdc7          120950      121253     2441817   83  Linux
/dev/sdc8          121254      121275      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc6 swap swap defaults 0 0
/dev/sdc8 swap swap defaults 0 0
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" UUID="6E44-72DD" TYPE="vfat" 
/dev/sda2: UUID="6A90726D90723F9D" TYPE="ntfs" 
/dev/sdb1: UUID="F6D44421D443E28B" TYPE="ntfs" 
/dev/sdc1: LABEL="My Book" UUID="8C43-8F03" TYPE="vfat" 
/dev/sdc5: UUID="9dbeab05-2ec8-4f8b-bd98-1169d52cafcd" TYPE="ext3" 
/dev/sdc6: UUID="bd9cfd31-fb61-4761-84ec-40f10cbad580" TYPE="swap" 
/dev/sdc7: UUID="2864d388-bd9e-4c88-b8f6-f76395cf653d" TYPE="ext3" 
/dev/sdc8: UUID="98188d93-b108-412e-8c72-5ea2af9eba04" TYPE="swap" 
ubuntu@ubuntu:~$

---

### Post by dreamer565 on 2009-05-19
@shaloken -
If i go to Places - Computer, I see several partitions but for example, right now i am booted from a "live cd" that is running from my external 1terabyte usb drive.  That actually exists in what appears to be a 2.5 gb media, and a filesystem (not sure which copy that created) my guess is the live version.  I can see it, I can also see a 2nd 1.5 GB media where i tried to install ubuntu and didn't know what i was doing and so didn't resize the partition correctly. I see both a CD Rom and CD-RW/DVD drive, a Floppy drive, and I see a 41.1 mb media (a partition on the 1st internal drive that is some sort of recovery partition with diagnostic tools by the pc manufacturer, a 79.9 gb media (the rest of internal disk 1), a 120 gb media (internal disk #2).  

What i can't see is the rest of my 1 terabyte External USB drive.  That's the drive I'm really looking for and want to set up to use while booted in Ubuntu.

My main goal is to be able to dual boot XP (which is on the 80 gb internal), and which i just fixed a mbr issue.  I also use the 2nd internal drive for storage and backups from the XP partition and want to share it with Ubuntu - so far that's not a problem.  

The other part is that i want to set ubuntu up correctly on the external USB drive and if i want to partition it (currently it has a partition with some data on it that I can't see) so that i can a) boot Ubuntu from it, and b) have at least one seperate partition to share out to the network.  Before i rebuild it, i want to make sure its going to work correctly.  

So far I've found that installing Ubuntu without changing any defaults means it won't size the partitions large enough to be useful - you can't even save settings or change settings in Firefox.  creating a "live-cd" version on the USB drive will boot and run, but each time you boot it it has forgotten all the settings you change to make it useful (the wireless card settings, the settings to support my dual monitor configuration, etc).  SO my next install i will use the advanced mode and partition the usb drive so that i hopefully will have a functioning os.

---

### Post by logos34 on 2009-05-19
> **dreamer565 said:**
> So far I've found that installing Ubuntu without changing any defaults means it won't size the partitions large enough to be useful...SO my next install i will use the advanced mode and partition the usb drive so that i hopefully will have a functioning os.

yeah, looks like the default selection ('guided--resize') didn't shrink your fat32 partition on the usb drive by much at all--it's taking up 99% of the space.  

I wonder if ubuntu's ubiquity installer tried but couldn't shrink sdc1  because it was heavily fragmented...Anyway, defrag or do what you have to on that partition, then use Gparted in ubuntu or on the ubuntu live cd to resize it.  Reinstall ubuntu.  Only need one swap.  Use [this as a guide]("http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32") to edit fstab if it still doesn't recognize sdc1

---

### Post by dreamer565 on 2009-05-19
Thanks again logos34.  I'll give it a shot.

also just found another post that points to this:
[http://mywebsite.bigpond.net.au/dfelderh/p24.html](http://mywebsite.bigpond.net.au/dfelderh/p24.html)
which looks to be a useful graphical guide for how to resize partitions and install ubuntu.  seems to include some good pointers to for those that might not feel like they know what they are doing.

---

### Post by logos34 on 2009-05-19
yeah Herman's pages are some of the best...it's been a while since I've been over there

---

