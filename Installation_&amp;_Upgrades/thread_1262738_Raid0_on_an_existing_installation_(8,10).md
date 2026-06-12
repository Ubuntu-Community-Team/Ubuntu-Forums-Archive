---
title: "Raid0 on an existing installation (8,10)??"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by attila_66 on 2009-09-10
I have already installed kubuntu 8,10 on my system.
It is installed on 160gb hdd.
I have another empty 160gb hdd.
To have additional space and performance I plan to make Raid0 with these two hdd's.
Questions:

Is it possible to make this raid without any data loss?? 

(I dont want to make new install and config also updates.)

---

### Post by ronparent on 2009-09-10
Not if you don't backup before proceeding. The raid0 especially is also refered to as a stripped raid. That means alternate sectors are written to each disk in a more common two disk set. It gives you the least data security because if one disk fails you lose all the data on both. But for well backed up systems it provides the advantage of about twice the read/write speeds.

There is no way to transition between a non-raid to a raid0 on a drive without a total reformat and repartitioning. Also, not completely necessary but ideally both disk should be identical - same model, mfg, etc. This is particularly true of any hardware raid including fake raid. If only a small portion of the drive is currently used you could conceivably create a software raid0 from it using only part of each disk but that could be more trouble than it's worth.

---

