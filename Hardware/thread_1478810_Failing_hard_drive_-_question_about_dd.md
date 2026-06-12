---
title: "Failing hard drive - question about dd"
date: 2010-05-10
forum: Hardware
---

### Post by TheSqueak on 2010-05-10
It appears that the drive on which my /, /boot and /home filesystems reside is failing - my system keeps locking up and the console filling with error messages about it.

I have enough space on other drives in the system to move all the stuff off, but before I do so, I just want to clarify something

If I were to simply run dd if=/dev/sdb of=/dev/sdc (after booting from a liveCD, obviously), will it copy the partition table as well, or do I need to copy each partition separately?

---

### Post by prshah on 2010-05-10
> **TheSqueak said:**
> 
If I were to simply run dd if=/dev/sdb of=/dev/sdc (after booting from a liveCD, obviously), will it copy the partition table as well, or do I need to copy each partition separately?

It will copy everything, including the partition tables, the partitions themselves, all the data they contain and information about the bad blocks (bad sectors).

You should run an fsck -c on the new drive when the dd copy finishes, otherwise you are likely to have good blocks marked as bad.

Note that dd may not successfully finish it's copy if the old drive is in very bad shape.

If you are relying on Palimpset telling you that there's bad sectors on your drive, be aware that there is a bug in Palimpset that reports a "failing drive" when actually it's nothing of the sort.

---

