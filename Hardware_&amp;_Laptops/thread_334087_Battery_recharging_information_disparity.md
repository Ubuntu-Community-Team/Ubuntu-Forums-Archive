---
title: "Battery recharging information disparity"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by Tiede on 2007-01-08
Ok... just poking around on my laptop, I took a gander at /proc/acpi/battery/BAT1/info and found this:
```
battery@ubuntumachine:~$ less /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         2000 mAh
last full capacity:      917 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 200 mAh
design capacity low:     36 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            12ZL
serial number:           4152
battery type:            LION
OEM info:                SONY
/proc/acpi/battery/BAT1/info (END) 

```
Noticicing that disparity between the design capacity and the last full capacity seem quite huge, I was wondering if this is sign of a problem?
The laptop is an Acer Aspire 3003WLCi.

---

### Post by tweedledee on 2007-01-09
> **Tiede said:**
> Noticicing that disparity between the design capacity and the last full capacity seem quite huge, I was wondering if this is sign of a problem?
The laptop is an Acer Aspire 3003WLCi.

I don't think so.  I have noticed that I don't get particularly accurate readings on battery capacity except when it is nearly full or nearly empty (e.g., I go from 40% to 3% capacity in much less time than from 45% to 40% when discharging).  But frankly I never got very good estimates in Windows, either.

---

