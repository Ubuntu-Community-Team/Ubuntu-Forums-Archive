---
title: "Mounting NTFS Partition"
date: 2008-10-10
forum: General Help
---

### Post by Lord_Takkera on 2008-10-10
Before the latest updates, I had my windows partition able to mount, and I even had it auto-mounting with NTFS-config. However, now it doesn't auto-mount, and when I try to manually mount it, it says I don't have the privlidges to do so. I am the only user on the OS. Any ideas what changed.

Oh yeah, I'm runnning 8.10

-Lord_Takkera

---

### Post by SuperSonic4 on 2008-10-10
You need to be root to mount files

```
gksudo nautilus
``` will launch nautilus as root and then you should be able to mount by right clicking the drive and selecting mount

---

### Post by bodhi.zazen on 2008-10-10
You can try re-running ntfs-config or edit the appropriate line in fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

