---
title: "New battery - less mAh"
date: 2011-07-11
forum: Hardware
---

### Post by sakishrist on 2011-07-11
Hello everyone,

I am having a problem with my new battery. It arrived today.

I followed the instructions and fully charged and discharged the battery 3 times (actually, now I am at the 3rd discharge), but the maximum mAh is lower than what it should be.

Here is the "cat info" output:```
/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         8800 mAh
last full capacity:      8608 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 437 mAh
design capacity low:     263 mAh
cycle count:          0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:           Bad
battery type:            LION
OEM info:                Hewlett-Packard

```I would like to ask whether this is normal.

Also, the voltage is 11.1V as I can see, but the laptop original battery was 10.8 (and they sold me this one as being 10.8V). Will that be a problem? Moreover, when fully charged, under "power statistics" -> "details" -> "voltage" it reads about 12.7V ... Should I be worried? (I am)

Thanks in advance!!!

PS: I noticed that in the power statistics, under the details tab it now reads Lithium Ion but earlier today I am 99.9% sure I saw it reading ... Nickel something (I am not exactly sure which type it was). Thanks again.

---

### Post by sakishrist on 2011-07-12
Bump


Please help me [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

Now it shows more than the normal:```
/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         8800 mAh
last full capacity:      9024 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 457 mAh
design capacity low:     275 mAh
cycle count:          0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:           Bad
battery type:            LION
OEM info:                Hewlett-Packard

```

Is something wrong with the battery?

---

### Post by sakishrist on 2011-07-12
Hi again!

The battery type just "changed" again, and the mAh too:
```
/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         8800 mAh
last full capacity:      8768 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 442 mAh
design capacity low:     266 mAh
cycle count:          0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            NiMH
OEM info:                Hewlett-Packard

```

I really hope that someone will be able to help me. I just need to know whether this is normal or whether I should return the battery.

Thanks again

---

### Post by sakishrist on 2011-07-12
Bump

Please help me ... should I return this battery or is this normal? [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by psusi on 2011-07-12
Everything is perfectly normal.  Go on about your normal work and enjoy the new battery.

---

### Post by sakishrist on 2011-07-12
Thanks a million!

---

