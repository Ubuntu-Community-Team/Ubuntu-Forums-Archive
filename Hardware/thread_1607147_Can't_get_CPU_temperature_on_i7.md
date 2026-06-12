---
title: "Can't get CPU temperature on i7"
date: 2010-10-27
forum: Hardware
---

### Post by OzzyFreakDude on 2010-10-27
Hey
So I have an HP Pavilion dv6-2190us, to be exact, with an i7.

temperature is of particular concern to me because it seems to run hot anyway...50-60 when I'm not doing anything too stressful, and it goes up to the early 80s when I'm doing something more stressful, like converting videos, which I do a lot of.  It's been known to get up into the high 80s on occasion as well.

anyway, I've had no issues with cpu temperature monitoring in Windows, but in Ubuntu, lm-sensors seems to be the way to go.  I can get it to detect my graphics chip sensors, but it doesn't see the cpu sensors at all. I've seen other people who have the same issue, other people who seem to have gotten it working with no issues whatsoever, and other people who've had the issue but it was resolved when they compiled lm-sensors from source. I tried compiling from source but wasn't able to.  I thought I got the dependencies, and was able to make, but when I try to make install, I get:
collect2: ld returned 1 exit status
make: *** [prog/sensors/sensors] Error 1

any help would be appreciated, whether it's helping me get lm-sensors working or pointing me in the direction of another sensor monitor.

Thanks

---

### Post by gupti on 2010-10-29
I'm pretty new to ubuntu (1 year), but have you tried "xsensors" from the software center? It gives me the temperature of my computer and gathers information from Im_Sensors, so it might work.

---

### Post by efflandt on 2010-10-29
If you just use the lm-sensors installed by default (but which Ubuntu version) does **sudo sensors-detect** come up empty?  For my i5 it found:

```
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0xa10, driver `it87')
```But I don't know what to make of that because once I go through that and set it up, the **sensors** command comes up with this:

```
it8720-isa-0a10
Adapter: ISA adapter
in0:         +0.91 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +2.14 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.14 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.12 V
fan1:        896 RPM  (min =    0 RPM)
fan2:        922 RPM  (min =    0 RPM)
temp1:      +127.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +22.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:       -84.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +0.000 V
```Notice that temp1 is at the high end of the scale (does not change), so that may be meaningless.  Not sure if temp2 is ambient temperature, because I have not seen that change (actual room temperature has not changed either from 18°C).  Even though temp3 says "disabled" and is below the bottom of the scale, it goes up (to -60.0°C) under load, so it might have wrong offset.  Maybe temp3 is like a count down, if it reaches zero, your CPU goes up in smoke.

Actually it would shut down before it would burn up.

---

