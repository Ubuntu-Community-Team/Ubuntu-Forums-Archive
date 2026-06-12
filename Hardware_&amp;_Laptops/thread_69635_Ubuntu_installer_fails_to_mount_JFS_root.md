---
title: "Ubuntu installer fails to mount JFS root"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by jute on 2005-09-27
Hello everyone,

I have a big JFS partition that, when mounted, only has one directory,
/backup.  I figure I should be able to install Ubuntu on this disk, but
when I've made all the choices (JFS, no format, mount as /, defaults,
bootable) the installer fails to mount that partition (/dev/hda1).  
I can see that the installer loads the jfs-modules earlier, however.

Anbody succeeded in a similar setup?  Re-formatting this partition is out of the question, as you 
may deduce from its contents, and I don't have a spare HDD to install
on.  I've been using the machine/disk with live CDs for a while after
the original root drive failed (and with the lives the partition mounts
just fine), but eventually that grows a bit old.

-- 
jussi

---

### Post by jute on 2005-09-27
Of course I had to forget -- I'm trying with the 5.10 preview.

-- 
jussi

---

