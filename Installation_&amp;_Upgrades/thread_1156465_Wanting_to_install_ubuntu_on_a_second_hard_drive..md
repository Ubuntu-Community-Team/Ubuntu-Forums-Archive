---
title: "Wanting to install ubuntu on a second hard drive."
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Cam42 on 2009-05-11
So here's my situation.
1 80 GB Hard Drive with Windows XP
1 20 GB Hard Drive with nothing on it.

What I want to do is put the second (20GB) Hard Drive into my computer, and install ubuntu on it. What I would like to know, if it's possible to be able to boot into grub and have the option to boot into XP or Ubuntu, while they are both on separate hard drives. Is this possible at all?

---

### Post by orange-wedge on 2009-05-11
that is possible...

what will happen is grub should find your master boot record on your windows hard drive and then write over it with the location of both boot partitions (windows and ubuntu).

---

### Post by HippieDave on 2009-05-11
I have similar situation, although the two internal drives I'm working with are 160GB each.  My question is really how to best set things up to have option of working in either XP or Ubuntu.  Right now I just use second drive to hold backup mirror image of C drive (use Acronis).  I would also like to access common data files, docs, pics, mp3 files, from either U or XP (if that's possible).  What's the best way to configure the drives? Partition C into U and XP? Load U onto the second drive and leave XP on C?

---

### Post by Cam42 on 2009-05-11
How would I go about installing Ubuntu in this situation?

---

### Post by orange-wedge on 2009-05-11
ok you first will need to install your hard drive... then boot from the installation disk...

when you get to the section to setup your partitions you will want to choose the manual option.  from there you will see the available disks to partition along with your existing windows xp partition.

if you have SATA drives then the drive labels will start with "sd" and if you have PATA drives then they will start with "hd"

as an example lets say your windows xp partition is sda1. then you will most likely see your second hard drive as sdb.  you will need to create your linux partitions on that drive. at the very minimum you will only need two partitions to install ubuntu:

the root partition with the mount point "/" formatted with ext3.
and a linux swap partition

i usually like to make my swap partitions twice the amount of ram i have installed.

---

### Post by Cam42 on 2009-05-11
PATA?

I'm gonna sound like a n00b here, but I've got IDE Drives... are these the same?

EDIT: and this is using the Live CD, right?

---

### Post by orange-wedge on 2009-05-11
> **HippieDave said:**
> I have similar situation, although the two internal drives I'm working with are 160GB each.  My question is really how to best set things up to have option of working in either XP or Ubuntu.  Right now I just use second drive to hold backup mirror image of C drive (use Acronis).  I would also like to access common data files, docs, pics, mp3 files, from either U or XP (if that's possible).  What's the best way to configure the drives? Partition C into U and XP? Load U onto the second drive and leave XP on C?

i actually did this recently with my netbook... you can install Ext2Fsd on XP to be able to read/write to ext2/3 linux partitions.  this will setup a new drive letter (D:, E:, etc...) for each linux partition you want to access.

and then to read/write to your windows NTFS partition is already pre-built into ubuntu, you just need to manually add the option to mount the NTFS partition at boot:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

to figure out your XP partition device label run the following command:
[HTML]sudo fdisk -l[/HTML]

and i would recommend using the UUID for your windows partition in your /etc/fstab file:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by orange-wedge on 2009-05-11
> **Cam42 said:**
> PATA?

I'm gonna sound like a n00b here, but I've got IDE Drives...

EDIT: and this is using the Live CD, right?

yeah PATA=IDE... for some reason people started calling them PATA (Parallel ATA) to match the acronym of SATA (Serial ATA).

just googled for how to setup the partitions...  but i guess i was wrong with the labeling... (its been a while since i've setup a partition for a PATA drive) all drive labels will start with "sd"

but the main identifier between the two drives will be the third letter.  ie your XP drive may have sd**a** and your future ubuntu drive may have sd**b**.  if you had a third drive installed it would be labeled sd[B]c

[/B]the fourth identifier in the partition labels is the partition number.

heres the scheme for my installation:

[html]
jimmy@orange-wedge:~$ sudo fdisk -l
[sudo] password for jimmy: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc254c254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
jimmy@orange-wedge:~$ 
[/html]i only have one drive installed on my laptop...

while here is my media server setup:
[html]jimmy@galaxy-bounce:~$ sudo fdisk -l
[sudo] password for jimmy: 

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19d93027

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14         535     4192965   82  Linux swap / Solaris
/dev/sda3             536        1840    10482412+  83  Linux
/dev/sda4            1841       36481   278253832+  8e  Linux LVM

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   8e  Linux LVM
jimmy@galaxy-bounce:~$ [/html]

---

### Post by Cam42 on 2009-05-11
So sda1, sda2, sda3 would all be partitions of sda?
while sdb would be a different physical drive?

---

### Post by Cam42 on 2009-05-17
would the Ubuntu drive have to be the primary drive?

---

