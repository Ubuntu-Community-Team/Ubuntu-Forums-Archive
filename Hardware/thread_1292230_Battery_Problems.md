---
title: "Battery Problems"
date: 2009-10-15
forum: Hardware
---

### Post by Xidena on 2009-10-15
I just bought a new 8800 mAh battery for my VAIO PCG-7N2L laptop, but it's not recognized by ubuntu and won't boot while the battery is actually attached. I had to replace it because the 4800mAh battery crapped out on me.

acpi 1 returns

```
Battery 1: discharging, 100%, rate information unavailable.
```

cat /proc/ACPI/battery/BAT0/info returns

```
present:                 yes
design capacity:         655350 mWh
last full capacity:      655350 mWh
battery technology:      non-rechargeable
design voltage:          655350 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:
serial number:
battery type:            LiOn
OEM info:                Sony Corp.
```

cat /proc/acpi/battery/BAT0/state returns

```
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      655350 mWh
present voltage:         unknown
```

uname -a returns

```
Linux laptop 2.6.24-24-generic #1 SMP Fri Sep 18 16:49:39 UTC 2009 i686 
GNU/Linux
```

---

### Post by Xidena on 2009-10-16
This is kinda annoying, and I don't know what to do. I can't seem to find any resources that are actually useful in regard to resetting the battery's metering or that it won't boot with the battery actually attached. When I try to power it on, the light stays on only as long as I hold it, but it doesn't actually POST or do anything.

---

