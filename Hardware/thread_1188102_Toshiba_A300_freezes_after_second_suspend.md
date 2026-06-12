---
title: "Toshiba A300 freezes after second suspend"
date: 2009-06-15
forum: Hardware
---

### Post by szarywilq on 2009-06-15
Hi,

I have Toshiba A300 and Ubuntu 9.04.
I can suspend laptop once. After I wake it syslog is full of:

> Jun 15 16:57:21 mateusz-laptop kernel: [15795.176348] ACPI: Transitioning device [FAN] to D3
Jun 15 16:57:21 mateusz-laptop kernel: [15795.176350] ACPI: Unable to turn cooling device [ffff8800bf815640] 'off'
Jun 15 16:57:31 mateusz-laptop kernel: [15804.647070] ACPI: Transitioning device [FAN] to D3
Jun 15 16:57:31 mateusz-laptop kernel: [15804.647073] ACPI: Unable to turn cooling device [ffff8800bf815640] 'off'
Jun 15 16:58:32 mateusz-laptop kernel: [15865.878926] ACPI: Transitioning device [FAN] to D3
Jun 15 16:58:32 mateusz-laptop kernel: [15865.878929] ACPI: Unable to turn cooling device [ffff8800bf815640] 'off'

And when I suspend laptop again, it freezes at resume.

---

### Post by szarywilq on 2009-06-16
bump

---

### Post by SonicsDemon on 2009-11-26
dido. exact issue. Regardless of kernel.:confused:

---

### Post by SonicsDemon on 2009-11-26
i have had this laptop for at least a year now. Its suspend on one distribution of ubuntu a while ago worked. Maybe i should try a few test installs of some older versions and see what has changed.

---

