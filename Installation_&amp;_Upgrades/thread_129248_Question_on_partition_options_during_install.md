---
title: "Question on partition options during install"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by grep on 2006-02-13
On the manually edit partition option, what is the space reserved for super user?  Its default value is 5%.  Is it needed on every partition created?

---

### Post by lha on 2006-02-13
If a partition has less than the amount of 'reserved space' free, only super user is allowed to fill up that space. It's purpose is to keep your system in usable state (for superuser) even if hard drive becomes full.

On a 5GB root partition that 5% is reasonable, reserving 250MB for super user. On the other hand, if your root partition was 50GB, a hefty 2,5GB would be reserved! It'd be waste of space. So if you make a big root partition, you could reduce the amount of reserved space. If you decide to make a /home partition, you can set the reserved space to 0% as super user doesn't need to have free space on /home.

---

