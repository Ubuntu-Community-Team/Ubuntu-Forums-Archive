---
title: "Cannot create swap space on EEE PC"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by shaneosullivan on 2009-08-09
I'm trying to install EeeBuntu on a Eee 1005HA netbook, as a dual boot with the Windows XP Home that it shipped with.

The computer came with four partitions,
/dev/sda1 is the main windows install
/dev/sda2 is the D: drive, which I'd like to put ubuntu on
/dev/sda3 and /dev/sda4 are small partitions I presume are used by Windows, together less than 5GB

So, I'd like to break up the 72GB sda2 into whatever Ubuntu needs, but Gparted won't let me create any new partitions.  Apparently 4 partitions is the maximum.  

I don't want to delete any partitions that Windows needs, and I don't want to install Ubuntu without swap space.

Any ideas on how to solve this?

Thanks

Shane

---

### Post by snowpine on 2009-08-09
Read up on extended and logical partitions:

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

---

