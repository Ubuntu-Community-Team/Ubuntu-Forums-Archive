---
title: "An Error occured"
date: 2008-11-08
forum: General Help
---

### Post by acpmex on 2008-11-08
Hi im new to Ubuntu and everything has been running well, however i'm having trouble with my synatic package manager. everytime that i try to open it, it gives me an error message.

exapmle:E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help me Please and thank you

-acpmex

---

### Post by taurus on 2008-11-08
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

