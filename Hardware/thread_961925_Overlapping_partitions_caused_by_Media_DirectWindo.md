---
title: "Overlapping partitions caused by Media Direct/Windows recovery. Can't install Ubuntu"
date: 2008-10-28
forum: Hardware
---

### Post by kkkkdddd on 2008-10-28
In August I bought DELL XPS 1530M laptop with 160GB hard drive, windows vista and Media Direct 3. Then, without reading anything, I started playing with it. 
While trying to install Ubuntu, I messed up my hard drive and I need help.

What I did:
-I ran windows to see whether it was working(it was)
-I inserted Ubuntu 8.04 CD and restarted computer
-I ran GParted from Live CD and I was very surprised with what I saw. My hard drive(160GB) had small partition(about 150MB), then there was windows partition, then recovery partition(10GB, 5.5 free) and media direct partition at the end(2.5 GB). Some small parts of the hard drive were unallocated. I thought "what an idiot made it like that" and I started repartitioning. I made space for ubuntu, shrinked recovery partition to reclaim space and finally added unallocated space to partitions
-GParted finished successfully after 8 hours. I was to tired to install Ubuntu, so I just turned off the computer
-Next day before turning on the computer I spotted that there was one button more near the power button and I pressed it. Some windows started booting but it ended up with blue screen. Now I know that this was windows from media direct.
-I restated computer but my windows vista failed to start. It said that it encountered unexpected error and it has to repair it. After one hour of "repairing" there was no progress.
-I took windows instantiation cd and I ran system recovery from it. It said that it founded and repaired an error in MBR.
-I restarted and this time windows vista from my hard drive booted successfully
-During next 2 months I was quite busy and I had no time to install Ubuntu, so I was working on windows
-I thought that it is a high time to install Ubuntu. I inserted Ubuntu 8.04 cd to drive and ran installer, but installer could not see any of my partitions! I started GParted but there were no partition at all.

I can' t even say who was the culprit. It may me be GParted, MD or windows recovery.

Current state:
-fdisk sees partitions but it says,
"Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 5."
-GParted prints to console:
"Unable to open /dev/scd0 - unrecognised disk label.
Can't have overlapping partitions."
In GUI I can only choose "new".
-Windows works. It sees three partitions: its partition, recovery partition and MD partition. Hibernation does not work(resuming end up in system hung), but it seemed to work before playing with partitions.

Now I would like to have dual boot system with windows and Ubuntu(with grub). I do not need MD at all.
I know that the easiest solution is to format whole drive and install everything from scratch, but I do not want to lose my windows partition.
 
Do you know how to solve the problem of overlapping partitions?

I attach screenshot of gparted and two screenshots from windows.
Below output of fdisk and gparted.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    7  HPFS/NTFS
/dev/sda2              17         600     4687500    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        7612       18952    91096582+   7  HPFS/NTFS
/dev/sda4           19131       19458     2620416+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown

Partition table entries are not in disk order

```

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): v
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 5.
115772808 unallocated sectors

```

```

ubuntu@ubuntu:~$ sudo gparted
 ======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Can't have overlapping partitions.

```

---

### Post by caljohnsmith on 2008-10-28
Probably "testdisk" will be able to correct your partition table problems. First I would recommend backing up your important files in Vista, and then from the Ubuntu Live CD, enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partitions. :)

---

### Post by kkkkdddd on 2008-10-29
Thank you.
I used testdisk.
It helped me with overlapping partitions.
But then GParted said that one of my partitions exceed disc. 
So I deleted MD partition and now GParted seems to see my partitions properly.
I think that I will wait for Ubuntu 8.10 and if something still wasn't working, I will write.
One again, thanks. :)

---

### Post by caljohnsmith on 2008-10-30
Glad you were able to sort out the partition problem. Cheers and have fun. :)

---

