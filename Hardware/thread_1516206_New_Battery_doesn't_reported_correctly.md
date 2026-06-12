---
title: "New Battery doesn't reported correctly"
date: 2010-06-23
forum: Hardware
---

### Post by Inglor on 2010-06-23
Hi all,

I installed Lucid on an old laptop.
The laptop is an Acer Travelmate 3200 series
More specific: Acer Travelmate 3201XMi

After some year I decided to get a new battery since I found cheap ones on ebay.
I got a new one with a designed capacity of: 7200mAh
The actual information from ACPI within linux are:
```
cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            327 mA
remaining capacity:      6900 mAh
present voltage:         12597 mV
inglor@selene:~$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         7200 mAh
last full capacity:      7026 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: unknown
design capacity low:     unknown
capacity granularity 1:  unknown
capacity granularity 2:  unknown
model number:            05ZA
serial number:           32035
battery type:            LION
OEM info:                SANYO
```

The problem is that the panel on gnome-desktop doesn't display the information I read from console through acpi.
It doesn't NOT get updated unless I plug in or out of the power adapter.

I noticed though that the information is updated once I run:
```
 cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            290 mA
remaining capacity:      6918 mAh
present voltage:         12600 mV
```

I was wondering how the gnome-power-manager is reading the battery percentage and if possible to access it from acpi.

On another secondary issue I would like to know how to reset the profile of the gnome-power-manager since it has the statistics from the old (broken) battery.

Any ideas/help would be great.

---

