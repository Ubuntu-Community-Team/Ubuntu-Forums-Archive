---
title: "acpi does not detect charging rate"
date: 2009-01-03
forum: Hardware
---

### Post by doppiaemme on 2009-01-03
Hi,
I installed kubuntu 8.10 (kernel 2.6.27-9 with backports modules) on a Hp Pavillion dv2850el (the BIOS is uptodate ...). Both kpowersave and power-guidance are non able to show how much time is needed to completely  (un)charge the battery. I think the problem is kernel-related:

zipozapo@zipolinux:/sys$ acpi -b
     Battery 0: Charging, 93%, charging at zero rate - will never fully charge

zipozapo@zipolinux:/sys$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      4089 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 200 mAh
design capacity low:     140 mAh
capacity granularity 1:  60 mAh
capacity granularity 2:  3889 mAh
model number:            VE06047
serial number:           15888
battery type:            LION
OEM info:                DP-SDI44
zipozapo@zipolinux:/sys$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mA ------------------------>HERE THE PROBLEM
remaining capacity:      3818 mAh
present voltage:         12554 mV

Thanks
MM

---

