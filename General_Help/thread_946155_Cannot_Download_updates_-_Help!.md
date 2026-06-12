---
title: "Cannot Download updates - Help!"
date: 2008-10-13
forum: General Help
---

### Post by DB2602 on 2008-10-13
Hi, I'm trying to download the recommended updates but keep getting: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any idea how I can rectify this?  I'm new to Ubuntu and any help would be much appreciated.

Cheers,

DB

---

### Post by tangibleorange on 2008-10-13
open up a terminal (Applications -> Accessories -> Terminal) and type:

```
sudo dpkg --configure -a
```

---

### Post by DB2602 on 2008-10-13
Thanks a bunch mate!

Easy as that.

DB

---

