---
title: "G-D-M says 100% charge but /proc/acpi says otherwise..."
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by organica on 2006-11-07
Hello,
The title should be "G-P-M says 100% charge but /proc/acpi says otherwise..."  Sorry folks!

I have an Acer Travelmate 4020.  Everything is working like a charm, even the custom keyboard.  

Problem is the gnome power manager icon says full charge and the battery stops charging.  However, running a #cat /proc/acpi/battery/BAT1/info command says my SANYO battery has the capability of charging to 2200 mAh, BUT it stops charging at 1427 mAh.  I'm getting an hour battery time when I should be getting at least two hours.

Here's my output: INFO
```
present:                 yes
design capacity:         2200 mAh
last full capacity:      1427 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            ZL05
serial number:           10717
battery type:            LION
OEM info:                SANYO

```

and 
STATE
```
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            65366 mA
remaining capacity:      1411 mAh
present voltage:         2 mV

```

It will stop charging at 1427 mAh.  Anybody running into this issue with Acers or SANYO batteries?  This is not related to the HAL bug recently submitted as far as I can tell.

Any suggestions or comments would be great!

---

### Post by og-emmet on 2006-11-29
For the benefit of other laptop users to see the same on your machine: 
```
cat /proc/acpi/battery/*/*
```

So you see:

> design capacity:         2200 mAh
last full capacity:      1427 mAh


Your battery is dying but it's not that bad. "last full capacity" means the max the battery was able to take during the last charge. Here's the same from my three year old Sharp MC24:

[INDENT]alarm:                   unsupported
present:                 yes
design capacity:         4000 mAh
last full capacity:      1715 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 171 mAh
design capacity low:     85 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            Internal Battery
serial number:
battery type:            Lion
OEM info:                SHARP Corporation
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      1715 mAh
present voltage:         12544 mV[/INDENT]

Notice "present rate" is 0mA which means the battery is "fully" charged. So my battery will only charge up to about 42% of it's original capacity. I just placed an order with a company called  "Battery Refill" ([www.batteryrefill.com](www.batteryrefill.com)) to basicly cut open my battery case and replace the two cells. Total cost to change a dying 4000mAh battery to a new 4400mAh (with 2-2200mAh cells) is $90USD (including shipping).BTW, lower mAh batteries cost less, higher more. Since li-ions start degrading from day one IMO this is a better solution than buying NOS (new old stock). With all the issues of charging li-ions I feel better about having the mfg's original charging circuitry than a third party's. 

I'll post a followup to this thread with the results of the "new" battery and dealing with refill company.

So the problem isn't with the software, it's an aging battery.

---

