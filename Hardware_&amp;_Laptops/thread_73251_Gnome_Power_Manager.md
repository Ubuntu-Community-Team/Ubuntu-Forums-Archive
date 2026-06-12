---
title: "Gnome Power Manager"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by Starman on 2005-10-08
After installing GPM I see this warning when I select 'Power Preferences' from the SYSTEM > PREFERENCES > POWER PREFERENCES icon.

'You have not got DPMS support enabled in gnome-screensaver. You cannot change the screen shutdown time using this program'

Anyone have any ideas how to resolve this? Is it even important?

Enabling acpi_sleep=true in /etc/default/acpi-support 

and

Enabling sleep.sh in /etc/acpi/events/lidbtn

no longer allows the system to sllep when the lid is closed...

thanks in advance...

---

