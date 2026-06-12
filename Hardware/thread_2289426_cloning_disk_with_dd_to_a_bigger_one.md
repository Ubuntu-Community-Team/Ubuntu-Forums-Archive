---
title: "cloning disk with dd to a bigger one"
date: 2015-08-04
forum: Hardware
---

### Post by MikeCyber on 2015-08-04
HI
what result would I get if I clone with dd a 500GB SSD to a 2000GB SSD? In fact I need the partition 2 bigger for Windows 10.
Thanks

---

### Post by howefield on 2015-08-04
Probably a 2000GB disk with 1500GB of unallocated space.

Some more information on what exactly you are trying to do wouldn't go amiss ?

---

### Post by weatherman2 on 2015-08-04
Use Clonezilla to save yourself a lot of grief.  Or, use Gparted to copy partition to partition safely without copying all of the unused space.  dd is probably the least efficient way to copy a partition.

---

