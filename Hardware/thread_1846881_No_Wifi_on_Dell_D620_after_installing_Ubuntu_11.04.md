---
title: "No Wifi on Dell D620 after installing Ubuntu 11.04"
date: 2011-09-19
forum: Hardware
---

### Post by vipulrb on 2011-09-19
I can not connect to wifi or any network after indtalling Ubuntu 11.04 on Dell D620.

---

### Post by josephmills on 2011-09-19
> **vipulrb said:**
> I can not connect to wifi or any network after indtalling Ubuntu 11.04 on Dell D620.

I am guessing that you need the b43 driver go to additinal drivers and install then press alt+f4<---wireless hot key 

if that wont work open your terminal ctrl+alt+t and type in ```
lspci -nn
```
then 
```
rfkill list all 
```
then 
```
lsmod
``` 
then paste all here thanks

---

