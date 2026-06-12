---
title: "Need GParted Help Urgently!"
date: 2009-03-27
forum: Hardware
---

### Post by DizzyTech on 2009-03-27
Okay, my partition setup today was as follows:

250 GB hard drive - 232.88 "usable"
Partition 1: 192.88 GB NTFS, label "Windows"
Partition 2: 40.00 GB NTFS, label "Vista"

I had all my files on the first partition, until I moved all of them today to my second partition. I started up the Hardy LiveCD I had, and then started GParted.

I deleted the first (192.88GB) partition, and hit apply. I then told GParted to move the second partition to the front, and hit apply.

It didn't get far. After moving the first 32 MB, the system *crashed*.

Here's where I am now. Apparently, GParted made all the changes to the partition table already:

Partition 1: 40.00 GB NTFS (label name "Windows", according to Hardy LiveCD)
Partition 2: 192.88 GB unallocated (according to GParted)

Please, help! How do I get my files (on the second partition) back? Can anybody help me craft a DD command to get those 32 MB back where they belong?

---

