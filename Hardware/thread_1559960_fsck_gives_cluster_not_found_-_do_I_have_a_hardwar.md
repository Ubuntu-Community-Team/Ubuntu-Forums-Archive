---
title: "fsck gives cluster not found - do I have a hardware problem"
date: 2010-08-24
forum: Hardware
---

### Post by hughcharlesparker on 2010-08-24
Hi.  Fsck.vfat says I have lots of "cluster not found" errors all over my USB external hard disk.  It spent a lot of time plugged into a computer that I think might have problems, so I'm not sure whether the external hard disk has a hardware problem, or whether it's just that the data on it is screwed.  Can anyone advise me?

Thanks.

---

### Post by dabl on 2010-08-24
FAT is not the worlds most rugged filesystem -- probably you don't have a hardware problem, but you may well have a corrupt filesystem problem.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Good luck.  I'd save whatever data you can retrieve off it, then repartition it and make an ext3 or ext4 filesystem on it (unless you have to have it for Windows, in which case you can settle for NTFS).

---

### Post by hughcharlesparker on 2010-08-24
OK, thanks.  I plan to use it to move data around, so it'll be another VFAT, but once the data's off it I'll format it and see how I go.

---

