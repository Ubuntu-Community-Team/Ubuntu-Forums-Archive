---
title: "Any &quot;How To&quot; on XFS file system?"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by joplass on 2009-03-23
I want to have and external drive based on XFS file system. Is there a "how to" somewhere?  Is it possible?

---

### Post by cariboo on 2009-03-23
All you have to do is format the disk to an xfs file system:

```
mke.xfs /dev/sda1
```

substitute your device label for /dev/sda1

Jim

---

### Post by joplass on 2009-03-24
> **cariboo907 said:**
> All you have to do is format the disk to an xfs file system:

```
mke.xfs /dev/sda1
```

substitute your device label for /dev/sda1

Jim

thanks for your help.

---

