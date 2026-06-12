---
title: "Ubuntu Studio with Vista 64 bit?"
date: 2008-09-11
forum: General Help
---

### Post by mark_lar on 2008-09-11
Hey people.

I've just done a clean Vista install, and have partitioned 50GB for Ubuntu Studio, i'm on the installer at the part of setting up the partitioner. This is were i'm stuck.

I can select the 50GB partition from the partitioner, but I think I need to setup eveything manually... is there no automated way to do this?

Many thanks

Mark

---

### Post by jblackthorne on 2008-09-11
Installing as you are trying to do is no big deal.  The Ubuntu installer does automatically suggest partition changes.  Though, I admit I don't know much about automatic partitioning because I always do it manually.  Manual is quite straight forward to.  Here is what you need,

* Choose manual partition
* Leave the NTFS partition alone and don't make any changes
* Create a new primary partition of 
- type ext3
- formatted = true
- mount point /
- bootable = true
- size is +48MB
* Create a new partition of
- type swap
- mount swap
- size (all space left, should be 2MB)

That is it.  There is nothing too complicated to do there.  The rule is that your swap space should equal your ram.  Normally, 2mb is fine.  Though, if you ran say a heavy server or such, you might want more.  Also, for a very simple workstation pc like you are setting up, you only need 1 main ext3 partition.  Some people with more advanced needs create more partitions, but there is no need in this case.

Hope that gets you through this point.  Good luck!

---

