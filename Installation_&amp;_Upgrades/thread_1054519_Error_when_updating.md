---
title: "Error when updating"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Michael Maurice on 2009-01-29
I'm trying to install the recommended updates but get the following message when attempting to do so:

[COLOR="Blue"]E: dpkg was interrupted, you must manually run 'dpkg --configure a' to correct the problem

E: _cache->open()failed, please report.[/COLOR]

What does this mean and how do I correct it?

---

### Post by Partyboi2 on 2009-01-29
Open a Terminal (Applications>Accessoires>Terminal) and do as it suggests
```
sudo dpkg --configure -a
```

It means that the package manger was interrupted and by manually running dpkg --configure -a you telling it to configure all unpacked packages.

---

### Post by Michael Maurice on 2009-01-29
Thanks ever so much, it worked.

---

### Post by trendy09 on 2009-01-29
Thanks from me too.

---

### Post by vrie8 on 2009-02-02
> **Partyboi2 said:**
> Open a Terminal (Applications>Accessoires>Terminal) and do as it suggests
```
sudo dpkg --configure -a
```

It means that the package manger was interrupted and by manually running dpkg --configure -a you telling it to configure all unpacked packages.
thanks PartyBoi2 i've solve the problem to...

---

