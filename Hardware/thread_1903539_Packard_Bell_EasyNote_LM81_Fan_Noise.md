---
title: "Packard Bell EasyNote LM81 Fan Noise"
date: 2012-01-02
forum: Hardware
---

### Post by vilwarin on 2012-01-02
Dear Forum,

My laptop (Packard Bell EasyNote LM81) is making a lot of noise all the time when running ubuntu, which is sad.
Now I tried some HowTos on the web (like for example this one: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)), but there are some things not working. E.g. 

```
pwmconfig
```
is returning
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Here is some more information:

```
sensors
```

is returning
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +59.0°C  (crit = +99.0°C)
temp2:        +59.0°C  (crit = +99.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +66.5°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +95.0°C)
```

I am running the latest ubuntu version: 11.10
Kernel: 3.0.0-14-generic-pae

The Laptop has two CPUs:
AMD Athlon(tm) II P320 Dual-Core Processor
Frequency: 800.000 MHz
Cache: 512 KB


The fan is running on full speed all the time. I'd loved to have a temperature dependent speed control. At least sensors seems to be able to query for the temperature, as well as the critical thresholds. But I don't know how to continue from here. 

Thanks in advance!

---

### Post by vilwarin on 2012-01-06
bump

---

### Post by adonet on 2013-02-26
> **vilwarin said:**
> bumpI am having the same kind of problem running Ubuntu 12.04.2. But in my case the fan isnt turning on at all (while in win 7 it is)

How to tunr on the fan on my Packard Bell Easynota AgroC

---

