---
title: "ASUS F3SV wont allow me to partition HD...?"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by Fittersman on 2007-07-15
for "an unknown reason" i cannot partition my hard drive... anyone got any clue what could be this "unknown reason"?

i already partitioned it once before but since then i did a full recovery to how it was when i got it.

my specs are in my sig and im trying to use the alternate 64bit ubuntu 7.04 CD

and here are the steps i took:

first off i went through the setup as normal, everything ran fine (i selected keyboard layout, where im from, etc.)

then i got to the partitioner and i selected 'manual' and then i picked the 160 GB partition that i have vista on, after that i selected the size, and then instead of 160GB i changed it to 70GB

once i did that it gave me an error, something like "this operation cannot be performed because of an unknown error"

---

### Post by merlinus on 2007-07-15
You might use vista's disk manager to create the partition for ubuntu, and then install.

-merlin

---

### Post by Fittersman on 2007-07-15
alright, im giving that a shot, seems to be working.

EDIT: its not working either, it will let me shrink it a bit, but not as much as i need to, and i know im not even getting close to overwriting any files or anything either...

---

### Post by Krischi on 2007-07-18
I read somewhere that Vista uses a newer version of NTFS. Resizing partitions with this version is apparently not yet supported by the partitioning tool.

You might have to bite the bullet and delete the Vista partition entirely (but leave the recovery partition intact). Then create a new NTFS partition of the size that you want for Vista, and then rerun the ASUS recovery DVD, and select the option of recovering just the first Windows partition. After that, you should be able to partition the free space.

---

