---
title: "Cam my computer handle 64 bit ubuntu?"
date: 2010-01-11
forum: Hardware
---

### Post by wlraider70 on 2010-01-11
So i have a windows box that i know runs vista 32 bit.
but its a quad core that's not that old so how do determine if it can handle 64 bit?

its an Intel Core2 Quad CPU q6600 @ 2.40GHZ

---

### Post by howefield on 2010-01-11
It can handle 64 bit.

If you want to confirm, type the following into a terminal (Applications > Accessories > Terminal)

```
cat /proc/cpuinfo
```

If you see lm in the flags, it is 64 bit capable, the clfush should say 64 as well.

---

### Post by wlraider70 on 2010-01-11
opps i forgot the other half of my question.

do i use the AMD64 ubutnu version even though i have an intel.

---

### Post by amauk on 2010-01-11
yes,
It doesn't matter whether you have Intel or AMD

AMD beat Intel to releasing 64-bit processors and AMD64 was the code name AMD gave the architecture (and it stuck)

---

### Post by jocko on 2010-01-11
> **wlraider70 said:**
> opps i forgot the other half of my question.

do i use the AMD64 ubutnu version even though i have an intel.
Yes. "amd64" is just a confusing name, coming from the fact that it was amd that invented the cpu architecture that is used by most 64 bit cpus (including intel).

---

### Post by wlraider70 on 2010-01-11
THANKS all.

---

### Post by cascade9 on 2010-01-12
> **amauk said:**
> AMD beat Intel to releasing 64-bit processors and AMD64 was the code name AMD gave the architecture (and it stuck)

Actually, Intel got in 1st. Itanium, 2001 vs Athlon 64, 2003-  

[http://en.wikipedia.org/wiki/Itanium](http://en.wikipedia.org/wiki/Itanium)
[http://en.wikipedia.org/wiki/Athlon_64](http://en.wikipedia.org/wiki/Athlon_64)

But Itanium wasnt compatible with x86, it was IA64 instructions only. Part of the reason why it 'failed'. AMD64 is x86 compatible, this is why some people call it x86_64, etc.

---

