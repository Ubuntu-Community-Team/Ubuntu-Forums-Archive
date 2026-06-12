---
title: "you must manually run 'dpkg --configure -a' to correct the problem."
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by babazero on 2008-12-04
I am newbie to linux please don't scare me away.I got this error when updating ubuntu please help all this occured after i had a power cut whilst installing the updates.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2008-12-04
Close down synaptic, add/remove, or update-manager first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by iponeverything on 2008-12-04
open a terminal and run:

```
sodu dpkg --configure -a
```

---

### Post by babazero on 2008-12-04
Thank you for the fast response.

---

### Post by ExemplarUbuntu on 2008-12-04
I got the same probelm after an update a couple of hours ago. Then it crashed again while updating and now it says that evolution is too badly damaged and has to be re-installed but doesn't say how.

When I try to re-install evolution from Synaptic PM it crashes/locks-up again.

PS

I ran apt-get install evolution and that worked so then I did apt-get update
and apt-get upgrade which installed the 11 packages that were failing.

I think it's ok again but I noticed one oddity. When I run apt-get update it
warns about duplicate packages in sources.list and advises me to run
apt-get update to get fix this !?

---

