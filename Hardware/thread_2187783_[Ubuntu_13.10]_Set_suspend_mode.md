---
title: "[Ubuntu 13.10] Set suspend mode"
date: 2013-11-13
forum: Hardware
---

### Post by P_Aleksandrov on 2013-11-13
How can I set suspend mode to use in LXDE (standby, mem)? In /etc/default/acpi-support ACPI_SLEEP_MODE is said to be deprecated. It seems that if I click "Suspend" in LXDE computer goes into "freeze" mode, but I want "standby". If I use pm-suspend computer immediately resumes after going into sleep. "echo standby > /sys/power/state" seems to work, but is this safe?

---

