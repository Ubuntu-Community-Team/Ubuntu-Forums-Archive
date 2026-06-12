---
title: "Peculiar problem with laptop battery...."
date: 2008-10-13
forum: Hardware
---

### Post by palamon00000 on 2008-10-13
I have a very bizarre problem with my Dell Inspiron, running Kubuntu 8.04 (but probably not limited to that).  Seems like the system is thinking it's attached to an excessively large battery:

```
cat /proc/acpi/battery/BAT0/*

alarm:                   720 mAh
present:                 yes
design capacity:         7200 mAh
**last full capacity:      64933 mAh**
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL U48735
serial number:           11124
battery type:            LION
OEM info:                Samsung SDI
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      3370 mAh
present voltage:         12437 mV

```

Any ideas, aside from prayer (or a new laptop)?  As it is, the battery is old but it seems to be in relatively good shape, even if it is at half capacity.  I tried to discharge the battery completely and then fully recharge it, but that did nothing.  Can the "last full capacity" value be manually set perhaps?

I'm also guessing that this is a problem with the BIOS, but it did happen soon after the most recent kernel update.  Haven't seen any other posts or reports about this problem, though, so I think that it might just be my own messed up little machine.

---

