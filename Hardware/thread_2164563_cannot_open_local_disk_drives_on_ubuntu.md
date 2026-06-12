---
title: "cannot open local disk drives on ubuntu"
date: 2013-07-31
forum: Hardware
---

### Post by aditya2 on 2013-07-31
i had windows 8 on my computer recently ihad installed ubuntu 13.04 on my computer in a partition it works perfectly but i cannot open local disk drives on ubuntu how to solve this:lolflag:

---

### Post by TheFu on 2013-08-01
Need facts first.
What sort of local disks can't you open? SATA, IDE, Flash, SSD?
What sort of partitions do these disks have?
Is there any encryption involved?
Did you select to install LVM during the Ubuntu install?

To get started, connect all the disks you have having issues with accessing and please run:
**$ sudo parted -l**
and post the results. This just gathers data about the connected storage media.  Check the parted man page, to see if I'm lying.

---

