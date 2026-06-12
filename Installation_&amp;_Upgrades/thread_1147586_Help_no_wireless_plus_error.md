---
title: "Help no wireless plus error"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by felixayalajr on 2009-05-03
help my wireless internet doesn't work and i get this message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


How do i do this?

---

### Post by Partyboi2 on 2009-05-03
Hi, do as the message says. Open a terminal (Applications>Accessories>Terminal) and type or paste
```
sudo dpkg --configure -a
```

---

