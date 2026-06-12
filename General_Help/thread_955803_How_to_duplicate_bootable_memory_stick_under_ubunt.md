---
title: "How to duplicate bootable memory stick under ubuntu?"
date: 2008-10-22
forum: General Help
---

### Post by sigwise on 2008-10-22
I have a bootable memory stick, how can I make exact copy of it to another memory stick?
Any suggestion will be appreciated.

---

### Post by C.S.Cameron on 2008-10-22
You can clone the flash drive using:

dd if=/dev/hda of=/dev/hdb

Check Krupski here for dd:
[http://ubuntuforums.org/showthread.p...69#post5983469](http://ubuntuforums.org/showthread.p...69#post5983469)

---

### Post by sigwise on 2008-10-22
> **C.S.Cameron said:**
> You can clone the flash drive using:

dd if=/dev/hda of=/dev/hdb

Check Krupski here for dd:
[http://ubuntuforums.org/showthread.p...69#post5983469](http://ubuntuforums.org/showthread.p...69#post5983469)

Thanks, I have another question, the source disk is 1GB, the target disk is 2 GB, after I run dd, will the target be partitioned to 1GB?

---

### Post by C.S.Cameron on 2008-10-22
Partitions end up being the same size.
Partition size on your new stick can be expanded using gparted.
You just don't want to try going from a larger disk to smaller.

---

