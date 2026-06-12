---
title: "Battery charge monitor doesn't detect battery (Acer Aspire 1681wlmi)"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by obiwankamote on 2007-11-22
Hi guys. I'm having trouble in detecting my battery status. When I use the battery charge monitor applet it doesn't detect the battery. After reading from some posts, i tried the following commands:

$ cat /proc/acpi/battery/BAT1/info 
present:                 no

But when I tried accessing BAT0

$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         65120 mWh
last full capacity:      -16630 mWh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: unknown
design capacity low:     unknown
capacity granularity 1:  unknown
capacity granularity 2:  unknown
model number:            04ZL
serial number:           1
battery type:            LION
OEM info:                SMP-SONY

When I remove the adapter and put it back, the values are updated. It seems that it is actually detected. However, if I'm not mistaken, the battery charge monitor is using the BAT1 info not BAT0. Is there a way to specify this? Or is there another solution for this? Thanks!

---

### Post by Tio on 2007-11-22
Hello,
I have the same problem... The battery is detected by reinstalling HAL but it works just for a session :( .
Even if I reinstall HAL, i don't have the battery options in the power management preferences :(

Thanks

---

