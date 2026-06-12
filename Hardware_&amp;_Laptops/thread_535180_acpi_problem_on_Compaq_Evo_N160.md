---
title: "acpi problem on Compaq Evo N160"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by omerlh on 2007-08-26
Hello!
I have a problem with acpi. I have the 2.6.20-16-generic kernel. The probelm is that the acpi didn't "read" the status of the battery of my laptop:
acpi -V:
```

    Thermal 1: ok, 55.0 degrees C
  AC Adapter 1: off-line

```
There is no battery here (as should to be). Weird.
I tried to search and found a bag in ubuntu when upgrading from 2.6.20-15 to 2.6.20-16, but I checked and the same problem is also in the 2.6.20-15.
I run some checks:
vi /proc/acpi/battery/CMB0/status:
```

present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1345 mW
remaining capacity:      2764 mWh
present voltage:         16743 mV

```
vi /proc/acpi/battery/CMB0/info:
```

present:                 yes
design capacity:         unknown
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          unknown
design capacity warning: 800 mWh
design capacity low:     16 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            BAT1
serial number:           0000
battery type:            LION
OEM info:                COMPAQ

```
acpi -v:
```

acpi 0.09

Copyright (C) 2001 Grahame Bowland.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```
I checked in the acpi site and the newst version is 2.6.16-rc1.
it looks like acpi "recognize" the battery but has problems read it. I checked and also the Power Manger and the KDE battery program also can't "read" the battery status.
What can be the problem?
omerlh.

---

### Post by msak007 on 2007-10-27
Any updates on this or have you found any info to make it work? I put Kubuntu on my sister's Evo N160 with the same battery, and I get the same exact results. The guidance power manager doesn't detect the battery or the CPU's frequency on this machine. I just upgraded it to Gutsy today and it's still exhibiting the same problems with kernel 2.6.22-14-generic.

acpi -V
>      Thermal 1: ok, 56.0 degrees C
  AC Adapter 1: on-info:> 
present:                 yes
design capacity:         unknown
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          unknown
design capacity warning: 800 mWh
design capacity low:     16 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            BAT1
serial number:           0000
battery type:            LION
OEM info:                COMPAQstate:> 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1058 mW
remaining capacity:      1778 mWh
present voltage:         15113 mV

---

