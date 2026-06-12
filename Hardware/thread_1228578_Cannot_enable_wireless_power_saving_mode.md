---
title: "Cannot enable wireless power saving mode"
date: 2009-08-01
forum: Hardware
---

### Post by JebusWankel on 2009-08-01
I've been using Powertop to extend my battery life. It suggests I enable wireless power saving mode with the following command: > echo 5 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level

This command returns Permission denied no matter how I run it. > sudo cat /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level returns > SYSTEM:auto	MODE:fixed	INDEX:1 What can I do?

---

### Post by JebusWankel on 2009-08-02
bump

---

