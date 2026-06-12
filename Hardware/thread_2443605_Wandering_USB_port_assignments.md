---
title: "Wandering USB port assignments"
date: 2020-05-17
forum: Hardware
---

### Post by skoles on 2020-05-17
My DELL Inspiron dual boot has been working well except for some USB ports are reassigning themselves in ways that are illogical to me. Of course, I am sure there is more to this behaviour.

I have a 3.0 USB hub plugged into the rear of the machine. I have a number of USB devices (WIN keyer, COM port for a ham radio) that are connected to this hub. I also have a Starlink RS232 8 port interface I use for my older generation radio com port interfaces. I setup everything up after I moved the 3.0 hub to another USB jack on the rear. The Starlink has active com port connections on hardware ports(DB9's) 1, 2, 3 and 8. These got recognized as USB0, USB1, USB2 and USB 7. WinKey was connected through the hub and assigned USB8. The other radio com port connected to the 3.0 hub got assigned USB9. All was working with my logging program and other radio software. When I rebooted, the assignments shifted around. Why ? An explanation why this happened would help me greatly. The WinKeyer got reassigned USB3 and the ham radio com port got reassigned to USB7, an already occupied RS232 port on the Starlink interface. Kind of whacky behaviour. A way to lock the assignments would be cool. I am still coming up to speed on Ubuntu in general but can hack my way through anything technical once given a direction.

---

### Post by TheFu on 2020-05-17
Devices are named in the order they are discovered by the kernel and the driver used.  From boot to boot, different hardware has different initialization time and those times lead to different discovery order.

Before systemd, we could force specific names for devices in udev rules.  Perhaps that still works?  Those settings were under /etc/udev/rules..... somewhere.  Perhaps the systemd guys moved them?  idk.

---

### Post by skoles on 2020-05-20
Hmmm, ok. Will poke around for udev rulage stuff. If you think of anything else, i am listening :-)

> **TheFu said:**
> Devices are named in the order they are discovered by the kernel and the driver used.  From boot to boot, different hardware has different initialization time and those times lead to different discovery order.

Before systemd, we could force specific names for devices in udev rules.  Perhaps that still works?  Those settings were under /etc/udev/rules..... somewhere.  Perhaps the systemd guys moved them?  idk.

---

### Post by TheFu on 2020-05-20
[https://askubuntu.com/questions/905115/assigning-name-to-usb-device](https://askubuntu.com/questions/905115/assigning-name-to-usb-device) has some more specifics.

---

