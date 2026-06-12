---
title: "Q: How to set min battery voltage on laptop"
date: 2018-09-10
forum: Hardware
---

### Post by linuksguru on 2018-09-10
Hi !


I have reconditioned Lenovo Thinkpad laptop battery with new high-capacity 18650 cells from Samsung. However, even after battery stats reset with Lenovo Power Management software, battery capacity and remaining time are being displayed incorrectly, data is based on old 2200 mAh cells, now new 3500 mAh ones.

Since I did not found a way to reset battery EPROM chip, the only way is to set minimum battery voltage is to hack parameters of either kernel/acpi or upower. 
Battery voltage seem to be displayed correctly (it is measured by separate circuit) yet capacity and remaining time are not. Laptop shuts down prematurely with battery still holding enough charge.
How to correctly do this ?

I’m using MATE desktop, it deploys standard Gnome utilities for power management.

Thanks in advance
Andrei

---

