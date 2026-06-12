---
title: "Virtual Server 2005 install hangs if more than 512MB RAM"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2005-12-14
Hi,

I'm trying to install Ubuntu to a Virtual Server 2005 image.

I found that if I allocate 756, 768, or 1024MB of RAM to the computer, the boot hangs at a point where the kernel is clearing/flushing 244 bytes of memory.  If I allocate 512MB, I will get to the **boot:** screen.

Has anyone encountered this or understand why this happens?

Thanks

---

### Post by daller on 2005-12-14
Is the server capable of more than 512MB?

Are all the RAM-blocks intact?

What happens if you install it with 512MB, and then add the rest after installation?

---

### Post by kacheng on 2005-12-14
The VPC Server itself has 16GB RAM, so I would assume that the RAM blocks are intact.  I would assume 4x4GB or 8x2GB. That shouldn't matter anyways though?

I'll try increasing the RAM allocation after installation and see what happens.  Having problems with the partitioning part of the installation, though... but that's another thread.

---

