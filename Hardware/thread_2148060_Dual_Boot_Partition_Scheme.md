---
title: "Dual Boot Partition Scheme?"
date: 2013-05-23
forum: Hardware
---

### Post by Sugiura Ayano on 2013-05-23
I've decided that I'm going to dual boot Windows 7 and Ubuntu 12.04 LTS on my desktop. Windows 7 will only be installed for gaming and gaming only; everything else will be done in Ubuntu. 

Right now, my desktop only has Windows 7 installed, but on two partitions:
[LIST]
[*]The Windows OS partition, which holds the OS and installed files. 500GB.
[*]A media partition for everything else. Files, music, anime, ect. ect. 431.45GB.
[/LIST]

I have a few questions as to how I should set up my partitions once I install Ubuntu.
[LIST]
[*]How many Ubuntu partitions should I have? I read that three would be ideal: one for the OS, one for the swap file, and one for /home. Is /home designed to only store documents?
[*]How big should the Ubuntu partition be? I'm dealing with a 1TB hard drive, and I plan on making the Windows partition around 200GB. Swap would be 8192 MB if I read properly (considering I have 4GB of RAM installed) The media partition should hold at LEAST 350 GB to accommodate my anime and music. I read around that 100 GB should be more than sufficient, but I'm not sure if that would be limiting.
[*]Would I be able to access all the partitions from Windows if need be?
[/LIST]

Thanks for helping out. I really appreciate it. ^^

---

### Post by Megaptera on 2013-05-24
In no particular order:
Swap - with 4gb RAM your 'swap' is very generous but is as per recommended proportions. I run with no problems a swap of 1gb on a laptop with 2gb RAM.
/home - will have your docs, pics etc _plus_ configuration files for the Ubuntu settings.
Ubuntu will be able to access the Windows (ntfs) partitions; but Windows won't (by default) "see" the Ubuntu (ext4) partitions.

Before you start partitioning and installing - make a backup to external media of all your important docs, pics, tunes etc etc .... just in case!

---

### Post by Mark Phelps on 2013-05-24
BEFORE you do anything else, you should read through the material below about dual-booting with Win7:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

