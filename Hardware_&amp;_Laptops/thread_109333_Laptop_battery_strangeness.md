---
title: "Laptop battery strangeness"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by Quirky on 2005-12-28
Occasionally my battery lasts 45 minutes. For a P4 with wireless, this is reasonable. Most of the time though, it lasts just a few minutes - around 6 or 7 - despite being reported as 100% charged.

Some statistics:
```

$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4000 mWh
last full capacity:      1157 mWh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 115 mWh
design capacity low:     57 mWh
capacity granularity 1:  120 mWh
capacity granularity 2:  8 mWh
model number:            755
serial number:           001
battery type:            LiON
OEM info:                OEM

```

Note the design and last full capacity values. What's that all about?

And if I watch /proc/acpi/battery/BAT0/state then I see a jump from ~1000mWh to just 80 or so - coupled with the predictable jump from 80% battery to just 7% and a warning message. Broken battery? The laptop is less than a year old, so I'd be disappointed if it was knackered already - the occasional hour's worth of life gives me hope that it is just a glitch somewhere. If I plug in the AC supply after reaching low charge, it appears to charge correctly.

---

### Post by Unicast on 2005-12-28
Don't know how true this is, but I was told that leaving your battery connected whilst using the mains power for extended periods of time can dramatically reduce the life of the battery.

---

### Post by Quirky on 2005-12-28
That's what I was afraid of, but apparently most new laptops don't try and keep charging the battery once it is full. The question is: who decides when a battery is full? Is it the OS? Or is it something in the hardware? To me, it looks like the battery says "I'm full! Stop charging!" before it really is full.

Update: Well, when the battery reached 0% it kept going for about 15 minutes more before really running out. I get the feeling the battery is on its last legs, which is really crap after only 10 months use. If I can bring myself to do it, I'll try booting Windows to see what happens.

---

