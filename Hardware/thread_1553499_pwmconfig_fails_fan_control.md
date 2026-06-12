---
title: "pwmconfig fails: fan control"
date: 2010-08-15
forum: Hardware
---

### Post by Pifilatakanemu on 2010-08-15
Hey there,
I have a Dell Inspiron 6400 with an Intel Dual Core @ 1,6Ghz and pwmconfig fails to grab the necessary informations:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```This is the sensors output:
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +50.5°C  (crit = +126.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +43.0°C  (crit = +85.0°C) 
```I only found a thread in the archive on pwmconfig I couldn't anser any more.

Any suggestions on how to get it to work?

Thanks!

---

### Post by Yellow Pasque on 2010-08-15
pwmconfig is more for desktops. Laptops usually use ACPI to control the fan.

---

