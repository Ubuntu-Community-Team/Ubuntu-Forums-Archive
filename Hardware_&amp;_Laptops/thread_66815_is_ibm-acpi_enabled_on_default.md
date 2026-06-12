---
title: "is ibm-acpi enabled on default"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by ricesteam on 2005-09-18
Is it on default or do I have to config the kernel modules?

---

### Post by AgenT on 2005-09-27
It is on by default if you are supposed to use it. However, it may not have been enabled for you for whatever strange reason. To see if it is running, type this:
```
lsmod | grep ibm
```
*lsmod* shows you all the modules loaded on your system. *grep ibm* just shows the modules with ibm in it. Note that this is using the lowercase letter L in lsmod, not an uppercase i.

---

