---
title: "Power management on an older machine"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by azebuski on 2008-01-08
I am running Ubuntu 7.10 on an old Compaq Deskpro PIII 450mhz, 256mb machine. Sound, video, wireless Internet, digital camera, photo printer, all work flawlessly but I cannot get power management to work properly.

No screensavers work, the screen just goes blank, and I cannot turn off the computer. If I select shutdown, the hard drive stops spinning, but the Ubuntu logo stays on the screen and the fans continue running. The only way to turn off the computer is to pull the plug out of the wall.

When I bootup the first message I see is ACPI: BIOS date (1999) exceeds cutoff date (2000) ACPI=force if required.

If there anything I can do?  Thanks!

---

### Post by tgalati4 on 2008-01-09
Did you boot with the kernel switch (ACPI=force)?  If so did the power management behavior change?

---

### Post by azebuski on 2008-01-09
Thanks. I added acpi=force as a kernel switch and it works! Screensavers work and the machine shuts down properly.

Guess I should have done more googling before asking questions. :)

---

