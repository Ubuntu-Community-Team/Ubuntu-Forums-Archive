---
title: "Setting Up Triple Boot Win7/iATKOS v7/Kubuntu 9.04"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by colonel_sanderson on 2009-09-30
Hello,

I'd like to try setting up a win-mac-linux multi boot system on my laptop.  I have never set up a dual-boot or triple boot system.  I've looked around and found a few tutorials, but most of them assume I already have enough knowledge of bootloaders and the linux command line etc. Or they are very out of date.

What I will be using:

Laptop: Everex Stepnote SA2052T (80GB hard drive)

OS's:
Windows 7
iATKOS v7
Kubuntu 9.04

Here's my process so far.

First I used a utility from the Ultimate Boot CD to partition the drive as best I could.  It has an 80GB hard drive, so I partitioned it into 3 20 GB partitions for each of the OS's, leaving the remaining 20 GB for shared storage.

Then I installed Windows 7 to the first partition.  Everything went smoothly.  In disk management, the partitions all showed correctly.

Next I went to install Kubuntu, but it didn't recognize that there was a partition table on the drive at all, so I aborted that.

I then booted up iATKOS, it also didn't see any partition table.  I decided to go ahead with the installation.  Using the iATKOS Disk Utility, I partitioned the drive out again in the same way, except I put Mac OS on the first partition this time.  Installation went smoothly.  However, upon trying to boot into Mac OS, it would show the Apple logo and the little Apple version of the hourglass, and just hang there.

So I decided to go ahead and install Kubuntu.  I set up the FAT32 partition I had set aside for Kubuntu and installed.  Kubuntu starts up perfectly well, but the GRUB bootloader only shows Kubuntu, no Mac OS.


I'd like the end result of this experiment to be a collaborative tutorial.  If anyone has any advice or can point me towards a helpful tut, I'll let you know my results.

---

### Post by bjornolai on 2009-10-17
.

---

