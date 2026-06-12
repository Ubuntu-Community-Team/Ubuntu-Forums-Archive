---
title: "lm-sensors?"
date: 2008-08-26
forum: General Help
---

### Post by malfist on 2008-08-26
I'm running an AMD 9850 BE (quad core) and I'm trying to get the temperature readings in linux. I installed and configured (using defaults) lm-sensors and it give this:
```

jerome@ubuntu:~$ sensors
it8716-isa-0e80
Adapter: ISA adapter
VCore:       +1.84 V  (min =  +0.00 V, max =  +3.82 V)
VDDR:        +1.30 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.30 V  (min =  +4.02 V, max =  +4.08 V)
+5V:         +5.13 V  (min =  +5.51 V, max =  +6.83 V)
+12V:       +11.90 V  (min = +15.94 V, max = +16.32 V)
in5:         +1.07 V  (min =  +3.82 V, max =  +4.08 V)
in6:         +1.31 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +6.85 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.22 V
fan1:       1409 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +58.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = thermal diode
temp2:       +42.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = transistor
temp3:       +77.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = thermal diode
cpu0_vid:   +0.000 V

```

Can someone explain that to me? I don't know where the core temps are. The max temp is 60C and I see a 77, should I be bothered by that? It's been running BOINC for almost three weeks so the processors have been maxed out at 100% for almost three weeks so it should be at it's max temperature it will get with the current fan.

---

### Post by Cobra_Fast on 2008-08-26
> **malfist said:**
> I'm running an AMD 9850 BE (quad core) and I'm trying to get the temperature readings in linux. I installed and configured (using defaults) lm-sensors and it give this:
```

jerome@ubuntu:~$ sensors
it8716-isa-0e80
Adapter: ISA adapter
VCore:       +1.84 V  (min =  +0.00 V, max =  +3.82 V)
VDDR:        +1.30 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.30 V  (min =  +4.02 V, max =  +4.08 V)
+5V:         +5.13 V  (min =  +5.51 V, max =  +6.83 V)
+12V:       +11.90 V  (min = +15.94 V, max = +16.32 V)
in5:         +1.07 V  (min =  +3.82 V, max =  +4.08 V)
in6:         +1.31 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +6.85 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.22 V
fan1:       1409 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +58.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = thermal diode
temp2:       +42.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = transistor
temp3:       +77.0°C  (low  = +127.0°C, high = +112.0°C)  sensor = thermal diode
cpu0_vid:   +0.000 V

```

Can someone explain that to me? I don't know where the core temps are. The max temp is 60C and I see a 77, should I be bothered by that? It's been running BOINC for almost three weeks so the processors have been maxed out at 100% for almost three weeks so it should be at it's max temperature it will get with the current fan.

You said you set max-temp to 60C, then:
"temp1" should be your Core-Temp.
"temp2" could be your System-Temp.
"temp3" could be your Graphics-Card-Temp.

---

### Post by malfist on 2008-08-26
Are you sure about that? Lm-sensors is reporting temp1 as 60 right now, and the motherboard is set to shutdown at 60...

---

