---
title: "How can i activate smp  on jaunty and karmik?."
date: 2010-02-16
forum: Hardware
---

### Post by puimino on 2010-02-16
hi! i have  a  AMD  Athlon 64 X2 processor,  but i would like   get  the maxmimun performance to that processor.

OK, by the moment is not possible install a 64 bit system.

So how can i do to activate the smp on jaunty and karmik in a 32 bits system to  improve the use of  both cores of  processor.

---

### Post by sisco311 on 2010-02-16
The generic kernel supports smp; it should detect the processors at boot time.

What's the output of:
```
cat /proc/cpuinfo
```
&
```
uname -a
```?

---

