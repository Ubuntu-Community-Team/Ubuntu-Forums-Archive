---
title: "Upgraded to Hardy Heron and wont to downgrade"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by rodm1 on 2009-01-16
I upgraded to Hardy Heron (8.04.1) and immediately began having problems with full system lock ups. I reinstalled Gutsy (7.10) and problems are over know.

When I boot into grub besides showing Gutsy it all sow shows Hardy kernel 2.6.24-15, and 2.6.24-1.

How do I properly remove Hardy from my drive?

---

### Post by aheckler on 2009-01-16
Search Synaptic for "linux-image" and remove the old kernels. But be careful, removing the one you currently use would be A Bad Thing To Do.

---

### Post by rodm1 on 2009-01-17
Thanks it worked grate

---

