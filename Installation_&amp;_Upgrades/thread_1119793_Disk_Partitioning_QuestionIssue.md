---
title: "Disk Partitioning Question/Issue"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by TheHarbinger on 2009-04-08
Hello to all.

I'm attempting to make a triple-boot system on my PC, with OS X (Hackintosh), XP, and Ubuntu.  I figured out that I needed to install OSX first, so I've done so and used its Disk Utility to create two partitions.  This allowed me to make a GPT, or GUID, partition for the OS and a second partition that I would use gparted to further divide for the other OSes. The plan, after creating partitions for the three OSes, was to have a large NTFS partition for XP's use and a 5GB Linux swap partition at the end of the drive.

I discovered that OSX actually created three partitions--one was an EFI partition (set as primary, boot, FAT32), the second was a GUID partition (set as primary, type af, HFS+), and the third was set up by default as an HFS+ partition. When I went into gparted I was able to blow away the third, HFS+ partition and subdivide it for Linux and XP. However, I ran into another problem--I'm only allowed four primary partitions and the rest must be extended. WIth EFI, OSX, XP, and Linux, all my primaries are used up. I could create an extended partition for XP's use, but could not create a 5GB partition at the end of the disk for Linux swap.

Could the remaining drive space be allocated as an extended partition, and the Linux swap be assigned as a drive in that partition? Could I simply create a swapfile in the Linux partition?  What would be the best way to proceed?

---

### Post by SnickerSnack on 2009-04-08
Your linux partition can be an extended partition with two logical partitions in it: linux, swap.  Then you have:
* EFI primary
* OSX primary
* XP primary
* Extended
*** Linux logical
*** swap logical

XP must be on a primary partition, but I don't know if the same is true of OSX.

---

