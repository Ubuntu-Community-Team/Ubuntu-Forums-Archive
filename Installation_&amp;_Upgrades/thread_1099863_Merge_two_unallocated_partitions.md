---
title: "Merge two unallocated partitions"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by shrimpy89 on 2009-03-18
Hello, 
I've happily used Intrepid (dualbooted with Vista) since October.  I got to the point where I wanted to give Ubuntu more hard drive space, so I resized my Windows partition without problems.  This left me with my Windows partition, ~10 GB of unallocated space, and my Ubuntu partition.  I decided to take the opportunity to do a fresh install of Intrepid, so now with my Vista, I have a 10 GB unallocated partition and a 45 GB unallocated partition.  GParted on the Live CD won't let me merge the two unallocated sections, and will only put Ubuntu in the first 10 GB section.  So my question is, how to do I merge these two unallocated partitions into one, for reinstalling Ubuntu?  Any help would be appreciated!

---

### Post by Mark Phelps on 2009-03-18
You can't merge unallocated space because it's -- unallocated!

You have to move existing partitions around to merge the space.

For example, lets say your space was: partition #1, unallocated #1, partition #2, unallocated #2.

To merge unallocated #1 and #2, you would move partition #2 to the left, adjacent to partition #1.  GParted will let you do that.  But be aware, that can take a LONG time -- as in HOURS.  So, be prepared for a long wait.

---

### Post by shrimpy89 on 2009-03-18
Got it! Thanks!

---

