---
title: "Ubuntu 12.04 lm-sensors reports CPU temps +20-25 Deg C higher"
date: 2014-03-16
forum: Hardware
---

### Post by sparticle2000 on 2014-03-16
I have an Ubuntu 12.04 installation on my desktop. Gigabyte GA-G41MT-D3 (rev. 1.3) motherboard. It is dual boot with Windows (Historical unused now) and both the bios and windows report the CPU temps correctly. In Ubuntu via lm-sensors the temps are reported about 20 Deg C higher. Does anyone knowif this is a known issue. I found various obscure posts around the net from google some talking about slope errors in the thermal reporting etc.

LM sensors seems to detect everything ok and loads the modules fine. This CPU is a Xeon L5430. But as I said in the bios cpu temp is about 25 Deg C and the same in windows. There is another sensor showing as about the same value listed as temp3. Is this the same CPU sensor that the bios and windows are using? See below I have highlighted the relevant temps. I don't see how the cpu cores could be at 40-50 Deg C and the CPU temp show as 25 Deg C in the bios and windows. Another clue is that the CPU fan (fan1) is running slow at c.1000rpm instead of flat out at 2000 rpm. Some of the numbers make no sense like negative numbers.
~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       [COLOR=#ff0000]+48.0°C[/COLOR]  (high = +73.0°C, crit = +85.0°C)
Core 1:       [COLOR=#ff0000]+44.0°C[/COLOR]  (high = +73.0°C, crit = +85.0°C)
Core 2:       [COLOR=#ff0000]+46.0°C [/COLOR] (high = +73.0°C, crit = +85.0°C)
Core 3:       [COLOR=#ff0000]+46.0°C [/COLOR] (high = +73.0°C, crit = +85.0°C)

it8718-isa-0290
Adapter: ISA adapter
in0:          +1.12 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.54 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.23 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.78 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +0.26 V  (min =  +0.00 V, max =  +2.10 V)
in5:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in7:          +3.06 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +2.74 V  
fan1:        [COLOR=#ff0000]1036 RPM[/COLOR]  (min =   10 RPM)
fan2:        1548 RPM  (min =   10 RPM)
temp1:        -55.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        [COLOR=#ff0000]+25.0°C[/COLOR]  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
cpu0_vid:    +1.550 V
intrusion0:  OK

Any help or advice appreciated.

Cheers
Spart

---

