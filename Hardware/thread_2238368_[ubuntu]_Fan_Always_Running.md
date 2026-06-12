---
title: "[ubuntu] Fan Always Running"
date: 2014-08-07
forum: Hardware
---

### Post by alex235 on 2014-08-07
Hi guys,

   Fan is always running, when I use sensors I get:
 ```

>> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +40.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +38.0°C  (high = +100.0°C, crit = +100.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +40.0°C  

nouveau-pci-0400
Adapter: PCI adapter
temp1:            N/A  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)


```

Odd that I'm getting N/A from nouveau-pci-0400. I'm using the NVIDIA GEFORCE 740M graphics card. Haven't been able to find someone with similar problem. The laptop itself is new, got it about 3 months ago.

---

