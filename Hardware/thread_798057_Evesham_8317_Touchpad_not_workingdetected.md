---
title: "Evesham 8317 Touchpad not working/detected"
date: 2008-05-17
forum: Hardware
---

### Post by werxie on 2008-05-17
Need to get the touchpad mouse working on this laptop, but I have absolutely no idea about how to. I'm not very experienced with linux, and I have searched for solutions but was unable to find anything relating to an Evesham machine. 

Any help would be greatly appreciated.

---

### Post by teaker1s on 2008-05-18
terminal ```
lspci-v
```
and ```
lsusb
```
from output you can locate the device product and vendor id and then proceed to find a solution

---

