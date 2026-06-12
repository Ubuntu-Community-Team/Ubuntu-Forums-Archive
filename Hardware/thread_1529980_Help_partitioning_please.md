---
title: "Help partitioning please"
date: 2010-07-12
forum: Hardware
---

### Post by Phyxiis on 2010-07-12
Alright, so I want to shrink my Ubuntu 10.04 partition and expand my XP parition. I have unallocated 22GB and I am stuck on how to make it move to the XP side...

---

### Post by lindsay7 on 2010-07-13
First, make sure that you are using the Ubuntu install live cd.  Start up your computer with it and run gparted. Since your Ubuntu partition is in an extended partition you need to shrink that first.  make sure that you swap off the swap partition, Shrink the unbuntu partition and then shrink the extended partition. After this is done you can grow the windows partition into the unallocated space from the extended partition.

This a little hard to put into works, but hopefully you will get the idea.

---

