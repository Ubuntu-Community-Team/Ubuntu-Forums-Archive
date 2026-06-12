---
title: "USB Drive Cache reaching 77% of total memory"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by mamlouk on 2007-12-26
I'm running Ubuntu Gutsy 7.10 64-bit edition on an AMD Athlon 64 3200+ with 2 GB of RAM with a 2.6.23 kernel, and I noticed a very strange behavior regarding USB2.0 external hard-drives.

When my computer starts, and my external hard-drive connected via USB2.0, my System Monitor's tray icon says in the memory tool tip:```
Memory:
11% in use by programs
11% in use as cache
```
A folder on that drive is shared via samba, which holds all my media. So I play a couple of media files on my external media player which reads them from my shared samba folder, then I notice the following:```
Memory:
16% in use by programs
77% in use as cache
```
The cache stays up as long as the drive is mounted. Once I unmount the external hard-drive, the cache goes back to normal. I'm not facing major problems regarding this issue, but I wanted to know if this behavior is normal.

Thanks

---

### Post by kidders on 2008-01-05
Hi there,

It's been a while since you posted this, but just in case you haven't found out some other way, it's perfectly normal.

---

### Post by mamlouk on 2008-01-08
Thank you for your reply, but is there any way I could flush the cache? Or does Ubuntu reclaim more memory for programs as applications are opened?

---

### Post by kidders on 2008-01-08
It does indeed.

---

