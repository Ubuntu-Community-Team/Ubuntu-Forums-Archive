---
title: "Hotplug crashes on boot on Acer TM 4401LMi"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by hypermusician on 2005-08-07
Hello everybody,

I have installed Ubuntu Hoary on my Acer Travelmate 4401LMi, with Ubuntu booting from an external usb2 hard drive. I have solved all the usb booting problems, but now the system crashes when Ubuntu tries to boot and says 'Initializing hotplug subsystem...'.

Any ideas how I could fix this? If I remove the /etc/hotplug folder, then the system boots fine, but obviously I can't use my usb mouse (and the touchpad won't work). All I need to do is find a way of debugging the hotplug initialization so that I can blacklist the appropriate module, but the hotplug system is really poorly documented, and after a month of trying, I still can't work out how to debug it. I've disabled apic and acpi as a boot option in grub, because I've heard Acers have problems with these.

Any help would be really, really great guys.

---

