---
title: "Interpreting sensors output..."
date: 2014-04-30
forum: Hardware
---

### Post by freebird54 on 2014-04-30
Hopefully this is the right place to post this question.  I finally got lm-sensors to work (with the new kernel - and distilling knowledge from a number of posts) - however - I find that I cannot be sure *what* the output is telling me.  On my other system the results are quite clear (and less extensive) - on this new one few of the terms make unequivocal sense!

Here is the output:
```

freebird@nest:~$ sensors
radeon-pci-0008
Adapter: PCI adapter
temp1:         -4.0°C  (crit = +120.0°C, hyst = +90.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

nct6791-isa-0290
Adapter: ISA adapter
in0:                    +0.91 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.29 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.34 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in10:                   +0.18 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                   +0.18 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +0.22 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   837 RPM  (min =    0 RPM)
fan2:                  3488 RPM  (min =    0 RPM)
fan3:                     0 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   827 RPM  (min =    0 RPM)
SYSTIN:                 +25.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:                 +28.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:               +102.0°C    sensor = thermistor
AUXTIN1:               +103.0°C    sensor = thermistor
AUXTIN2:               +103.0°C    sensor = thermistor
AUXTIN3:               +103.0°C    sensor = thermistor
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
PCH_MCH_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled

```

The fan information is clear enough - the CPUTIN may be the main CPU temp reading (it fits with the relaxed fan results!) - but what are the AUXTIN0 thru AUXTIN3?  Being that this is a 4 core system, that could be it - but why are the readings so high?  Do I need to apply a scale factor - and if so - what factor?  Does the notation about thermistors mean they are voltage throttlers rather than sensors? Any help would be appreciated..

Thanks in advance

---

### Post by Yellow Pasque on 2014-04-30
What kernel are you running?

> but what are the AUXTIN0 thru AUXTIN3?
Probably sensors that aren't connected to anything (i.e. garbage values that you can ignore).

---

### Post by freebird54 on 2014-04-30
> **Temüjin said:**
> What kernel are you running?


Currently on Trusty Tahr x86_64, so 3.13.0-24-generic. Hardware list is in the sig (the AMD quad core).

---

