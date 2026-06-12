---
title: "raid 5/6 setup"
date: 2014-06-11
forum: Hardware
---

### Post by mattdawolf on 2014-06-11
What would be the best sub-$100 card option for setting up a RAID array with two 2TB disks and that doesn't use the silicon image chipset?

---

### Post by Lars Noodén on 2014-06-12
With only two disks, your option is RAID 1, mirroring.  RAID 5 needs at least three disks and RAID 6 needs at least four disks.  Software RAID with mdadm might be just fine.  I'm not sure of the status of ZFS on Ubuntu but it might be worth looking into as an alternative.

---

### Post by lukeiamyourfather on 2014-06-25
ZFS or md would do the trick and would be more reliable than a cheap fake RAID controller. For just a mirror md would be much easier, you can even do it during the install. While ZFS can be used for the root file system it's a little more complicated and better suited for non-root storage (at least on Linux).

---

