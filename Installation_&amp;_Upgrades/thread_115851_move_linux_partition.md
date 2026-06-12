---
title: "move linux partition"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by willhurt on 2006-01-11
hi,
i have two unallocated areas on my hdd an 8gb and a 17gb, with the linux partition sitting in between them, is it possible to move the linux partition without hurting it so i can join the 8gb and 17gb thus guving me one partition of 25gb, i have partition magic which runs in windows.

thanks will

---

### Post by hillbilly on 2006-01-11
hmm...i dont think you will be able to do this without loss of data. One thing you could do is first merge two contiguous partitions A and B(they both must be of the same file system), where B is a partition with data and A an empty partition. Then again split this partition into two. See how this looks like !! If after this split you get two contiguos free spaces(8gb and 17gb), then you can merge them using partition magic or qtparted. And remember, both the partitions must have the same filesystem, so that they can be merged.

But I dont think it is possible to get them two non-contiguos partitions together. Hmm...maybe if you defrag after joining A and B it might be possible. But I dont know how to do this. sorry about that.

---

