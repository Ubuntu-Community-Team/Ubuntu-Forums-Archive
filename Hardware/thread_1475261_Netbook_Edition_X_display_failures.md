---
title: "Netbook Edition X display failures"
date: 2010-05-06
forum: Hardware
---

### Post by nunyez on 2010-05-06
I've setup netbook edition on my asus 1001p netbook. About once per day I have started getting display errors, X crashes, and it prompts me to go into low graphics mode.

From syslog i've captured:
```
May  6 10:00:00 netphace gdm-binary[798]: WARNING: GdmDisplay: display lasted 0.584602 seconds
May  6 10:00:00 netphace gdm-binary[798]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
 
```

My xorg log seems to all be relevant so I have attached those logs. Any help would be appreciated!

---

### Post by nunyez on 2010-05-12
System->Monitor shows 'Monitor unknown' which is part of the problem. X.org crashes because it cant detect monitor. Intel integrated GMA 3150.

Help appreciated. These x.org crashes are getting old :(

---

### Post by guillegauna on 2010-10-13
please, if u have some answers about, TELLMEE!!

sometimes, mi screen looks likes off

i mean, all de screen its black!!

but de computer continues on!!!

its freakme out!!:(

but now i have netbook ubuntu 10.04!

---

