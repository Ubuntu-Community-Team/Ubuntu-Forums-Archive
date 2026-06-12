---
title: "mdadm array shrink disks"
date: 2017-11-02
forum: Hardware
---

### Post by shoeleshunter78 on 2017-11-02
I am building a mdadm Raid5 array with three disks sized: 4TB, 5TB, and 6TB. This will only yield 8TB usable space. I am ok with the loss as I will be replacing the 5TB and 6TB soon with 2 more 4TB drives.

The question. If I fail the 5TB drive, can I replace it with a 4TB drive, or will mdadm complain?

---

### Post by steeldriver on 2017-11-02
I don't know - however I've seen it suggested as good practice to create partitions just a little bit smaller than the smallest physical disk size, and create the array from those rather than from the bare drives directly

That also gives you a bit of wiggle room if the replacement disks are not exactly the same size as the originals (e.g. from a different manufacturer)

---

