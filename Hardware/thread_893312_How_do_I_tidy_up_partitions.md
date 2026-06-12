---
title: "How do I tidy up partitions"
date: 2008-08-18
forum: Hardware
---

### Post by gleble on 2008-08-18
Hi
  Forreasons that I won't go in to I have three installations of Hardy. How do I reduce this to one and tidy up my disk. See screenshot attached

---

### Post by spacedoggy on 2008-08-18
the short answer is, it doesn't matter.

in the old days of hard disks there was a performance bias towards the start of the hard disk because the sectors on the outer tracks would be read faster than those in the centre track. but these days hard drive makers use the space on the disks surface to it's most efficient and increase speed as the head approached the centre. as well as cram more and more bits into each square mm of the platters.

it's not like defragmentation is required on your partition space, the only problem here is cosmetic, and in my experience if it aint' broke don't fix it.

I guess you could resize your partitions to occupy the space preceding it, and then resize again to restore it to original size from the right hand side, then repeating for each partition, if you really needed to do this, but it would be a time consuming, dangerous (unnecessarily messing with partitions is always risky) and redundant. 

if you're board enough to be caring about tidy partition tables perhaps you'd be better off finding cool stuff to apt-get and play with.

---

### Post by finito on 2008-08-18
well for starts which partition is active, 

Delete all unwanted partitions Leave one swap. 
and then resize the one that is active.

---

