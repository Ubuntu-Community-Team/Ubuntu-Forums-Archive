---
title: "wifi light blink"
date: 2014-06-21
forum: Hardware
---

### Post by ken_cullum on 2014-06-21
my hp 6930p running 14.04 wifi light blinks only on ubuntu  windows 7 no blink any terminal command to fix this thanks ubuntus the best

---

### Post by jeremy31 on 2014-06-21
```
lspci
``````
lsmod
```
There is likely a module option to disable the led

---

### Post by tgalati4 on 2014-06-21
To get the switches availabe for your wireless module:

```
modinfo nameofyourwirelessmodulethatyouaretryingtoturnoffled
```

---

