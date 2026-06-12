---
title: "Laptop's fan does not work properly"
date: 2020-10-18
forum: Hardware
---

### Post by flavio05 on 2020-10-18
Hello, everyone.

My laptop's fan does not work properly anymore. When I press power on it starts normally, but when the login page comes, it reduces abruptly and does not speed up, even when I am doing some heavy task. The temperature keeps rising, and it keeps almost stopped.
It's always noticeable when it spins normally, but now the only way to notice is pressing the laptop and feeling that something is vibrating really really weakly.

I noticed that in part of the last update from Software Updater there was a component called thermald, and looking for something about it, I learned that its function is avoid the overheating. But this fan won't spin anymore?? Haha
Some hours of using, the laptop is necessarily hot, and fan keeps almost stopped.

Is someone with the same problem?
Thanks

---
$ sensors
BAT0-acpi-0
Adapter: ACPI interface
in0:          12.17 V  
curr1:         0.00 A  


coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +59.0°C  (high = +105.0°C, crit = +105.0°C)
Core 0:        +57.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:        +57.0°C  (high = +105.0°C, crit = +105.0°C)


acpitz-acpi-0
Adapter: ACPI interface
temp1:        +27.8°C  (crit = +105.0°C)
temp2:        +29.8°C  (crit = +105.0°C)

---
Laptop Hewlett Packard 
Ubuntu 20.04.1 LTS 64bit
Intel(R) Core(TM) i3-5005U CPU @ 2.00GHz

---
$ thermald --version
1.9.1

---

