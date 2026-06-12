---
title: "New Sony Vaio - AR Series - Brightness Control"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by veediot on 2006-12-12
It seems the sonypi module doesn't allow one to control brightness on the new AR series VAIOs. I have a VGN-AR150g, and have tried changing the value of /proc/acpi/sony/brightness and /proc/acpi/sony/brightness_default, but unfortunately, it has no effect. Has anyone heard of any new kernel modules that allow control of this?

Thanks!

---

### Post by veediot on 2007-01-04
I've figured it out. The VAIO I have has an NVIDIA GeForce Go in it, so a package called smartdimmer can control the brightness level.

---

