---
title: "HP Spectre 13 Skylake 17.04 no fan, help!"
date: 2017-09-23
forum: Hardware
---

### Post by joseff on 2017-09-23
Hi guys,

I'm a longtime Ubuntu user, although by no means an expert. 
I just got this Spectre 13 2016 (skylake) i7, and installed Ubuntu GNOME 17.04 on it. Everything works, except the fan.  It's usually very loud under Win10, so I'm sure it's not working.
Anyway, here is the output of sensors:

```

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +44.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +42.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +42.0°C  (high = +100.0°C, crit = +100.0°C)

acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)
temp3:        +10.0°C  

iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +34.0°C  

pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +43.5°C  

```

I've tried searching the web for this and found no clue so far. Can anyone help?

---

### Post by meijer.o on 2017-09-23
Dear Linux user,

That the fan is not listed in the output does not mean that it does not work. It should start working at about 45-50 0°C. Try e.g. a webpage earth.google.com which needs more system resources. Than it will probably kick in.



Best regards.

---

### Post by joseff on 2017-09-24
Nope, it definitely did not work.  Ran the CPU as high as 60+C and still no fan.  It throttles down instead.
Anyhow, I've gone through the BIOS settings, and enabled "fan always on" mode.  Apparently there's no way to control the fan via OS on ubuntu.

---

### Post by joseff on 2017-09-29
Bump... any hints, anyone?  The "fan always on" BIOS setting runs the fan at one constant speed, so it's still not ideal.

---

