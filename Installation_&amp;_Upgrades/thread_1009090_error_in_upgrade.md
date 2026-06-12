---
title: "error in upgrade"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by cysilver on 2008-12-12
i am upgrading my ubuntu and it the computer crashed while upgrading them i tried again and it gives me this error now 
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error processing passwd (--configure):
 package passwd is not ready for configuration
 cannot configure (current status `triggers-awaited')
Errors were encountered while processing:
 passwd
E: Sub-process /usr/bin/dpkg returned an error code (1)

can someone help me plz

---

### Post by zvacet on 2008-12-12
```
sudo dpkg --configure -a
```

---

