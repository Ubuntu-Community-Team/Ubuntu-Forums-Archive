---
title: "cpuinfo seems to ignore overclocking"
date: 2009-08-30
forum: Hardware
---

### Post by vexorian on 2009-08-30
You know
```
cat /proc/cpuinfo | grep -i Mhz
``` And many other tools that show clock rate are giving me wrong clock rates, ok, they give me clockrates as if I wasn't overclocking the machine, but I am.

Normally, the max speed would be 2.93 Ghz , but I am overclocking to 3.36 Ghz using a percentage overclock feature in my ASUS board I know that the overclocking works even in ubuntu, because when testing temperature I put the CPU on load by using a timed hill climbing algorithm, and I get consistently better results when the overclocking is on.

Well, what happens is that it should sho 3300-ish  Mhz, but it shows 2960Mhz, is there a way to make these things overclock-conscious? windows and bios show the correct clock rate.


(I test cpuinfo when the thing is in full load, so no scaling is causing the issue)

---

