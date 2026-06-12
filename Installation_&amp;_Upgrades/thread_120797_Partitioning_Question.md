---
title: "Partitioning Question"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by OlineSixtyOne on 2006-01-23
I don't know how to do LVM, and it's unlikely that I will get any new hard drives for this computer. If it will work on the extended partition, thats what I will do. Thanks for the help everyone.

---

### Post by OlineSixtyOne on 2006-01-23
Well I've run out of primary partitions on my hard drive (you only get 4 :(). I was considering reinstalling Ubuntu with the following parition arrangement:
10GB mounted as /
45GB mounted as /home/
1GB swap
and put all three of those on 1 extended partition.
Would it be a problem to put all of those on an extended partition? Would they still use a familiar naming scheme like /dev/sda2...3...4?
Is there a chance this partitioning setup would be unstable? I've never used extended partitions, so I don't know much about 'em.

---

### Post by az on 2006-01-23
Extende partition just work like any other partitions.

You get a name for the exteded partition and for every partitoin within it.

---

### Post by emptor on 2006-01-23
Why don't you consider using LVM? That way you can manage all those as logical volumes and even add disks to a certain volume as your needs change?

---

### Post by raghav_p on 2006-01-23
You should be fine. I currently have 2 installations of Ubuntu on my hard drive. One is completely restricted to an extended partition and the other is using primary partitions in / and /home and /swap. I have had no trouble partition wise.

---

