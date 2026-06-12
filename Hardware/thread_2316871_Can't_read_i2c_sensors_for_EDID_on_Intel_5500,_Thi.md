---
title: "Can't read i2c sensors for EDID on Intel 5500, Thinkpad T450"
date: 2016-03-11
forum: Hardware
---

### Post by Herb_Sepplmaer on 2016-03-11
Hey,

I am on Ubuntu 15.10 on a Thinkpad t450 with Intel 5500 chipset. I am trying to read out my EDID and I want to find out the bus the l2c sensor is on.

I am trying to use ```
***sudo /usr/sbin/sensors-detect***
```
but I retrieve the following:
```
[I][B]Found unknown SMBus adapter 8086:9ca2 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.[/B][/I]
```

Any clue what's going on here? Much appreciate your help.

---

