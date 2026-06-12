---
title: "Unmounted disks spin up every 20-40 Minutes"
date: 2010-02-23
forum: Hardware
---

### Post by coolphoenix on 2010-02-23
Hello,

I've got a simple problem, first some details: I've got 5 disks in my pc, 3 are are on a raid10, 1 is having a ntfs-filesystem and 1 is only having a partition table, but no partitions (yet).

The raid10 is my karmic-installation (with lvm on the raid10 btw). the other two disks are not mounted (the one without partitions cannot be, of course, the ntfs-one is not).

So the two unmounted disks spin down after some time like they should, but what's really annoying: they spin up again after about 20-40 minutes (i didn't have a clock running yet). And they do it together at the same time! Later they spin down again after spin-down-time (which i have set up to be one minute), like they should, but then again, after some time....

What is accessing my unmounted disks in that regular interval? Any ideas? Using karmic stable.

Thanks

---

