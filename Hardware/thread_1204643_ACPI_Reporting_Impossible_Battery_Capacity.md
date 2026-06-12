---
title: "ACPI Reporting Impossible Battery Capacity"
date: 2009-07-05
forum: Hardware
---

### Post by dookehster on 2009-07-05
Hello,

I have an odd problem... here is the output of "cat /proc/acpi/battery/BAT1":

> 
present:                 yes
design capacity:         7800 mAh
last full capacity:      65414 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            DELLRD8506
serial number:           754
battery type:            LION
OEM info:                SIMPLO


Same thing except with state:
> 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      1812 mAh
present voltage:         12676 mV


As you can see, the value for "last full capacity:      65414 mAh" is literally impossible and currently the battery should be fully charged. It might be a faulty battery, it's quite abused... as you can see I only have 23% of my original capacity. 

My current kernel is 2.6.28-13-generic... I don't think old kernels had this kind of problem (but I will investigate). Opinions? Should I file a bug report?

---

### Post by hewart on 2009-07-05
Hi

I got a very damaged battery: lasts 5 minutes and used to last 5 hours :mad:

Here's a strange output of acpi -i

> sp@sp-laptop:~$ acpi -i
     Battery 1: Full, 92%
     Battery 1: design capacity 63360 mAh, last full capacity 631740 mAh = 100%
I never fixed this, still have the same issue on Jaunty. I think of recalibrating the battery, but the only software I know is for win.
Anyway it could be more a battery problem than a bug.

---

