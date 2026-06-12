---
title: "Uninstalling an application"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-21
I forced installed (on wrong architecture)

1)Peazip
2)flash player

And both of them do not appear in the synaptic package manager...how do I uninstall these?

Also I installed ddresuce by apt-get, but it did not appear anywhere.

---

### Post by dE_logics on 2009-04-21
No one?

---

### Post by stilling on 2009-04-21
> **dE_logics said:**
> No one?

try sudo apt-get remove name of the program 
or sudo apt-get purge name of the program that did it for me

---

### Post by oldos2er on 2009-04-21
```
sudo dpkg -r <packagename.deb>

```

---

### Post by dE_logics on 2009-04-21
2 packages got removed (one by each technique).

Is there anyway to view all the packages (specially such sort of 'hidden' packages)?

---

### Post by oldos2er on 2009-04-21
```
dpkg -l | more
```

---

### Post by dE_logics on 2009-04-22
Ok...thanks a lot!

---

