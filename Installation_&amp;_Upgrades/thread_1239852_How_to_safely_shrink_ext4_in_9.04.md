---
title: "How to safely shrink ext4 in 9.04?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by exsecant on 2009-08-14
The release notes for 9.04 said that a bug would cause possible data loss when resizing ext4 partitions in a certain way...

Is there a verified way to shrink an ext4 partition safely?

Help much appreciated.

---

### Post by exsecant on 2009-08-14
On second look the release notes say that the bug occurs when resizing "offline"... is there a way to resize it "online" that doesn't trigger this bug?

---

### Post by Mark Phelps on 2009-08-14
> **exsecant said:**
> On second look the release notes say that the bug occurs when resizing "offline"... is there a way to resize it "online" that doesn't trigger this bug?

If "online" means while the partition is mounted, then no -- partition mods can only be done while they're unmounted, essentially, "offline".

---

### Post by exsecant on 2009-08-18
I see :(

So has the bug that causes data corruption been fixed?

---

