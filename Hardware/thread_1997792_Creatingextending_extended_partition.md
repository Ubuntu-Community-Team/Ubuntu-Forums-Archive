---
title: "Creating/extending extended partition"
date: 2012-06-05
forum: Hardware
---

### Post by galaxion2 on 2012-06-05
Hi everyone,

I apologize if this is not the correct category to post under. I am having some trouble with partitions. I recently purchased a new laptop with four partitions on the hard drive, one of which is a logical drive. I want to install Ubuntu on a new partition, but when I try to create a new partition (Windows 7 disk management) it says that I already have the maximum number of partitions. I tried using Partition Wizard to expand the extended partition containing the logical drive and then create a new logical drive, but when I open PW (I'm using the minitool home edition) it says that I have a bad disk under file system and all the options are grayed out. I can't create. I'm not sure if this means my computer's broken (I hope not, I just got it). Is there any way I can expand the current extended partition or create a new extended partition? Thanks.

---

### Post by oldfred on 2012-06-05
Post this from gparted liveCD or Ubuntu liveCD.
```

sudo fdisk -lu
```

If you have an extended partition, you have to expand the extended partition first then you can create new logicals in the unallocated in the extended. If you just shrink Windows 7 from inside Windows that unallocated is in the primary area and you cannot then create any more primaries.

Use Windows tools to shrink the Windows 7 partition, but use gparted or Linux tools for any Linux partitions. Some tools write incorrect data in the partition table and then most partition tools stop working as partition table is corrupted.

---

