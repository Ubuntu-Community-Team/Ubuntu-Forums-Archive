---
title: "PowerTOP changes not made permanent"
date: 2009-07-13
forum: Hardware
---

### Post by JebusWankel on 2009-07-13
I was excited to find PowerTOP when I went searching for ways to stretch my battery life. Windows 7 gets much longer battery life than Ubuntu. I have a one year old Thinkpad T61 with the 9-cell battery, but I only get 3.5 hours of run time with wi-fi on, no Compiz. Under Intrepid I had 4 hours 20 minutes of battery life.

Whenever I restart and run PowerTOP, it suggests the same measures. Also it is unable to enable wireless power saving mode with this command

```
echo 5 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level
```

when I run it alone with sudo I get a permission denied error.

How do I get these settings to become permanent, or to be enable them when I disconnect AC power?

---

