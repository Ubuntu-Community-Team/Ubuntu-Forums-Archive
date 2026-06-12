---
title: "Touch pad turns off completely after turning off"
date: 2010-01-24
forum: Hardware
---

### Post by dE_logics on 2010-01-24
Actually this is a problem in someone else's lap.

After turning off the touchpad in a session, it cannot be turned on back again...

There's a light indicating the status of the touchpad. Turning off the touchpad (using a given button) will turn off this light, and turning it on back again will turn the light on too, but the touchpad will not work on Ubuntu unless restarted.
--------------------solved------------------

Add "nomodeset i8042.nomux acpi_backlight=vendor" (excluding quotes) in the kernel options (i.e line starting with 'kernel') in /etc/grub.cfg

---

