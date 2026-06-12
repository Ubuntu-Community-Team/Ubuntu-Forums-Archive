---
title: "confused about system monitor, memory"
date: 2010-07-08
forum: Hardware
---

### Post by trojan0852 on 2010-07-08
I'm considering upgrading my RAM, but I'm confused about current memory usage.  I'm running a refurbished desktop with Pentium 4, 1.7 Ghz, Memory 497.4MiB, 9.10 Karmic. It seems a lot slower than my laptop with Pentium M, 1.7 Ghz, Memory 1Gb, Windows XP. I'm assuming that's largely down to the RAM.  When I check System Monitor it typically shows maybe 30-40% memory usage (and tiny swap usage), which suggests spare capacity to me. But, I then check Top concurrently, and it shows memory 80-90% usage. I'm inclined to act based on the Top info, but I don't understand why they seem to show different info.  Should I upgrade? Can anyone explain the confusion? Thanks.

---

### Post by SlugSlug on 2010-07-08
try 
```
free -m
```

you'll most likely find that ubuntu has just cached in your ram -- Linux likes to do that ;)

---

### Post by trojan0852 on 2010-07-08
Thanks Slug, I now learned something about memory buffer/cache, so Sys Monitor numbers make sense.   This leaves me with a Desktop that reularly max's out the CPU with normal web browsing, but the RAM is rarely more than 40% usage. So, am I right to conclude that adding more RAM will likely not make things faster?

---

### Post by SlugSlug on 2010-07-08
Pentium 4, 1.7 Ghz, Memory 497.4MiB should be enough..

---

### Post by cascade9 on 2010-07-08
> **trojan0852 said:**
> I'm considering upgrading my RAM, but I'm confused about current memory usage. I'm running a refurbished desktop with Pentium 4, 1.7 Ghz, Memory 497.4MiB, 9.10 Karmic. It seems a lot slower than my laptop with Pentium M, 1.7 Ghz, Memory 1Gb, Windows XP. I'm assuming that's largely down to the RAM. When I check System Monitor it typically shows maybe 30-40% memory usage (and tiny swap usage), which suggests spare capacity to me. But, I then check Top concurrently, and it shows memory 80-90% usage. I'm inclined to act based on the Top info, but I don't understand why they seem to show different info. Should I upgrade? Can anyone explain the confusion? Thanks.

Pentium 4 IS a lot slower than pentium M- 

> a 1.6 GHz Pentium M can typically attain or even surpass the performance of a 2.4 GHz Pentium 4-M

Pentium 4-M is the same speed as petium 4. 

If you are checking system montiro, be aware that it eats a lot of CPU cycles. htop is far more accurate. 

SlugSlug is right, the reason why top is showing a lot more memory use is because its couting cache programs (eg, htop shows me at aprox 690MB RAM usage, top/free -m show me at just under 2GB).

> **trojan0852 said:**
> Thanks Slug, I now learned something about memory buffer/cache, so Sys Monitor numbers make sense.   This leaves me with a Desktop that reularly max's out the CPU with normal web browsing, but the RAM is rarely more than 40% usage. So, am I right to conclude that adding more RAM will likely not make things faster?

Yes, adding more RAM wont make things any faster. Well, on 9.10 it wont, but if (when) you move to 10.04 or higher, you may well need more memory then (as the reccomended RAM levels increased from 512MB for 9.10 to 1GB for 10.04)

---

### Post by trojan0852 on 2010-07-08
slugslug, cascade9, thanks for your comments. I'll leave things as they are until such time as I can afford a faster processor. Cheers.

---

### Post by cascade9 on 2010-07-08
Glad it helped. 

BTW, upgrading a P4 can be super 'fun', be sure to check your hardware and what is compatible before you even think about doing it.

---

