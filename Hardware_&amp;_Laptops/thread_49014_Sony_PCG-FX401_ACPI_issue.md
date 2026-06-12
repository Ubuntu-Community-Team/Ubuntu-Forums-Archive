---
title: "Sony PCG-FX401 ACPI issue"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by Inigo Montoya on 2005-07-14
I sort of inherited an old Sony laptop (PCG-FX401) some time ago. Before i installed Ubuntu Hoary I flashed the BIOS to version R0121K5 ([http://www.myplc.com/sony/](http://www.myplc.com/sony/) for details). Installation worked out fine, but on first boot the gnome battery applet went mad. So I spent some time on the issue and found something quite strange.
In /proc/acpi/ac_adapter/ACAD/state the ac adapter status is always shown correctly which means "state: on-line" if plugged in and "state: off-line" if not. But if I listen to the ACPI events using "acpi_listen" no event is cought by acpid while plugging/unplugging the ac adapter! Investigating the acpi_listen output and the acpid logs i just found events for battery, button/sleep and button/lid. So why does proc know whats going on and acpid not?!?!
Any hints?

---

