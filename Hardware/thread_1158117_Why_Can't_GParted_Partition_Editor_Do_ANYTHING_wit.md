---
title: "Why Can't GParted Partition Editor Do ANYTHING with my USB Stick? What to do instead?"
date: 2009-05-13
forum: Hardware
---

### Post by OzzyFrank on 2009-05-13
OK, so I fire up GParted to wipe and reformat my USB stick, and while it tells me it can delete the current partition/filesystem, it can't create a new one. And the funny thing is, while it assures me the space is unallocated and without a filesystem, I can amazingly enough play videos that are still on there, hehe! I can unmount and remount and everything is still there, but restart GParted and according to it, there is an unknown filesystem now.

I can assure you that the filesystem is intact, and like I said, I can access files still there, and that it is indeed a filesystem GParted knows (NTFS). But try to format it (back to Fat32, if it makes a difference) and it fails, with the erorr:

[B]mkdosfs: unable to open /dev/sdc1
[/B]
I can mount and unmount, read and write, and can format it in Windows, so what gives? Is there another option for me in Ubuntu? I've found GParted to be a great tool, so am perplexed as to how it could fail so dismally on a mere USB stick, which can be easily unmounted, etc. Cheers.

EDIT: I just figured out I could at least reformat via the terminal with [COLOR="Purple"]**sudo mkfs.vfat /dev/sdc1**[/COLOR], but I'd still like to figure out why GParted can't do it.

---

### Post by coffeecat on 2009-05-13
Sounds like something funny with the partition table. Try this in Gparted. Make sure you have the USB stick selected. You don't want to do this on any other drive by mistake. :| Go to Device > Create Partition Table and create an msdos partition table. This will, of course, zap any partitions and data you have on there. Now try to create your partition(s).

---

### Post by OzzyFrank on 2009-05-17
Well, all is OK since I wiped it via the terminal with that command I outlined. But I must say I doubt anything was wrong with the partition table, as EVERYTHING could access it, read/write, give me accurate info about the filesystem etc... all but GParted. The only thing I can think of is that GParted indeed has problems with USB devices being formatted as NTFS, though I would assume this not to be the case (especially since these days GParted is my partitioner of choice). So of course I can't rule out it was a corrupted partition table, but from past experience I would have expected to see more sign of it outside of GParted.

---

### Post by coffeecat on 2009-05-18
> **OzzyFrank said:**
> But I must say I doubt anything was wrong with the partition table, as EVERYTHING could access it, read/write, give me accurate info about the filesystem etc... all but GParted.

Maybe. But with an admittedly earlier version of Gparted I did once have a very weird experience with the hard drive on a laptop. I had shrunk the Windows C: partition with Acronis, and then created partitions in the unallocated space with the SuSE (version 10.0 iirc) installer, and Suse ran happily. When I came to install Ubuntu, its installer crashed and Gparted told me that the whole disc was unformatted - from which I was running both Windows and Suse. Hmmm. In the end I imaged everything I wanted to keep, created a new partition table with Gparted, created my partitions, restored everything, installed Ubuntu and after that Bob was my Uncle.

I can only think that somewhere between the laptop being set up in the factory, to the Suse installer making new partitions, something had happened to the partition table such that everything still seemed to work, but Gparted had difficulties.

---

