---
title: "ACPI: platform missing in /sys/power/disk"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by lohmueller on 2005-10-13
With Ubuntu-5.04 I had hypernate (suspend to disk) working with the acpi-platform-mode.

Since I updated to Breezy "cat /sys/power/disk" shows only "shutdown". The line "platform" is missing.

Does anyone know how to force "platform"? I know, that it works with platform, but not with shutdown.

many thanks

---

### Post by mlord on 2005-10-13
echo "platform" >/sys/power/disk

---

### Post by lohmueller on 2005-10-13
[QUOTE=mlord]echo "platform" >/sys/power/disk[/QUOTE]
Does not work. It does a "shutdown" instead. I have to find a way to add "platform" to the list of supported modes (cat /sys/power/disk).

---

