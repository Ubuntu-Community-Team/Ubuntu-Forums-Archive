---
title: "Software Sources Problem"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by DavidFromCanada on 2009-02-22
Software sources won't launch, so I located the problem.
I installed 8.10 Intrepid Ibex, worked fine
I installed nUbuntu 8.12 beta, its a security linux and I didn't like it.
I removed nUbuntu
Now Software Sources doesn't know what distro it is.

sudo lsb_release -a gives me:
```
david@david-laptop:~$ sudo lsb_release -a
No LSB modules are available.
Distributor ID:	nUbuntu
Description:	nUbuntu 8.12
Release:	8.12
Codename:	Instigating Insecurity Beta Candidate 

```

How do I change it back to thinking its ubuntu?

---

### Post by everythingsround on 2009-03-03
I'm having the same problem.  I noticed that the problem is that nUbuntu is not in the /var/lib/update-manager/meta-release file so an update cannot occur.  Anyone know how to add nUbuntu to this file or another way to force a dist upgrade?  I'm willing to jump to 9.04 alpha if I have to.

---

### Post by DavidFromCanada on 2009-03-03
I'm just going to hold out until 9.04 and do a complete reinstallation of ubuntu. I find that Ubuntu gets buggy with the more updates it gets.

---

