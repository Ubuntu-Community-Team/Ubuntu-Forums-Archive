---
title: "i get error when i open the Update manager OR..."
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by hellish_eye on 2009-03-19
Can anybody help with this, whenever i open the Update Manager OR the Add/Remove Application, i get the Error


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Just if it will help :S i was trying to install LimeWire.deb  ! and it took so long and the laptop turned off before the installation get done..

i hope anyone can help with that...

---

### Post by Pumalite on 2009-03-19
Run:
```
sudo dpkg --configure -a
```

---

### Post by hellish_eye on 2009-03-19
thanks :) it worked :D

---

