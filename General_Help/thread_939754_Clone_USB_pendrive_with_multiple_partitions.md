---
title: "Clone USB pendrive with multiple partitions"
date: 2008-10-06
forum: General Help
---

### Post by estratos on 2008-10-06
Hi,

I have an USB pendrive containing two partitions that I want to backup into a single image file. dd gives me the possibility of storing single partitions into an image file but then, I have to manually restore every partition from its associated image.

Is there an utility that I could use for creating a single backup image from different partitions and later restoring the system into a new pendrive without having to create the partitions first?

The initial backup process doesn't bother me. I just want to clone the original pendrive on several blank USB pendrives without partitioning them first.

Thanks in advance,

Daniel.

---

### Post by C.S.Cameron on 2008-10-06
This worked for me, I have 4 partitions, Fat32, Home, Root and Swap.
Booted computer using primary pendrive, (sdb).
(can also boot from HDD or Live CD).
Inserted pendrive to clone o/s from, (sdc).
Inserted pendrive to clone o/s to, (sdd).
In terminal ran:
sudo dd if=/dev/sdc of=/dev/sdd
After operation completed, rebooted with sdd.
So far everything looks identical to sdc.
Although identical make and model sdd has a few more megs than sdc thus a bit of unallocated space at the end.

---

### Post by estratos on 2008-10-07
That worked for me too! I didn't know that dd was so smart!

Thank you very much.

Daniel.

---

### Post by RMOP on 2010-06-28
Old post, I realize, but glad to have found it. This was ***very helpful***! I moved from a full 4Gb card to an 8Gb. The unused space on the target card was readily incorporated by resizing the new partition w gparted. Nice. Thanks.

---

### Post by C.S.Cameron on 2010-06-28
My dual boot laptop hard drive started to fail one day in the Sri Lankan jungle. I managed to clone the drive to a spare I had in an external enclosure. I then stuck this into the laptop and it was like nothing had happened.

---

