---
title: "Gparted mounting USB HDD while partitioning"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by chaosblue on 2006-07-14
I'm having a problem with gparted mounting my external USB harddrive when I try to set up a new partition.  It deletes the old ones just fine, but when I attempt to set up a new one (ext3), it tries to mount it and ends up corrupting the filesystem.  Any ideas?

---

### Post by Jedeye on 2006-07-15
did you unmount the drive before applying the changes? Partition>unmount it worked for me, but I was not curupting the partition, just crashing gparted.

---

### Post by chaosblue on 2006-07-15
> **Jedeye said:**
> did you unmount the drive before applying the changes? Partition>unmount it worked for me, but I was not curupting the partition, just crashing gparted.

Yeah, I have to keep unmounting it to delete the corrupted partitions as well.  It's kind of funny you should mention crashing... it's doing that about every five attempts.  ](*,)

---

