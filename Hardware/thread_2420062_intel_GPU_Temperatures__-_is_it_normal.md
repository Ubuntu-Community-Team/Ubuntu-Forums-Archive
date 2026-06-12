---
title: "intel GPU Temperatures  - is it normal?"
date: 2019-05-29
forum: Hardware
---

### Post by Kognit on 2019-05-29
Hello,

i have Lenovo ideapad 320-171KB

After i do sensors-detect and then sensors i get:

[HTML]iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +40.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +41.0°C  (high = +100.0°C, crit = +100.0°C)

pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +46.0°C  
[/HTML]

Through PRIME i enabled only Intel and as you can see integrated graphic card is quite hot relatively to processors. This is something i do not experience in Windows. There temperature are more or less the same. Is it possible that Ubuntu reports wromg numbers?

Do you have any idea from where this difference comes?

Thank you  very much.

Best,

---

### Post by Autodave on 2019-05-29
It is possible.  However, at only 46 degrees it is definitely nothing to worry about.  As a point of reference, this desktop has been idle for over 1 1/2 hours and my Nvidia RTX 2070 is presently at 44 degrees.

---

### Post by CatKiller on 2019-05-30
40-odd degrees is absolutely fine. 70-80° is hot. Things will start throttling to manage heat at around 90°.

---

### Post by crip720 on 2019-06-04
One of my laptops had a dual core cpu, always had a 7 degree difference between the two cores.  Laptop using now all cores within a degree, but my ssd is reading 100.  Other temp monitoring reports normal temp for ssd and similar temps for core.

---

