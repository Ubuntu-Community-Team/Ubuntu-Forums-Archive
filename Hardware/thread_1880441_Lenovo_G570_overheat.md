---
title: "Lenovo G570 overheat"
date: 2011-11-13
forum: Hardware
---

### Post by Night-Horse on 2011-11-13
Hi all,

I have a new Lenovo G570 laptop, the problem is that It is always hot !! even that I changed the configuration of the CPU speed to be on demand, The minimum temperature I can get is 60, If I opened many tabs in FF it goes to 80, many times It even goes over 90.

And the overall performance is so slow, specially when the temperature goes higher, I know the CPU tries to cool itself, but It shall not go that hot, shall It?

Also note that trying to execute acpi throws a thread dump.

OS: Ubuntu 11.10 64 
Processor: Intel® Core™ i5-2410M CPU @ 2.30GHz × 4 
Ram: 8GB
Video: ATI Radeon 6450

---

### Post by Night-Horse on 2011-11-17
Pumb.

---

### Post by Night-Horse on 2011-12-11
Now I think I might need to configure fan speed for my cpu, but I don't know what to add on /etc/sensors.d/sensors.conf

here is the output of sensors command:


```
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +70.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +70.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +69.0°C  (high = +86.0°C, crit = +100.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +54.5°C  
```

---

