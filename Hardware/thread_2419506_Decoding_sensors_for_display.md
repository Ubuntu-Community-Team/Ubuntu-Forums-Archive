---
title: "Decoding sensors for display"
date: 2019-05-23
forum: Hardware
---

### Post by freebird54 on 2019-05-23
I am sure this has come up before, but I am unsure as to which reported items are what I need. Here is what sensors now reports:

```

freebird@nest:~$ sensors
radeon-pci-0008
Adapter: PCI adapter
temp1:         +7.0°C  (crit = +120.0°C, hyst = +90.0°C)

nct6791-isa-0290
Adapter: ISA adapter
Vcore:                  +0.90 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.00 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:                   +3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:                  +3.36 V  (min =  +2.98 V, max =  +3.63 V)
in4:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:                   +3.34 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:                   +3.31 V  (min =  +2.70 V, max =  +3.63 V)
in9:                    +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in10:                   +0.18 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                   +0.18 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +0.22 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   986 RPM  (min =    0 RPM)
fan2:                  3600 RPM  (min =    0 RPM)
fan3:                     0 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   909 RPM  (min =    0 RPM)
SYSTIN:                 +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:                 +39.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:               +102.0°C    sensor = thermistor
AUXTIN1:               +100.0°C    sensor = thermistor
AUXTIN2:               +100.0°C    sensor = thermistor
AUXTIN3:               +101.0°C    sensor = thermistor
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
PCH_MCH_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled

asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.9°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

```

I have seen suggestions that AMD chips give exaggerated temperature reports, and others who disagree. What I suspect is that 
CPUTIN:  +39.5 C
is accurate enough, and reports the main CPU overall temperature in Celsius and that the 
AUXTIN0:               +102.0°C    sensor = thermistor
AUXTIN1:               +100.0°C    sensor = thermistor
AUXTIN2:               +100.0°C    sensor = thermistor
AUXTIN3:               +101.0°C    sensor = thermistor

lines refer to the separate cores, and report in Fahrenheit despite the C shown. It may be just that the numbers need adjusting down by 60, though. Which is more likely, do you think? Before I awk or sed the heck out of it for use in a conky, it would be nice to have an expert opinion :)

Thanks for your time

freebird

---

### Post by CatKiller on 2019-05-23
> **freebird54 said:**
> What I suspect is that CPUTIN is accurate enough, and reports the main CPU overall temperature in Celsius and that the 
AUXTIN lines refer to the separate cores, and report in Fahrenheit despite the C shown. It may be just that the numbers need adjusting down by 60, though. Which is more likely, do you think?
I don't think either is likely. No one uses Fahrenheit. More likely is that those sensor lines aren't connected to anything useful.

---

### Post by freebird54 on 2019-05-23
Thyanks - I was afraid of that! Of course, when I built my system, it was a higher priority to avoid contributing to Microsoft than to investigate the hardware reporting capabilities...

From the  non-comment, I am going to assume that the CPUTIN line does refer to the CPU overall, and work from there. I guess fan speeds will take the place of the other lines! :)

Thanks, and I'll mark it [SOLVED].

freebird

---

### Post by CatKiller on 2019-05-23
> **freebird54 said:**
> Thyanks - I was afraid of that! Of course, when I built my system, it was a higher priority to avoid contributing to Microsoft than to investigate the hardware reporting capabilities... 
It's cheaper for manufacturers to get an off-the-shelf sensor chip for use across all their products that provides more than they need than to have lower volumes of more expensive chips customised to each use case. Unused sensor lines are the norm. 
> From the  non-comment, I am going to assume that the CPUTIN line does refer to the CPU overall, and work from there. I guess fan speeds will take the place of the other lines! :)
Yes. CPU Temperature Input.

I have conditional colouring in my conky for temperatures and fans.

---

