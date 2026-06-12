---
title: "Device Permissions on boot"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by MeMo_oMeM on 2006-01-06
Hello everyone,

I have a problem with setting correct permissions for devices at boot time. I had to create a device (/dev/perfctr) to be able to use hardware counters. Its permissions should be set to 644. When I reboot the machine, the init process changes the permissions to 640, and I have to 'su' to root and use chmod to correct the settings. This is frustrating to do so every time I reboot the laptop.

Do you know which script or program sets the permissions at boot time? How can I modify it to set 644 to /dev/perfctr? 

Thank you so much in advance, and have a great new year! :D 
MeMo

---

### Post by ape on 2006-01-07
Not sure on this (as I've never had to do it), but have you tried adding an entry for your device into the /etc/udev/permissions.d/udev.permissions file?

---

