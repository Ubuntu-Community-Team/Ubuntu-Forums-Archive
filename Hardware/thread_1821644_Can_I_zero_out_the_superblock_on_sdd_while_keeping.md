---
title: "Can I zero out the superblock on sdd while keeping sdd1 intact?"
date: 2011-08-09
forum: Hardware
---

### Post by tekknoir on 2011-08-09
Hello All,
    thanks for clicking on this thread.


I have a LVM raid and need to zero out the superblock on /dev/sdd, while keeping /dev/sdd1 ?

This is confusing mdadm and can't assemble the array.  *mdadm tries to build with /dev/sdd instead of /dev/sdd1.

I already tried the following which caused the array to rebuild.  
# mdadm --zero-superblock /dev/sdd

The superblock is still there after the rebuild.    Is there another way to  do it *(maybe with dd) while keeping sdd1 intact so I don't have to rebuild again?

*I have the array currently stopped.


Thanks for your help in advance.

* denotes edited for clarification.

---

