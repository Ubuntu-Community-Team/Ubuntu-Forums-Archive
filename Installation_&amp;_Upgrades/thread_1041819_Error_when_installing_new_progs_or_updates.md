---
title: "Error when installing new progs or updates?"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by dcmills on 2009-01-16
Hello all,

I am getting the following error whenever I try to install new sw or when I try to install the "available" updates.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I even tried to do this, however when I go to the terminal and run the suggested command, it tells me that "dpkg: requested operation requires superuser privilege"  ... and my understanding is that this is not possible with Ubuntu.

Any suggestions would be great.

Thanks,
David

---

### Post by Tim Sharitt on 2009-01-17
Run with sudo
```
sudo dpkg --configure -a
```

---

