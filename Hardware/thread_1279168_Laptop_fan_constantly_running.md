---
title: "Laptop fan constantly running"
date: 2009-09-30
forum: Hardware
---

### Post by jeneverboy on 2009-09-30
Hi

When I am running UBUNTU on my laptop my fan is making a lot of noise. This happens most of the time after 30 min. When running Vista this is not the case.

Does anyone know how I can see what my fan is doing??

Or does anyone known if the program Dellfand is any good?

It seems that I am not the only one with this problems ( I googled a bit).

Bye

---

### Post by Juno Eclipse on 2009-11-15
I have the same problem with my L505 Toshiba laptop. So far, I haven't found anything to solve this. It's ACPI related. See [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578)

---

### Post by aldeby on 2009-11-15
Have a look at **System->Administration->System Monitor -> Processes tab** and check whether a process is intensively using the CPU. Most of the times is *tracker* (the file indexer search tool) fault. If you see a process using 50% or more of the CPU try killing it (rightclick...)

You can also install lm-sensors to read the CPU temperature 
(type everything follows in a terminal)
```
sudo apt-get install lm-sensors
```
the detect your sensors
```
sudo sensors-detect
```
and after reboot simply type
```
sensors
```
and you will get an output like this one:```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +100.0°C, crit = +100.0°C
```

If your fan still behaves in a crazy way you should check your dmsg and system logs whether your system has problems loading some module drivers.

---

