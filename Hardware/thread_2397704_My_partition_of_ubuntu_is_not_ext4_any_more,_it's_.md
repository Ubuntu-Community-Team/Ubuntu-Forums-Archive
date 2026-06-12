---
title: "My partition of ubuntu is not ext4 any more, it's msdos!"
date: 2018-08-02
forum: Hardware
---

### Post by bosko2004 on 2018-08-02
I see that start of partition is to low, how to change it(without unmounting because thats system partition(mouted as '/')).

---

### Post by westie457 on 2018-08-02
Hi, it is highly unlikely your Ubuntu has changed from ext4 to msdos because it very probably will not boot at all.
It is more likely you are confusing file-system formats with partition table formats.
post the terminal output of ```
sudo fdisk -l #the l is a lower-case L, not a 1 or i or I
```

Regarding your second query: You cannot change any mounted partitions, you can  only work on partitions from a Live session.

---

