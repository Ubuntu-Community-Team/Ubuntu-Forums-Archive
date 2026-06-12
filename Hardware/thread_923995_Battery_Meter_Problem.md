---
title: "Battery Meter Problem"
date: 2008-09-19
forum: Hardware
---

### Post by Eberbachl on 2008-09-19
Hi Everyone - just wondered if anyone might be able to help.

I have Hardy 8.04 (AMD64) installed on my Macbook. Installed it last week, and everything is running great after installing some wireless drivers.

Problem is that the battery meter was working fine until the other day, and now it's just stopped dead.

It reads 0% remaining at all times regardless of whether I'm running on battery power, or charging.

Just as an FYI - the output of:

```
cat /proc/acpi/battery/*/*
```

...is:

> alarm:                   unsupported
present:                 yes
design capacity:         0 mWh
last full capacity:      0 mWh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            
OEM info:                
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         0 mV


I have tried re-installing gnome-power-manager, but it doesn't seem to help.

Any ideas?

Please :D

---

### Post by kaivar on 2008-09-19
looks like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215074](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215074)

:D

---

### Post by Eberbachl on 2008-09-25
That would be the same problem ;)

Thanks for the link.

---

