---
title: "eee and high load cycle fix best value for BATT_HD_POWERMGM"
date: 2008-12-03
forum: Hardware
---

### Post by frrobert on 2008-12-03
I am  running Ubuntu 8.10 with Adam's kernel and elmurato's ACPI scripts on a 1000HA and it was suffering from a high load cycle count. 

I edited  /etc/default/acpi-support to 

"ENABLE_LAPTOP_MODE=true" 


then edited etc/laptop-mode/laptop-mode.conf 
changing the following line with the values below

LM_AC_HD_IDLE_TIMEOUT_SECONDS=7200
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=300

BATT_HD_POWERMGMT=200

and it seems to resolve the issue of high load cycles but is that the best number to use for BATT_HD_POWERMGMT=  the default was 1 which resulted in very high load cycles and so did 128

I was curious what other people were doing?

---

