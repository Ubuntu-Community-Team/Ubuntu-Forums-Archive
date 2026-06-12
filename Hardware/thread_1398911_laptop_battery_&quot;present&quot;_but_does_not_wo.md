---
title: "laptop battery &quot;present&quot; but does not work"
date: 2010-02-05
forum: Hardware
---

### Post by sarthorks on 2010-02-05
Hi, today all of a sudden, when I tried powering on my laptop, it did not turn on. It still had like 60% battery left from last charging. Only when i plugged to AC could it turn on. However, the "battery" indicator, for the first time ever, did not light up. When I logged in, and unplugged AC power, the computer just turned OFF. 
I use hardy, but i tried the same on karmic through live usb.


Here are some of the outputs.
```
~$ dmesg | grep BAT
[   48.090948] ACPI: Battery Slot [BAT1] (battery present)

```

```

:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         5100 mAh
last full capacity:      5100 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3465U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                COMPAL 

```
```

~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4692 mAh
present voltage:         11100 mV

```

So it seems that the battery is still present, but its not working at all.  I tried searching on the net, but could not find anything constructive. Can anyone help me fix this? Is my battery dead or not? Why is it still "present" then?

I will paste any other output which is asked. Thanks in advance.

---

### Post by IcarusR on 2010-02-05
How old is the battery? they do not last for ever.
Try charging, leave plugged in with laptop switched off overnight & see what happens.
Some folk say putting battery in freezer for a while helps to revive dodgy batteries, not tried it myself.

---

### Post by sarthorks on 2010-02-05
> **IcarusR said:**
> How old is the battery? they do not last for ever.
Try charging, leave plugged in with laptop switched off overnight & see what happens.
Some folk say putting battery in freezer for a while helps to revive dodgy batteries, not tried it myself.

The laptop is one and a half years old, and the current battery backup was roughly one hour.

---

