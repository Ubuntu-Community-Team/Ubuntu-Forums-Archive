---
title: "how do i know if i have 32bit or 64bit?"
date: 2009-04-05
forum: Hardware
---

### Post by totallyclueless on 2009-04-05
I have ubuntu 8.10

---

### Post by benjatodd on 2009-04-05
Go to Places > Computer, then click on filesystem, etc, apt, then sources.list.save.  On the first row if it says "Release i386" you have 32 bit, if it says "Release amd64" you have 64 bit.  There's probably an easier way to find out but that should work.

---

### Post by cariboo on 2009-04-05
A much easier way to find out what cpu you have is to opne an Applications-->Accessories-->Terminal and type:

```
cat /proc/cpuinfo
```

this is a partial listing for my cpu:

```
 cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.231
cache size	: 512 KB
```

Jim

---

### Post by Sealbhach on 2009-04-05
Type in a terminal 

```
uname -m
```

also 

```
uname -a
```

will give you more information.

.

---

