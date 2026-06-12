---
title: "consequences of gparted force quit?"
date: 2008-09-22
forum: General Help
---

### Post by kolibri on 2008-09-22
I have a damaged 3 partition disk.

I started trying to check and repair my 100 GB ext3 partition using gparted.  It has been running for 8 hours. 

The completed operations indicator bar shows no progression.  Under details, "check and repair filesystem (ext3) row has a set of gears next to it.  Subheading calibrate underneath it has a green check mark and 00:00 next to it.  The next sub heading "check filesystem for errors and (if possible) fix them" has a set of gears next to it.

Is it possible to tell if it's hung up or working?  How long should it take to run a 100 GB partition on which only 30 GB are used?

If it's hung up, what would be the hazards of forcing a quit?  Would there be any consequences for the other partitions?

Thanks

---

### Post by pieoncar on 2008-09-23
Try running top in a console (or htop if you have it).  You can use the < > keys to change which column is used for sorting, then look for gparted.  The time column will tell you how much CPU time has been spent on that process, or the %CPU column will tell you how much processing time is currently being devoted to it.

If it's working, it *probably* won't be at 100% since it has to work some, then wait for the disk, then work some, etc.

Since ext3 is a journaled filesystem, I'm fairly sure it will handle a crash fine, as long as you are indeed only checking/repairing it.  If you are actually resizing a partition, you probably don't want to force it to quit.

---

