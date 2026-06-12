---
title: "CLI softwares like htop"
date: 2008-09-16
forum: General Help
---

### Post by amin_inb on 2008-09-16
Hi

Is there any other software like "htop" to monitor cpu

I want a simple one that can show information in some few lines

---

### Post by WRDN on 2008-09-16
You can use lm-sensors to monitor the CPU temperature:

```
sudo apt-get install lm-sensors
```

Now, type:

```
sudo sensors-detect
```

Reboot the PC, and you can now access the program from the Terminal by typing:

```
sensors
```

Example output:

> it87-isa-0290
Adapter: ISA adapter
VCore 1:     +1.63 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +2.62 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.20 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +3.79 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.22 V  (min =  +0.00 V, max = +16.32 V)
-12V:        -3.92 V  (min = -27.36 V, max =  +3.93 V)
-5V:         -5.33 V  (min = -13.64 V, max =  +4.03 V)
Stdby:       +4.70 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +0.00 V
fan1:       3443 RPM  (min =    0 RPM, div = Eight)
fan2:          0 RPM  (min =    0 RPM, div = Eight)
M/B Temp:    +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
Temp3:       +50.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode


If you want a GUI based application, you can use xsensors:

```
sudo apt-get install xsensors
```

---

