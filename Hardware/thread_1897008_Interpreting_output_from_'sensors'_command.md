---
title: "Interpreting output from 'sensors' command"
date: 2011-12-18
forum: Hardware
---

### Post by sewerurchin on 2011-12-18
Hi,

Here is the output I get when I run the 'sensors' command:

it8720-isa-0228
Adapter: ISA adapter
in0:          +1.09 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.34 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.17 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.34 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.25 V  
fan1:        1670 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1380 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +33.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
temp3:        +45.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:    +1.250 V

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +35.5°C  (high = +70.0°C)
                       (crit = +79.0°C, hyst = +77.0°C)

How do I determine what 'temp1', 'temp2', etc correspond to?

---

