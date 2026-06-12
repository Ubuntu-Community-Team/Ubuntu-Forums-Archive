---
title: "Dell Partitioning/Install Questions"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by themusicwave on 2006-08-03
I just got a Dell Inspiron e1505 yesterday and I want to dual boot it with XP pro and Ubuntu.

When I viewed the default partition setup through XP home(came with it), I noticed it has 4 partitions by default.

There are the following partitions: 
37mb FAT  - no idea what this is for
2.3 GB FAT32 - No idea what this is for either
66.6 GB NTFS - This is the partition for the user to install everything
27.3 GB NTFS - This is the backup partition for Dell restores.

I have been searching everywhere and can not figure out what the 2 smaller partitions are for, does anyone know?  I have suspiscion that one of them enables the capability to play dvds without booting the system.  By the way these 2 partitions don't show up in XP as usable drives, only the large partitions do.

I want to repartition the drive install XP and Ubuntu w/ GRUB.  I'd also like to not screw up any of my extra features(like no boot DVDs).

Does anyone know how I should partition the drive or have any resources that would help?  Any tips would be awesome.

---

### Post by yukito on 2006-08-03
Well, those partitions are often used for the recovery tools that come with laptops these days. I have a 7.5GB partition on my sony vaio that is used for recovery tools. If the install/recovery partition is one of the others, it might be the partition containing software to run your no boot DVD thingie. If the partitions don't show up in windows, its best not to touch them from a linux installer or you might destroy your legal version of the windows install media or damage your extra features. Not sure though.

---

### Post by themusicwave on 2006-08-04
I think I am just going to go for it.  I'm going to just leave the 2 small partitions alone and create new partitions for Ubuntu, Xp and Data.  I'll post the results of this attempt in case anyone has this question in the future.

---

