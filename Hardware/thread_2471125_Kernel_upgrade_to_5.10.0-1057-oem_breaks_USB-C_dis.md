---
title: "Kernel upgrade to 5.10.0-1057-oem breaks USB-C display connection?"
date: 2022-01-21
forum: Hardware
---

### Post by ian on 2022-01-21
Hi,

Ubuntu 20.04 on a HP Laptop 840 G7 (I think) with HP Z27k monitor, connected with USB-C. Until the very recent kernel upgrade to 5.10.0-1057-oem (from 5.10.0-1055-oem) the display worked fine as main screen. Since the upgrade the display does not work via USB at all, only via HDMI.
Error message in dmesg is: 
"i915 0000:00:02.0: [drm] *ERROR* Sending link address failed with -5"

Any ideas? Any additional info I could check to figure out what happened?

Thanks, ian

---

### Post by ian on 2022-01-24
Hm, after removing .config/monitor.xml and rebooting it did work again :confused:

---

