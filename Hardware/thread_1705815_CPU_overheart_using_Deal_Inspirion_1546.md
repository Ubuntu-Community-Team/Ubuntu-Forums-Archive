---
title: "CPU overheart using Deal Inspirion 1546"
date: 2011-03-12
forum: Hardware
---

### Post by Blue112 on 2011-03-12
Hi everyone.

I've recently bought a Dell Inspirion 1546, and the main problem is the cpu temperature.

Here's what sensors say :

**Idle**
> 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.5°C  (crit = +100.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +58.6°C  (high = +70.0°C, crit = +100.0°C)


**On a flash app in firefox**
> acpitz-virtual-0
Adapter: Virtual device
temp1:       +77.5°C  (crit = +100.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +76.2°C  (high = +70.0°C, crit = +100.0°C)  

(it can reach more than 90° sometime).

60° is kinda hot too for a idle desktop...

Here is some basic information about my hardware :
CPU :
> model name	: AMD Athlon(tm) X2 Dual-Core QL-64
stepping	: 1
cpu MHz		: 1050.000
cache size	: 512 KB


GPU : 02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

Graphic driver (unsure) : FGLRX (up to date)

The laptop is pretty new (about 6 months). I've opened it few days ago, it's totally clean of dust.

How can I make the temperature decrease to a normal level ?

---

### Post by mardo on 2011-09-16
Hey,

I have the exact same problem! With the same hardware running debian. I even tried switching to the open-source readon driver (mesa 7.12 git) and tweaking the cpu governor.

Right know ,while compiling a custom kernel, the sensors output even reaches 87 and 85 degrees with a load average of 1.72 1.55 1.29 
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +87.5°C  (crit = +100.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +85.1°C  (high = +70.0°C, crit = +100.0°C)  
```

I don't think it is possible to fix this under linux since i have the same problems under windows 7. Of course I can't accurately measure the temp and load under windows but it is just as hot to the touch.

---

