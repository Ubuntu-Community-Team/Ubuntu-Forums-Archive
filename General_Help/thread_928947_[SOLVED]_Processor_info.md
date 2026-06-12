---
title: "[SOLVED] Processor info"
date: 2008-09-24
forum: General Help
---

### Post by kokkus on 2008-09-24
HI. 
Where or how can I find all the info about my processor
like which model, 32 or 64 bit etc...?

---

### Post by Ryadt on 2008-09-24
```
uname -m
```
If you get i686, it's 32bit. Otherwise it's 64bit.

---

### Post by kokkus on 2008-09-24
Thanks but I mean all the info like model number, version and so.

---

### Post by Steveway on 2008-09-24
> **kokkus said:**
> Thanks but I mean all the info like model number, version and so.

cat /proc/cpuinfo

---

### Post by Ryadt on 2008-09-24
Go in System > Administration > System Monitor > System.

---

### Post by niteshifter on 2008-09-24
Hi,

```
cat /proc/cpuinfo
```

will tell all about your processor.

```
uname -m
```
will not tell you anything about the processor, it will tell you what OS version (32 or 64 bit build) you have installed. 32 bit OS'es can run on 64 bit hardware, but not vice versa.

---

### Post by kokkus on 2008-09-24
AH. THank you guys:)

---

