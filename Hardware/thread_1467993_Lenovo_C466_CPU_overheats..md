---
title: "Lenovo C466 CPU overheats."
date: 2010-05-01
forum: Hardware
---

### Post by fqj1994 on 2010-05-01
LENOVO C466M LAPTOP
MAIN BOARD:IHL00
CPU:Intel(R) Pentium(R) Dual CPU T2330 @ 1.60GHz * 2(cores)
DISTRO:UBUNTU 10.04 LTS
LINUX KERNEL:2.6.32-21-generic i686
BIOS PROVIDER:LENOVO
BIOS VERSION:05CN36WW(V1.20)


The cpu overheats after working a while.

```

# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +76.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +70.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +70.0°C  (high = +100.0°C, crit = +100.0°C) 

```The fan seems down though there isn't any hardware error with the fan.
when the temp is over 90.0 centigrade degrade,the fan starts to work.When the temp decreases,the fan stop working again(It seems level0).
lm-sensors can not detect the fan.
And /proc/acpi/fan is empty.
```
# pwd
/proc/acpi/fan
# ls

```So how can i set the fan's level(control the fan's speed) mannualy or make Ubuntu more smart on controling the fan.

You should know it's neither thinkpad nor ideapad before answering this question.


Thanks.

---

