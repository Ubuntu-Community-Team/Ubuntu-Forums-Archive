---
title: "Asus 1018P fan is always running"
date: 2011-09-13
forum: Hardware
---

### Post by gofurygo on 2011-09-13
Hello

I have an annoying problem with my ASUS Eeepc1018p. The fan is on and running all the time, no matter if I'm online, or its sitting there in idle mode.

I followed those 2 tutorials:
[http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu)
Output at the end is:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +67.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53.0°C  (crit = +100.0°C)

From my understanding, I "cant" control the fanspeed... right?

pwmconfig gives me this:
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

and fancontrol gives me this:
Loading configuration from /etc/fancontrol ...
Some mandatory settings missing, please check your config file!

Any ideas everybody?

Thanks for your help in advance ;-)

Fury

---

