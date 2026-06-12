---
title: "Error Message - Need Help"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by vlastanovak on 2008-12-25
I have just installed ubuntu and have received the following error message when I attempted to install a totem plug in to watch a dvd and also when i tried to add the program desktop effects;

----------

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

----------

Suggestions?

---

### Post by Partyboi2 on 2008-12-25
hi,
Open a terminal (Applications>Accessories>Terminal) and do as it says.
```
sudo dpkg --configure -a
```

---

