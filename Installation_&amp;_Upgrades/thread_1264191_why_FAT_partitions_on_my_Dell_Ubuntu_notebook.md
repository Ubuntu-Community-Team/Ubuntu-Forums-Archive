---
title: "why FAT partitions on my Dell Ubuntu notebook"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by noanker on 2009-09-11
I have a Dell 1420 notebook with Ubuntu 7.10 installed. There is one 80M primary FAT 16 partition and one 2,155M primary FAT 32 partition. There is also a 206M primary ext3 boot partition, as well as a 158G primary extended partition containing several logical partitions for Ubuntu. My question is, what are the FAT partitions for (I assume something to do with Dell) and are they important. Can they be deleted and the entire HD be devoted to Ubuntu stuff.

---

### Post by StuartN on 2009-09-11
The two FAT partitions are about the right size for Dell diagnostics and system restore. They probably don't even feature as options in GRUB (see [http://www.ehow.com/how_2184092_perform-dell-system-restore.html](http://www.ehow.com/how_2184092_perform-dell-system-restore.html)) and probably don't have any functions that a decent Linux CD lacks. If so then you could delete them. There is probably a DSR.EXE file in the little one and Windows stuff in the bigger one.

---

### Post by TBerk on 2009-09-12
> **StuartN said:**
> The two FAT partitions are about the right size for Dell diagnostics and system restore. They probably don't even feature as options in GRUB (see [http://www.ehow.com/how_2184092_perform-dell-system-restore.html](http://www.ehow.com/how_2184092_perform-dell-system-restore.html)) and probably don't have any functions that a decent Linux CD lacks. If so then you could delete them. There is probably a DSR.EXE file in the little one and Windows stuff in the bigger one.

I'd agree with most of that BUT-

If your system didn't come with a Windows Installer CD **and** if you delete the partitions (that we are assuming are Restore/Install locations for Win_x) then you have burned a bridge so to speak.

So, think it through before you delete them.


berk

---

### Post by bumanie on 2009-09-12
I imaged the restore partitions, placed them on external media and then deleted them off the hard drive, that I can restore them if necessary.

---

### Post by rob-ward on 2009-09-12
If you have a decent backup image of them partitions and are able to recover them if you ever decided that you needed to then there is no reason that you can't destroy the partitions and use the entirety of your drive for ubuntu.

---

