---
title: "acpitool, lsusb and lspci how to correlate device names"
date: 2010-08-01
forum: Hardware
---

### Post by shiftbit on 2010-08-01
Im trying to make the connection between what I see with lspci and lsusb (more descriptive names)

The goal here is to identify the device name/id of a keyboard and mouse that I can use to wakeup the pc from suspend.

I think im confusing the bus and the device.  A given bus might have several devices associated with it.

Both the acpitool -w, and lspci commands will give me the sysfs value, but not a descriptive name to identify which usb device its talking about.  

After I identify WHICH device to use then I can

echo device_name > /proc/acpi/wakeup


Then, I just need to added this command to a startup script so its available after reboot.

---

### Post by eschoeller on 2010-10-21
I'm trying to do the same thing. Did you figure this out?

---

