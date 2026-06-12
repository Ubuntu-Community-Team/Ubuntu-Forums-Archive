---
title: "deleting retired kernels (how?)"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2009-01-09
I just installed the latest upgrade to Hardy Heron, and am now running 2.6.24-23-generic on my 686 laptop.

Looking in /boot, I see all the earlier kernels back to 2.6.24-19.  I like to keep the predecessor kernel around for a while after every upgrade, "just in case," but there's no reason to clutter up the file system with all those older kernel packages.

What's the clean way to deinstall an obsolete kernel and all its supporting files?  What packages do I need to get rid of?

---

### Post by king_lear on 2009-01-09
Search *linux-image* in Synaptic and remove the older kernels

---

