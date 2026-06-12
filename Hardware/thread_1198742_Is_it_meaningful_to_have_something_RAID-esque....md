---
title: "Is it meaningful to have something RAID-esque..."
date: 2009-06-27
forum: Hardware
---

### Post by clanmackay on 2009-06-27
... between multiple disks of differing sizes?

Like many people, I accumulate old and spare disks, and seeing a stack of eight or ten of them next to my desk, I thought it would be useful to actually use some of the capacity, which totals more than two TB.

They are all 3.5" IDE drives, but have about a factor of three size difference between the smallest and largest.  Is there a meaningful and useful way to string them together, redundantly, and have access to some % of their combined storage capacities?  It doesn't seem like it would be reliable to set up three partitions on the largest drive, because a physical disk failure would wipe out three partitions, and thereby (probably) all the data.  I can imagine writing a system that would be tolerant of failures of *n* partitions, and just make sure that n is greater than or equal to the max number of partitions on any drive -- but I really have no idea what I'm talking about.

Also, what's the best way to do this, physically?  Are there relatively cheap boxes with controllers for (say) 10 drives, that attaches by USB/FireWire or something?  And is the useful lesson at the end of all of this "save your money and just buy two 1TB drives?"

Thanks.

---

### Post by cariboo on 2009-06-27
You can probably pick up a ide raid card cheaply on ebay, and run them in jbod (just a bunch of disks) mode, and use something like lvm to make them all look like one large disk.

---

