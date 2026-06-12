---
title: "Motherboard temperature too high."
date: 2008-11-07
forum: Hardware
---

### Post by Bruce M. on 2008-11-07
Hi folks...

I think my motherboard temperature is too high and it's worrying me.

I have an MSI K8N SLI-F 939 NVIDIA nForce4 SLI ATX AMD mainboard with an AMD64 CPU.  Attached is an image showing 45°C (at the moment it's 59°C)

I can't find anything on the net, to date, to tell me what the norms are for this board although I'm still looking.

Sensors tells me: high=28°C, see why I'm a bit worried.
```
bruloo@bruloo:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +59.0°C                                    

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.40 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.46 V  (min =  +9.18 V, max =  +0.24 V)
+3.3V:       +3.14 V  (min =  +1.47 V, max =  +3.98 V)
+5V:         +4.91 V  (min =  +5.97 V, max =  +4.59 V)
-12V:       -11.87 V  (min = -13.10 V, max = -13.59 V)
V5SB:        +5.03 V  (min =  +1.10 V, max =  +1.96 V)
VBat:        +2.99 V  (min =  +1.01 V, max =  +3.09 V)
fan1:          0 RPM  (min = 168750 RPM, div = 2)
CPU Fan:    24107 RPM  (min =   -1 RPM, div = 8)
fan3:       5192 RPM  (min = 9926 RPM, div = 2)
**M/B Temp:    +44.0°C  (high = +28.0°C,** hyst =  +8.0°C)  sensor = thermistor
CPU Temp:    +53.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +23.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
cpu0_vid:   +0.000 V
beep_enable:enabled

bruloo@bruloo:~$
```
I have NO idea what that hyst = +8.0°C means either.

Any help put there?

Chimo!
Bruce

---

