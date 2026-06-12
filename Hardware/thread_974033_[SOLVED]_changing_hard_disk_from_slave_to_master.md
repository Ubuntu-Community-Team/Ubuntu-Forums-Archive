---
title: "[SOLVED] changing hard disk from slave to master"
date: 2008-11-07
forum: Hardware
---

### Post by sandy8925 on 2008-11-07
Hi,

I have two 40 GB hard disks.
One is my primary master and the other one is my primary slave.

I have Windows XP and Ubuntu(Hardy) installed on the master disk.

I'm planning to clean install Intrepid on the slave disk and I was wondering if the hard disks would be slower than normal since they are master and slave and are connected to the motherboard through the same cable.

Would the hard disks be faster if I connected the slave as secondary master?

Also will the drive label change i.e from sdb to sca or something like that ?

---

### Post by logos34 on 2008-11-07
> **sandy8925 said:**
> Would the hard disks be faster if I connected the slave as secondary master?

Yes.  That is to say, data transfers (copy/move files) BETWEEN disks will be faster. It's always a good idea to put two hard disks on separate IDE channnels if possible

>  Also will the drive label change i.e from sdb to sca or something like that ?Yes.  It should go from /dev/sdb to '/dev/sdc'

---

