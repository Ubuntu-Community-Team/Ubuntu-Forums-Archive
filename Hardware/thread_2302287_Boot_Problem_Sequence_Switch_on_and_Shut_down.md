---
title: "Boot Problem Sequence Switch on and Shut down"
date: 2015-11-09
forum: Hardware
---

### Post by Z_Machine on 2015-11-09
I've installed Ubuntu 14.04.3 LTS on my PC. When I switch on the PC, then after 3 seconds approx. shuts down and then turns on automatically and after 3 seconds the PC shuts down again... If I do nothing the sequence is indefinitely repeated, but If I access to bios and exit without saving, then OS starts and runs normally. If after of having started the OS then I shut down and  turn on instantly, the PC runs normally, namely, I get into to the OS normally,  but If I shut down the PC for 15 minutes and after I switch on,  the sequence of shut down &#8211; switch on is repeated...

Maybe is a hardware problem but I would like discard an OS problem. 

I've generate a boot report here: [URL="http://paste.ubuntu.com/13207997/"]http://paste.ubuntu.com/13207997/ 
[/URL]

```

~sensors

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +30.0°C  (high = +85.0°C, crit = +105.0°C)
Core 0:         +25.0°C  (high = +85.0°C, crit = +105.0°C)
Core 1:         +30.0°C  (high = +85.0°C, crit = +105.0°C)
Core 2:         +23.0°C  (high = +85.0°C, crit = +105.0°C)
Core 3:         +22.0°C  (high = +85.0°C, crit = +105.0°C)

nct6776-isa-0290
Adapter: ISA adapter
Vcore:          +0.91 V  (min =  +0.00 V, max =  +1.74 V)
in1:            +1.86 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:           +3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:          +3.34 V  (min =  +2.98 V, max =  +3.63 V)
in4:            +0.06 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:            +1.73 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:            +0.78 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:           +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:           +3.25 V  (min =  +2.70 V, max =  +3.63 V)
fan1:          5232 RPM  (min =    0 RPM)
fan2:             0 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:          2119 RPM  (min =    0 RPM)
SYSTIN:         +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:         +26.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:         +50.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:   +30.0°C  (high = +80.0°C, hyst = +75.0°C)
                         (crit = +105.0°C)
PCH_CHIP_TEMP:   +0.0°C  
PCH_CPU_TEMP:    +0.0°C  
PCH_MCH_TEMP:    +0.0°C  
intrusion0:    ALARM
intrusion1:    OK
beep_enable:   disabled

```

[2015-12-10] Finally was a hardware problem. Thanks.

---

