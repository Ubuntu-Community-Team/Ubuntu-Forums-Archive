---
title: "A serious problem."
date: 2008-09-21
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-21
Damn.


just ran sensors, look at what ive highlighted. 


jak@ubuntu:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.17 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.86 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.26 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +1.39 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.25 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.88 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.07 V
fan1:        950 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
[COLOR="Red"]temp1:      +127.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = transistor
temp2:      +127.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = transistor
[/COLOR]
temp3:       +22.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = thermal diode
cpu0_vid:   +1.269 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +23.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter



Is this a problem????
Core 1:      +23.0°C  (crit = +85.0°C)

---

### Post by -Zeus- on 2008-09-21
My guess is that it's just broken?  I mean, 127.0 would be the cap of a 7-bit integer, and if there was a data bit attached, that would make it one byte.  Is your computer crashing?

Please try to keep your threads together and not duplicate them.

---

### Post by Thyssenkrupp on 2008-09-21
sorry bout the threas thing...

umm no it doesnt crash at all, if it was brokenwhat problem will it cause?

---

### Post by -Zeus- on 2008-09-21
I think what I said is correct if it runs fine... if it was that hot it wouldn't be running i don't think!

---

