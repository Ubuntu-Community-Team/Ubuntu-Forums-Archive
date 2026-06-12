---
title: "pwmconfig problem"
date: 2009-11-01
forum: Hardware
---

### Post by catchman on 2009-11-01
Hello, 
I have HP pavilion laptop and I can't get the fancontrol working. When I run fancontrol I get this error:

[I]Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
[/I]

I tried to run pwmconfig to create /etc/fancontrol but I end with the error too: 

*usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed*

I have lm-sensors installed and configured using *sensors-detect*. This is output from *sensors* command:
[I]acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (high = +100.0°C, crit = +100.0°C)  
[/I]

In the /etc/modules I have only these two modules:
[I]lp
coretemp[/I] (added by *sensors-detect*)
I have Intel Core2Duo T7200 on Mobile945 PM Chipset. Using Ubuntu 9.04 32b with kernel 2.6.28-16-generic.
The cpu fan is really noisy and I couldn't found anything that works for me in the web.

Thanks for any help.

---

