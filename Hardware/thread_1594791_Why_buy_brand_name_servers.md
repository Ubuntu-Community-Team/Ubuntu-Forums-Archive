---
title: "Why buy brand name servers"
date: 2010-10-12
forum: Hardware
---

### Post by epsolon77 on 2010-10-12
I'm setting up a virtual environment at my office, and as I'm quoting out HP and Dell servers like always, I started to think, why, if I no longer need to worry about things like individual hardware failures as much, do I need to pay the premium for a name brand server?  So I thought I'd ask yall.  So what do you think?

---

### Post by CharlesA on 2010-10-12
Warranty and support. If you build one yourself, you have to deal with the manufactuer if anything fails.

---

### Post by epsolon77 on 2010-10-12
But if my virtual OS is still running if a server falls, do I care?  I don't need the part tomarrow, and will the Warranty actually save me any money?  The manufacturer will not likely be able to support the software since it's virtualized.  Going forward more and more systems are becoming virtual, and in the next several years I don't see why a company would not move into a virtual enviorment.  So is that old saying still worth it?

---

### Post by CharlesA on 2010-10-12
If you have a bunch of machines virtualized, and the host goes down, what do you do?

That's the main downfall to running a ton of VMs on one server. If the host crashes or has a hardware failure, you are SOL until you get it fixed.

---

### Post by lisati on 2010-10-12
Having virtual servers might be fine and dandy, but you still need hardware somewhere in the picture to run them.

---

### Post by epsolon77 on 2010-10-12
I'm running a High Availability Cluster, so if one hardware machine fails the VM's go live on another server within milliseconds of the host failure.  If anyone is NOT running HA, check it out it's worth it.

---

### Post by CharlesA on 2010-10-12
If that's the case, I'm not quite sure why you are asking about hardware.

---

### Post by epsolon77 on 2010-10-14
Mostly because one of our consultants is claiming we MUST have redundant power supplies ect in each of the cluster servers.  I am curious if I'm missing something, and thought someone here would be far more intelligent than I and be able to offer a good counter point.

---

