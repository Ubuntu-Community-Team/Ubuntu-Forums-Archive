---
title: "Brightness"
date: 2012-04-26
forum: Hardware
---

### Post by Spae on 2012-04-26
Can't adjust with either the function keys or in the settings menu.

Tried both 11.10 and 12.04, no difference.

ls /sys/class/backlight
acpi_video0 intel_backlight

This is really important. For battery and the health of my eyes!

Ubuntu doesn't recognise my graphics. I have intel hd3000 graphics. Are there not any drivers? hd3000 is so common, i can't believe it. :(

---

### Post by matt_symes on 2012-04-26
Hi

> acpi_video0 intel_backlightYou have two acpi drivers loaded for the backlight by the looks of it.

Can you post the output of this command

```
ls /sys/class/backlight/*
```And please post the output of

```
cat /proc/cmdline
```It may just be a case of using the backlight=vendor kernel command line switch.

Kind regards

---

### Post by Spae on 2012-04-26
Hi, thanks for your reply here are the outputs:
```
ls /sys/class/backlight/*
/sys/class/backlight/acpi_video0:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/intel_backlight:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

``````
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=f24ba3d8-c820-4d2e-a9c3-104fde46793c ro quiet splash vt.handoff=7

```> It may just be a case of using the backlight=vendor kernel command line switch.Ok I think I understand. But i'm not sure how to change that.
Edit:I am using boot-repair software to disable acpi

Thanks for your help. That was so simple. Edit: But now my fan is running 100% non-stop?

Edit:Swapped acpi=off with acpi_backlight=vendor, or something like that. Now the fan works normally and the brightness is adjustable. :)

---

### Post by matt_symes on 2012-04-26
Hi

> Edit:Swapped acpi=off with acpi_backlight=vendor, or something like  that. Now the fan works normally and the brightness is adjustable. :smile:That's what i meant. acpi=off is a big hammer when it's only your backlight causing the problems.

acpi_backlight=vendor will tell the kernel to use the intel backlight kernel module to control the brightness and not the generic acpi video module.

I'm glad it's fixed.

Kind regards

---

