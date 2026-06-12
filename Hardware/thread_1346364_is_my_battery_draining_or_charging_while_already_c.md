---
title: "is my battery draining or charging while already charged?"
date: 2009-12-05
forum: Hardware
---

### Post by vajorie on 2009-12-05
edit: the below output is when laptop is on AC. 

I don't really understand this stuff, but I'm already having troubles with my battery (brand new battery is missing 300mAh)... so I thought I should ask: is my battery draining (or, charging) while already charged?

```

$ cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged <-------
present rate:            773 mA  <------- ??
remaining capacity:      5500 mAh
present voltage:         12430 mV

```

```

$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         5800 mAh
last full capacity:      5500 mAh  <---- my other problem (laptop is new), ignore if unrelated
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 290 mAh
design capacity low:     174 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            UM08B52
serial number:           
battery type:            Lion
OEM info:                PANASONIC 

```

what do you think?

---

### Post by wilee-nilee on 2009-12-05
I have an acer aspire and it has a slow draw when off and unplugged you might check on the web if this is the case with whatever model of computer your using.

---

### Post by vajorie on 2009-12-05
> **wilee-nilee said:**
> I have an acer aspire and it has a slow draw when off and unplugged you might check on the web if this is the case with whatever model of computer your using.

ehm, acer aspire one :) so you're saying that the battery, in this case, is draining (in addition to the "draining while turned off" problem you mentioned) while also charging / on AC?

---

### Post by wilee-nilee on 2009-12-05
> **vajorie said:**
> ehm, acer aspire one :) so you're saying that the battery, in this case, is draining (in addition to the "draining while turned off" problem you mentioned) while also charging?

Your cat posts read pretty much like mine I don't think it is draining while plugged in to ac but others will have a better read on the outputs.

---

### Post by jmate24 on 2009-12-05
the maximum is its the tolerance, its highest capacity.
the lower number just means that it is full. as your battery ages as you use it (over months to years) that lower number will drop. one way to fix it is to go into the bios and do a battery calibration.

jmate24--  :D

---

