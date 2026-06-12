---
title: "THM0 reports 128C, but nothing else does"
date: 2009-05-07
forum: Hardware
---

### Post by jkao on 2009-05-07
So I have a Thinkpad X61s running Hardy 8.10 64-bit. I've encountered some oddities with the ACPI temperature warnings and was wondering if anyone had encountered these.

Initially, my computer would suddenly shut down randomly, usually when i was doing something CPU intensive but sometimes when it was idle. After rebooting, the kernel error log would show a line like:

```
[ 2566.807455] ACPI: Critical trip point
```

Whoa! Looking at THM0, it seemed like something in my computer was burning up:

```
root@plant:~# cat /proc/acpi/thermal_zone/THM0/temperature 
temperature:             128 C

```

But oddly enough, my thinkpad bios controlled fan wasn't spinning like mad.

So then I checked a few more things:

THM1 seemed okay:
```
root@plant:~# cat /proc/acpi/thermal_zone/THM1/temperature 
temperature:             54 C

```

The IBM Thinkpad ACPI thermal didn't show anything at 128 C:
```
root@plant:/# cat /proc/acpi/ibm/thermal 
temperatures:	52 48 48 48 35 -128 33 -128 47 47 -128 -128 -128 -128 -128 -128

```

sensors output seemed to indicate that on acpitz-virtual-0, temp1 mapped to THM0 and temp2 mapped to THM1. The temperature on temp2 seems to match Core 0, but no other sensor shows anything close to 128 C:
```

root@plant:/# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:      +128.0°C  (crit = +127.0°C)                  
temp2:       +53.0°C  (crit = +100.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3870 RPM
temp1:       +52.0°C                                    
temp2:       +48.0°C                                    
temp3:       +48.0°C                                    
temp4:       +48.0°C                                    
temp5:       +35.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +33.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +48.0°C                                    
temp10:      +47.0°C                                    
ERROR: Can't get value of subfeature temp11_input: Can't read
temp11:       +0.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +51.0°C  (high = +100.0°C, crit = +100.0°C)  

```

So, I googled around, and ended up disabling the trip_points on THM0. Now, at least, my computer doesn't reboot, but I'm a little concerned.

I'm still getting a nonstop stream of errors in dmesg:
```

[ 3036.807336] ACPI: Critical trip point
[ 3041.822353] ACPI: Critical trip point
[ 3046.807385] ACPI: Critical trip point
[ 3051.807657] ACPI: Critical trip point
[ 3056.807533] ACPI: Critical trip point
[ 3061.822383] ACPI: Critical trip point
[ 3066.807789] ACPI: Critical trip point
[ 3071.807690] ACPI: Critical trip point
[ 3076.819080] ACPI: Critical trip point
[ 3081.807784] ACPI: Critical trip point
[ 3086.818903] ACPI: Critical trip point
[ 3091.818749] ACPI: Critical trip point
[ 3096.818757] ACPI: Critical trip point
[ 3101.807430] ACPI: Critical trip point
[ 3106.808246] ACPI: Critical trip point
[ 3111.818296] ACPI: Critical trip point
[ 3116.807241] ACPI: Critical trip point
[ 3121.807317] ACPI: Critical trip point
[ 3126.807616] ACPI: Critical trip point
[ 3131.822458] ACPI: Critical trip point
[ 3136.822509] ACPI: Critical trip point

```

Is my computer going to melt down? Has anyone encountered anything like this before?

Thanks!

---

### Post by rkoma on 2010-11-14
Have you found out the source of this problem? I have the same problem with R500, THM0 shows high temperature when there is high CPU load, while all other sensors are within normal range.

---

