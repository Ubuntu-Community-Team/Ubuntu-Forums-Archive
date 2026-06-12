---
title: "Battery charging in BIOS but not while on Ubuntu"
date: 2010-06-03
forum: Hardware
---

### Post by puccio on 2010-06-03
Hi,

my battery does not charge (it remains on the same battery level) if I'm running Ubuntu.

If I shutdown the laptop (Dell Inspiron 6400 with brand new 9 cells battery) and I reboot entering the BIOS, from there the battery can be recharged.

Can someone help me understand what's going on?

Some perhaps useful infos:

```

cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         7800 mAh
last full capacity:      7683 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 780 mAh
design capacity low:     236 mAh
capacity granularity 1:  78 mAh
capacity granularity 2:  78 mAh
model number:             DELLJN1490
serial number:           949
battery type:            LION
OEM info:                Sanyo

```


```

cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      274 mAh
present voltage:         10934 mV

```

That "remaining capacity" does not increase..

Thank you in advance for any suggestion.

---

### Post by dino99 on 2010-06-03
[http://brainstorm.ubuntu.com/idea/19487/](http://brainstorm.ubuntu.com/idea/19487/)

---

### Post by puccio on 2010-06-03
Actually while running on battery says "battery charged", while it is not (if I unplug the AC adapter, it blinks in red because it is almost decharged).

I trid Fn+F3 (the battery icon is on that key on my laptop), but the only thing that happens is a popup message which simplys states what is already said by the battery applet (->"battery charged").

---

