---
title: "updates received error"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by keyfeather on 2009-03-22
Trying to download the most current updates and received this message. Can someone please tell me what to do. This information makes no sense to me.  Thanks!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by kestrel1 on 2009-03-22
Open a terminal & type```
sudo dpkg --configure -a
```
You will need to enter your password & that should sort it out.

---

