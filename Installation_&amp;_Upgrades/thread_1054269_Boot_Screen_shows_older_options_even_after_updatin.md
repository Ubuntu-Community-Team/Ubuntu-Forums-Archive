---
title: "Boot Screen shows older options even after updating."
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-01-29
I updated from Ubuntu 8.10, kernel 2.6.27-7-generic to 2.6.27-9-generic to 2.6.27-11-generic, but i can still see the older versions as options in the boot screen. Is there any way I could remove them?

---

### Post by SqRt7744 on 2009-01-29
> **bhishan said:**
> I updated from Ubuntu 8.10, kernel 2.6.27-7-generic to 2.6.27-9-generic to 2.6.27-11-generic, but i can still see the older versions as options in the boot screen. Is there any way I could remove them?

open a termnial window and enter:
aptitude search 2.6.27-9-generic|grep 'i '

this will show the installed packages with 2.6.27-9 in the name. Remove them with:
sudo apt-get autoremove linux-image-2.6.27-7-generic linux-image-2.6.27-9-generic

You could also do with with synaptic package manager, search for the old kernels and remove them.

---

### Post by bhishan on 2009-01-29
Thanks man.

---

