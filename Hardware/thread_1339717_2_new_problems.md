---
title: "2 new problems"
date: 2009-11-27
forum: Hardware
---

### Post by aleksandarne on 2009-11-27
hi, i had problem with booting ubuntu on batteries, i solved that problem with help of ubuntu-sr members. I boot ubuntu by adding acpi=off in grub, but now  my battery meter does not work, and i do not know where do i need to save that acpi=off once forever, because i must write this on every boot; on power meter is only shown ac mode, nomether the computer is runing on battery.

thank you

---

### Post by nixscripter on 2009-11-28
Fixing it across boots can be done by modifying **/boot/grub/menu.lst** Then, you must run **update-grub** in order for the changes to stick.

Hope this helps.

---

### Post by mvalero on 2009-11-28
This problem seems familiar to me, I imagined that the ACPI bios extensions might have something to do with it, because the newest bios version for my laptop implements the latest ACPI estensions for Vista and two flavors of Linux (being Ubuntu one of them) failed to install, I even had to go one version of bios back to use Ubuntu.
Curiously, I had no problems with Ubuntu 9.04, and now I just can complete the boot with v9.10, something has happened in the meantime with ACPI control?

---

