---
title: "Installation Woes"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by owy on 2009-04-11
Hi I was installing some software and got an error message on ubantu kubantu version 8.10 as follows:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to use the terminal but it said I needed superuser priviledge doh whatever that means and was not sure what to do from there.

btw who ever gave me the hint about getting 8.10 for wireless issues thank you so much it worked.

now can you help me with this??

Owy

---

### Post by iponeverything on 2009-04-11
It needs to be run with administrative privileges -- to do this.. 

run:

```
sudo dpkg --configure -a
```

---

