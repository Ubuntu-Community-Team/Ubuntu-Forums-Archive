---
title: "Toshiba Satellite A60: how to change brightness?"
date: 2009-09-19
forum: Hardware
---

### Post by edonan on 2009-09-19
Hello, I have a Toshiba Satellite A60 (SA60-125 IT), my bios is "acpi bios v1.70", and I am running Jaunty who tells me on the startup: "timer not connected to IO-APIC".

I CAN'T change the brightness using the fn key, the brightness applet in gnome panel is unable to retrieve lcd brightness, and /proc/acpi/video/ is empty.

Module "kernel/drivers/acpi/toshiba_acpi.ko" is loaded (I can see it with modprobe -l).

I tried to boot with "noapic" and "nolapic" options, one at a time, but it didn't work (and in the first case it disabled my usb ports as well).
I tried to install fnfx, but apt-get told me I had to install fnfxd instead. So I did, but in the end of the installations I got this:
```
fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

invoke-rc.d: initscript fnfxd, action "start" failed.
```
Indeed, /proc/acpi/toshiba doesn't exist.

I'm clueless. Is there a way to change the brightness without deal with acpi? Or, should I flash my bios to get the new version (1.80)? Or, is there some kernels that support fn keys in my laptop (I have 2.6.28-15-generic)?

Thank you very much!

---

