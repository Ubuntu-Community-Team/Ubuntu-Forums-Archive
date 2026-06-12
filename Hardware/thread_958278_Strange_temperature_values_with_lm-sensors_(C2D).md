---
title: "Strange temperature values with lm-sensors (C2D)"
date: 2008-10-25
forum: Hardware
---

### Post by saz on 2008-10-25
Hi guys!

I'm with a bit of a problem here, this is part of my "sensors" output:

```
temp1:       +49.0 C  (low  =  -1.0 C, high = +127.0 C)  sensor = thermal diode
temp2:       +36.0 C  (low  =  -1.0 C, high = +127.0 C)  sensor = transistor
temp3:       -55.0 C  (low  =  -1.0 C, high = +127.0 C)  sensor = transistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0 C  (high = +78.0 C, crit = +100.0 C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +59.0 C  (high = +78.0 C, crit = +100.0 C)  
```

now the problem is simple, I don't know if my cpu temp is given by the "temp" parameter or the "core" parameter. that's because comparing to the results I get on vista, the "temp" parameter should be the one I'm looking for.

the core parameter is way hotter than the "temp" and I don't believe that my cpu would be so much hotter in linux than in vista!

just looking for some enlightment...

---

