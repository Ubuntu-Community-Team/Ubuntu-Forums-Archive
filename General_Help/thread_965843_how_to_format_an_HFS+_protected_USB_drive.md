---
title: "how to format an HFS+ protected USB drive?"
date: 2008-10-31
forum: General Help
---

### Post by Keen101 on 2008-10-31
my friend brought a broken flash drive to me the other day. It had been previously used on a mac. It still functions, but somehow is messed up. 

I went to reformat to fat32 or fat16 in gparted, but it failed. IT say's it is a HFS+ protected partition. I didn't even know there was such a thing. How do we go about repartitioning it. I am hoping for a way to fix it without a mac. Particular hoping it will be easy in Linux. 

If the only way is to fix it from a mac, how would we go about doing that?

---

### Post by dcstar on 2008-10-31
> **Keen101 said:**
> my friend brought a broken flash drive to me the other day. It had been previously used on a mac. It still functions, but somehow is messed up. 

I went to reformat to fat32 or fat16 in gparted, but it failed. IT say's it is a HFS+ protected partition. I didn't even know there was such a thing. How do we go about repartitioning it. I am hoping for a way to fix it without a mac. Particular hoping it will be easy in Linux. 

If the only way is to fix it from a mac, how would we go about doing that?

To work on any partition in gparted you must first unmount the partition (right-click it). If the partition is inside an extended partition, you may have to unmount any other partitions inside the extended partition.

You may be able to then delete the partition.

---

