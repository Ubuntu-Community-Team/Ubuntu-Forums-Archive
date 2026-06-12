---
title: "help with synaptic package manager"
date: 2008-07-19
forum: General Help
---

### Post by Exile666 on 2008-07-19
when ever the launch th SPM i get this:

> "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

what does it mean, how do i fix this?

---

### Post by coffeecat on 2008-07-19
Something wrong with the package database. Not a big issue. Open a terminal, and:

```
sudo dpkg --configure -a
```

---

