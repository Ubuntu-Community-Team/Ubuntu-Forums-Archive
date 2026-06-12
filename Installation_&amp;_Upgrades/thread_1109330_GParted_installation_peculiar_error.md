---
title: "GParted installation peculiar error"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Wolvenreign on 2009-03-28
Hello one and all of Ubuntu Forums!

I am currently trying to go from a completely Ubuntu setup to a dual boot with Windows XP home edition. I installed GParted to get started, However, a strange error occured during its installation. "E: liblexz600core0: subprocess post-installation script returned error exit status 100"

What is this error, and will it effect the dual boot in any way? Is it something you haven't seen before, perhaps?

As of the time of this writing, I have the latest updates available. It is Saturday, march 28, 5:23 PM.

Thank you for any and all responses.

---

### Post by Partyboi2 on 2009-03-28
Try using gparted from a ubuntu live cd (System>Admin>Partition Editor) instead of installing it. When working on partitions they need to be unmounted first which is the advantage of using gparted from the cd.

If you still want install gparted can you open a terminal (Applications>Accessories>Terminal) and post the whole output to
```
sudo apt-get install gparted
```

---

### Post by Wolvenreign on 2009-06-20
Ah, yes, thank you. It is sad, however, that I wasn't able to resolve this before the computer got hauled away by a custom shop.

However, I have instructed them to include a large partition of Ubuntu when the repairs are complete.

---

