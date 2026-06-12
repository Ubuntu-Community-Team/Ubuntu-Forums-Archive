---
title: "Battery warning low power."
date: 2012-02-10
forum: Hardware
---

### Post by RikardSvenningsen on 2012-02-10
I have been using Ubuntu sins version 5.xx on several different Dell Laptops, the last well working Ubuntu was 10.10 ever sins I got trouble with battery warnings.
The problem is, when I open my laptop and login i got a warning that battery is low, after a 5 to 20 sec. it close.
If i try to open my computer several times in a rope i can get lucky to get in. Usually I plug in power login and remove power then no problem.
The laptop is Dell D630.

cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         7800 mAh
last full capacity:      6948 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 780 mAh
design capacity low:     236 mAh
cycle count:		  0
capacity granularity 1:  78 mAh
capacity granularity 2:  78 mAh
model number:            DELL DU1399
serial number:           767
battery type:            LION
OEM info:                SMP

cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1549 mA
remaining capacity:      4848 mAh
present voltage:         11605 mV

---

