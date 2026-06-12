---
title: "ACPI Resume will reboot"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by chris-at on 2006-08-28
Could someone help me with a resume problem on an IBM ThinkCentre M50 Desktop (I also got the same issue on a Compaq Evo D510)?

- I've enabled ACPI_SLEEP=true in /etc/default/acpi-support
- "echo -n mem>/sys/power/state" suspends the machine and the power button starts to blink (OK)
- pressing any key on the keyboard has no effect (should wake up)
- when I press the power button again it reboots instead of waking up.

I've tried a few options in /etc/default/acpi-support and also added "acpi_sleep=s3_bios" in grub but I can't get it to work.

Thanks!

---

