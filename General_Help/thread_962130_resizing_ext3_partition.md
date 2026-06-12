---
title: "resizing ext3 partition"
date: 2008-10-28
forum: General Help
---

### Post by stoppage on 2008-10-28
Hi, I'm currently resizing an existing ext3 partition to create an additional partition for my „home“ folder. A question....on using „Gparted“ am I guaranteed that it will only use empty space to create the partition and I won't lose data or mount points? Grateful for any assistance here

---

### Post by OneRingShort on 2008-10-28
Guaranteed?  I wouldn't use that word, as there is always a slight chance something would go wrong.  Because of this, I would always back up data before modifying partitions in any way.

I did recently do what you did, but I was increasing the size of my Windows partition (poorly planned space allocations).  From what I understand, is it moves all the data around to make empty space where it's needed, changes the partition size, and then moves the files back to the new beginning of the partition (if necessary).  Please correct me if I'm wrong.

One thing to note:  When I changed my partition size (320 g hard drive), it took about 7-8 hours to complete, so I would recommened doing it over night.

---

