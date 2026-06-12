---
title: "Battery not detected"
date: 2010-04-26
forum: Hardware
---

### Post by jlldn on 2010-04-26
I have a little problem. The Power Manager doesn't show battery info. I can plug, unplug, take off the battery and it still only shows the "usual" Desktop options. I'm running 10.04, but I already had this problem on Karmic. During install is the same thing, despite the predefined computer name includes the "-laptop". My guess is some problem in the Power Manager, since some times, when GUI is loading a window pop's up saying that the Power Manager can't be closed. :weird: 

In lshw I get:
```
$ lshw
WARNING: you should run this program as super-user.
jlldn-laptop            
    description: Computer
    width: 64 bits

```

and at the battery status:
```
$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      3182 mAh
present voltage:         12586 mV

```

---

### Post by Samzon on 2010-04-26
Can you give the specifications of your computer please? Sounds or looks like a very odd issue, possible bug.

---

### Post by jlldn on 2010-04-26
> **Samzon said:**
> Can you give the specifications of your computer please? Sounds or looks like a very odd issue, possible bug.

Hardware specifications?

The Laptop is an Acer Aspire 5630
Nvidia 7300
Core 2 Duo T5600
The OEM info of the battery is SANYO

---

### Post by jlldn on 2010-04-26
Well, I managed to fix it with a "sudo sensors-detect " (I guess it was this that fixed it). :popcorn:

---

