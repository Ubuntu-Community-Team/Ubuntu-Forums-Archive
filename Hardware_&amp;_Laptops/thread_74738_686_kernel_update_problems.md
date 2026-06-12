---
title: "686 kernel update problems"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by RyanGT on 2005-10-12
I installed ubuntu over the last couple days and am fairly happy with it.  I have a Compaq Presario 2500 laptop with a Pentium 4 and right now I am running the 2.6.10-5-386 kernel.  I used the synaptic gui to install the 2.6.10-5-686 kernel and when it booted my ath0 pci card was no longer listed in the network config gui.  I also tried the 2.6.11-1 kernels (386 and 686), but the system locks up as X is starting.  What can I do to trouble shoot this?  I would really like to run a 686 kernel and preferably a newer one.

Thanks,

Ryan

---

### Post by RyanGT on 2005-10-12
Installing the linux-686 package allowed me to use the 2.6.10-5-686 kernel and have my wireless card continue working correctly.  Is this a dependency that Synaptics Package Manager should have caught?

I still can't use the 2.6.11 kernels.  The system locks while X is starting.

Ryan

---

