---
title: "HP Pavilion dv6000 Battery not charging in 10.04"
date: 2010-12-11
forum: Hardware
---

### Post by Alan McNea on 2010-12-11
I just upgraded my OS from 8.04 to 10.04 and my battery will no longer charge.  The battery indicator applet shows full charge at 0%.  Under 8.04 as of 6 hours ago the battery charged just fine.  Also, I have tried it using 2 different batteries, so, the battery itself should be fine.

Here are some outputs:
--------------------------
--BATTERY 1---------------
--------------------------
cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         6000 mAh
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     150 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         0 mV

acpi -V
Battery 0: Unknown, 0%, rate information unavailable
Battery 0: design capacity 6000 mAh, last full capacity -60 mAh = -1%


--------------------------
--BATTERY 2---------------
--------------------------
cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         6000 mAh
last full capacity:      3168 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 162 mAh
design capacity low:     98 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         11229 mV

acpi -V
Battery 0: Unknown, 0%, rate information unavailable
Battery 0: design capacity 6000 mAh, last full capacity 3168 mAh = 52%
-----------------------------------------------------------

Battery 2 was the battery inserted when the OS was installed.  And judging from the "last full capacity", my guess is the battery discharged after that point in time.

Any help you can shine on this would be appreciated.

---

### Post by Alan McNea on 2010-12-11
Basically, this was my friends laptop which I was updating the OS for them.  Anyways, apparently there is button on the power brick which you must press else the battery doesn't charge.  Something to do with running on airplanes.

---

