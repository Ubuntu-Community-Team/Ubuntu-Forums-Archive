---
title: "CPU Scaling - No Device Info"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by gizzmo_jr on 2006-06-03
First time posting so be nice, ;) 

Dedicated Ubuntu user, all my problems been solved with google or searching in these forums but can't find one this time.

Just did a fresh install of Dapper, and installed HLDS and went to fire it up and it can't. Illegal Operation, bad I/O. Did some digging up and something to do with my CPU. Alright, fire up the device manage and low and behold no info. Absolutly nothing, same with memory. my /proc/cpuinfo and meminfo are completely blank. Added the CPU scaling monitor to my panel as a test, now its telling me it can't determine the scaling. Well duh if it doesn't even know what it is. I know it can't scale but just to read the stepping values.

I sure do know what it is, AMD K6-750 but how can i get Ubuntu to reload, refresh or whatever and get the proper settings?

---

### Post by ranf on 2006-06-06
[QUOTE=gizzmo_jr]
my /proc/cpuinfo and meminfo are completely blank.[/QUOTE]
"ls -l " will show them as being 0 bytes. But this must work:
```
cat /proc/cpuinfo
cat /proc/meminfo
```

Ah, another idea what could cause this: show us the output of 
```
mount
```

---

