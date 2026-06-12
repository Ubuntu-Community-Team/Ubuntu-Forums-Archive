---
title: "Ubuntu Studio Update Problem"
date: 2008-08-17
forum: General Help
---

### Post by Granner on 2008-08-17
When want to update my Ubuntu Studio this message appears on my screen:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

pls help

MfG Granner

PS: sorry for my bad english

---

### Post by Sef on 2008-08-17
Applications > Accessories > Terminal

type or copy this code:

```
sudo dpkg --configure -a
```

That should get your system working again.  If not, post any error messages.

NB: Your English is fine.  There is no problem understanding you.

---

