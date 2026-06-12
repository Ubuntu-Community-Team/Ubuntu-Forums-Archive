---
title: "&quot;dpkg was interrupted&quot; error on synaptic package inst."
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by gilk on 2009-06-24
I get the error:
_________________
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
_______________
when ever I try to run Synaptic package manager

what should be done?

Thanks in advance

---

### Post by tarps87 on 2009-06-24
Applications -> accessories -> terminal

```
sudo dpkg --configure -a
```

---

