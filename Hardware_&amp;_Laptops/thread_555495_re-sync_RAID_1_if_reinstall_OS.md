---
title: "re-sync RAID 1 if reinstall OS?"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by vinboy on 2007-09-20
hi
My question is:  if I reinstall my OS, do I have to re-sync my RAID 1 hard drives?
Or is there a way to create the RAID 1 without having to sync?

I use mdadm.

thanks in advance

---

### Post by MrHippocampus on 2007-09-20
As long as the livecd detects the raid and you reinstall onto the raid device node e.g. /dev/md0 (rather than e.g. /dev/sda) then you shouldn't have to.

---

