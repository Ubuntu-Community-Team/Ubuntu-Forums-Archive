---
title: "Synaptic Package Manager not working..?"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by alexisd on 2009-01-21
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I'm getting that error message when I try to open the synaptic package manager. What do I do to fix it?

thanks in advance

---

### Post by taurus on 2009-01-21
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by alexisd on 2009-01-21
Okay but then when i do that it asks me for the sudo password

---

### Post by taurus on 2009-01-21
Use the same password that you log in with.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

