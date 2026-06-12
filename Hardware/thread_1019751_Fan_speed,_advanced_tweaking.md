---
title: "Fan speed, advanced tweaking"
date: 2008-12-23
forum: Hardware
---

### Post by Hoyland84 on 2008-12-23
Hi!

I have managed to reduce my fan speed for my CPU with pwmconfig. Noise has been reduced, but my two chassis fans are still running at what seems to be full speed. This is not necessary as there's more than enough air flowing through the cabinet. The two fans are parallel coupled from the same source and have no sensors to read and/or tweak the RPM of the fans. Only two cables going to each fan. Adjusting in BIOS setup seems to be impossible.

What I want is to reduce the voltage going out to the fans and by that way reduce their speed and noise level. Is this possible without actually installing new hardware on the circuits? If you don't know how to do this, just knowing whether it would be possible to do this or not, would help me out.

Here's my sensors readout:
```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +34.0°C                                    
Core1 Temp:  +27.0°C                                    

it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:       +12.54 V  (min =  +0.00 V, max = +16.32 V)   
-12V:       -15.46 V  (min = -27.36 V, max =  +3.93 V)   
-5V:         +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:        +3.15 V
fan1:        872 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
M/B Temp:    +32.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +28.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
Temp3:      +128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

```

---

### Post by teaker1s on 2008-12-30
No you need either three wire with speed sensor or manual fan controller

---

### Post by Hoyland84 on 2009-01-04
OK. Thanks!

---

