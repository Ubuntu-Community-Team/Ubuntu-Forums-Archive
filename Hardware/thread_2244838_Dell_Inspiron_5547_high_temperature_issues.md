---
title: "Dell Inspiron 5547 high temperature issues"
date: 2014-09-19
forum: Hardware
---

### Post by demonic2 on 2014-09-19
Hello ubuntu forums!

I'm using the latest ubuntu 14.04 on the Dell Inspiron 5547. (It was originally shipped with the 12.04)
I am facing problems with overheating. It has high temperature in the right side of the laptop (keyboard touch pad) so I can't type with comfort because its hot!
This laptop comes with two graphics cards (Intel from the i7 and one AMD ATI Radeon)

Output from sensors:

> coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +70.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +68.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +68.0°C  (high = +100.0°C, crit = +100.0°C)


i8k-virtual-0
Adapter: Virtual device
Right Fan:   84000 RPM
CPU:          +71.0°C  



I am using the fglrx driver and I have tested it with the opensource one too. 

Is there any fix for that?

---

