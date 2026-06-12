---
title: "laptop battery capacity HUGELY depleted"
date: 2010-03-04
forum: Hardware
---

### Post by paulvbrown on 2010-03-04
Hi all -- in the process of wading thru other battery issues here, but as my initial searches haven't come across anything similar, I'll go ahead and post in the hopes someone can help if further searching doesn't come up with anything....

As you can see from the following, my battery is *designed* to have 6000 mAh capacity, but currently (and this "just happened" as a huge, sudden drop one day afaik) "FULL" means a whopping 160mAh.

```
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      160 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 12 mAh
design capacity low:     8 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      160 mAh
present voltage:         12530 mV

$ acpi -V
     Battery 1: charging, 100%, rate information unavailable.
     Thermal 1: ok, 34.0 degrees C
  AC Adapter 1: on-line
```

I took the charger out for about 1-2 minutes, and got the following:

```
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      96 mAh
present voltage:         12083 mV


$ acpi -V
     Battery 1: discharging, 80%, rate information unavailable.
     Thermal 1: ok, 34.0 degrees C
  AC Adapter 1: off-line


```

I can think of nothing that I've done physically or software-wise, that would have caused this.  I'm still running Hardy, and my laptop is an HP Pavilion dv6000.  I update regularly.  (BTW, for someone like me that can't ever remember what version I've got running (hopeless, I know) is there an easier way to check than to cat /etc/apt/sources.list to see what that says?  Something like 'uname' that would return something a bit more helpful than "Linux" =o) )

ONE thing that I *can* think of that happened recently was that my adapter went missing, and I used another one from work (which I've used before), but that should have the same spex as the one I have, although it's not as heavy as my own.

Any ideas?  Happy to provide more info on my system...

TIA!

---

