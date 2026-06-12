---
title: "problem with the output of 'sensors'"
date: 2008-09-28
forum: Hardware
---

### Post by electronique on 2008-09-28
hello,

typing the command
cat /proc/acpi/thermal_zone/THRM/temperature 
in the terminal usually gives a temperature higher than 50 c .
I thought something was wrong with my fan.

so I wanted to configure my fan speed using the post
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

but the output of sensors gives me only:


coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (crit = +85.0°C)

....in contrast to the information that the author of the post got.
Please help me.
I am using a acer5920g
1.83GHz core2duo
ubuntu 8.04 64bit.

And could any body tell me how to highlight code while posting into forum?

EDIT:
the above mentioned post directs me to first go to
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
which asks me to go to line no 68 of /usr/sbin/pwmconfig
and replace 

-------------------------
        MATCH='*/fan[1-9]_pwm'
else
        MATCH='*/pwm[1-9]'
---------------------------

with

-------------------
       MATCH='*/pwm[1-9]'
else
        MATCH='*/fan[1-9]_pwm'
----------------------

But there is no such code at line no. 68 of that file.

---

### Post by electronique on 2008-09-29
bump
reply please...

---

### Post by electronique on 2008-09-29
bump

reply please

---

