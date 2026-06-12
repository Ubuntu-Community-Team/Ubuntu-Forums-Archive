---
title: "HP Pavilion TX2000 TX2500 series Thermal Sensors"
date: 2010-03-19
forum: Hardware
---

### Post by Slade Winstone on 2010-03-19
Hi,

I'm running 9.10 on an HP Pavilion TX2522AU (TX2500 series) laptop/tablet.  I've finally managed to get the thermal or CPU temperature sensors running properly so that I can monitor the CPU temp with an applet. :guitar:

Simply, edit the appropriate grub config and add the following to the kernal parms:
acpi_osi=Linux

For Grub 2, edit: /etc/default/grub and update the line GRUB_CMDLINE_LINUX_DEFAULT to include acpi_osi=Linux

e.g.

GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash" 

Then, update-grub.

You should then be able to add the sensors applet and lm-sensors (if needed)

Regards,
Slade.

---

