---
title: "Ubuntu 9.04 version"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by landrykap on 2009-10-22
Hi again,
How do I know whether my system is a 32bit or 64 bit?
:confused:

---

### Post by 80aless on 2009-10-22
```
uname -m 	
```
if x86_64 it is 64 bits. i686 is 32 bits

even better: 
```
getconf LONG_BIT
```

---

### Post by landrykap on 2009-10-22
Hey, thnx! I was getting i686 but didn't know!!
good tyme!:)

---

