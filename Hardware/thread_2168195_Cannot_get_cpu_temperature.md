---
title: "Cannot get cpu temperature"
date: 2013-08-16
forum: Hardware
---

### Post by jca2323 on 2013-08-16
The cpu: AMD APU 5600K
The os: Ubuntu 13.04
Hi,

I've been trying to get the cpu temperature using lm-sensors and psensor. I have had no luck. Here's what I get:
it8728-isa-0228
Adapter: ISA adapter
in0:          +0.92 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.00 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.31 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.19 V  
fan1:        1950 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1757 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -7.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor  (I don't believe my computer is running at -7.0 degrees Celsius.
temp3:        +14.0°C  (low  =  +0.0°C, high = +70.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.5°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

AND BEFORE YOU ASK:
I did run sensors-detect.

---

### Post by QIII on 2013-08-16
Hello!

It's not obvious, but k10temp is the sensor that returns temps on recent AMD processors.  But that is definitely a wonky reading.

Cheers!

---

### Post by jca2323 on 2013-08-16
I doubt my cpu is running at 0.5 degrees Celsius. Something isn't working. EDIT: It appears the the bios is reporting different temperatures, although 65 degrees celsius is high. EDIT 2: k10temp-pci-00c3 is now reporting temp1:        +32.9°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)
I guess it fixed itself.

---

### Post by QIII on 2013-08-16
You could give rebooting a try and look at it again.

There are two possibilities:

1.  lm-sensors does not handle APUs well (which would surprise me).

2.  There is a sensor fault on the motherboard.

I don't have the time to look right now, but you might want to have a look at Launchpad to see if this has been reported as a bug.

---

### Post by QIII on 2013-08-16
> **jca2323 said:**
> ...although 65 degrees celsius is high.

APUs run hotter, since they also have the GPU on-die.  But that does seem a bit much if that is happening at idle.

---

### Post by jca2323 on 2013-08-16
I edited my second post: It seems to be providing a reasonable temperature now! Thanks!

---

### Post by QIII on 2013-08-16
Looks like you might need a can of computer gremlin repellant!  :)

---

