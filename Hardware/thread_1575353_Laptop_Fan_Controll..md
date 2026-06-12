---
title: "Laptop Fan Controll."
date: 2010-09-15
forum: Hardware
---

### Post by skjoldfetter on 2010-09-15
Hello, i have a bit of a problem.

I have a Packard Bell Easynote TR-87. and in Ubuntu the fans simply will not turn on.

In windows the fans work fine.

However in Ubuntu it has shut down due to reaching critical temp (90 Celsius) more than once. (running wow in wine, with the laptop on top of two books to help airflow under it).

I've looked at it a bit, and sensors tells me:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.0°C  (crit = +90.0°C)                  
temp2:       +59.0°C  (crit = +90.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +90.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +90.0°C, crit = +90.0°C) 

which i basically read as: fans go on at 90 C, and the computer shuts down at 90 C.

is there a way to change this?

also, the 55-60 degrees there are with nothing but firefox and the terminal running.


EDIT: got one of the fans to run (no clue how), so i have some airflow now, however, when i opened up two wow windows to test it it spiked to 80+ degrees.

so still not exactly solved...

matthias@borgnode1:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +84.0°C  (crit = +90.0°C)                  
temp2:       +84.0°C  (crit = +90.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +85.0°C  (high = +90.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +81.0°C  (high = +90.0°C, crit = +90.0°C)

---

### Post by skjoldfetter on 2010-09-19
bump :)

---

### Post by skjoldfetter on 2010-09-20
Bump :(
Making me sad with no responses!

doesn't anyone here know stuff about fan controll? :P

---

