---
title: "after hybernation doesn't resumt"
date: 2008-04-29
forum: Hardware
---

### Post by lugburz on 2008-04-29
Hi All,
I just updated from 7.10 to 8.04,all seems to work well but I lost the possibility to hybernate my laptop (sony vaio sz1m), that before worked very well.

When I try to hybernate the laptop seems to do all usual stuffs, with only a screnn message that doesn't seem an erroes, something like "drm_sys_suspend". Then when I restart the laptop it does the normal reboot.

In general my boot screen appears strange: the graphical boot run for few seconds but when the scripts are called the graphical bar changes in text messages.

---

### Post by Pomble on 2008-04-29
I'm completely new to Ubuntu myself, but have you tried putting the NOACPI flag in your boot string?  It might be a power management issue.  Just a thought.

---

### Post by lugburz on 2008-04-29
I'm not sure but suspend works well so I'd like before to try something else. dmesg about acpi in example gives this message:

[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)


so I'm trying to change according this suggestion

---

### Post by lugburz on 2008-04-29
Problem solved!!!!

The two issues: not usplash login and hibarnation problem had the some reasone. My update had a problem and it didn't do the "update-initramfs", just after both thing started to work

---

