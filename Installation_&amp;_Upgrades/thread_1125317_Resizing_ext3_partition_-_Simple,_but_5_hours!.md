---
title: "Resizing ext3 partition - Simple, but 5 hours?!"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Razorg on 2009-04-14
Hello, at my laptop i have all disk allocated to ubuntu. A full installation. But i decided to make it dualboot with vista, so i can play games.

So i decided to resize my ubuntu partition, and to test if it would work, i just resized to decrease my ubuntu partition size, by 2GB, no more.

The process started, and it did the fake process, and now it is doing the real one. And remaining time is 5 Hours! So how much time would it take decreasing it by 20GB, which i want to do finally? 

Does using the latest gparted edition, instead of the one from ubuntu 8.10 live cd is faster? Is there anything i can do to make it faster anyway?

---

### Post by timcredible on 2009-04-14
no, it shouldn't take that long.  if it's already started, i think that interrupting it could have really bad effects though, so i would let it run.

---

### Post by silentrebel on 2009-04-14
Changing partition size should not take long at all.  It's moving partitions that requires nearly unacceptable amounts of time (I guess it makes sense when you consider that it has to copy every block from one place on the hard drive to another location).  So if you resized a partition to make room for another and had to move one of them to make use of the freed space, that would be the cause of the delay.
If the process is taking so long because it is *moving *a partition, the size of a move will greatly affect execution time.  Note however that *distance* from the source location to the target location should not affect this.
timcredible is right: do not interrupt the process if you do not want to suffer terrible consequences...  ...especially if any moving is being accomplished.  That could result in an irreparably corrupted partition.

---

### Post by Razorg on 2009-04-14
aw ok, thank you very much! I guess i should leave it on, all night to do the 20gb transfer.

---

