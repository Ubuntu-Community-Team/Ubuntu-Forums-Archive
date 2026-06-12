---
title: "USB mouse not detected on a amd64 laptop"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by mache on 2005-05-29
Hi,

I have a HP Pavilion zv5000 laptop, with hoary-amd64 installed on it. The laptop has 3 USB ports, 2 x USB 1.1 and 1 x USB 2.0. Here is the lspci output:
```
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
``` 
The Installer did not detect my USB mouse, nor hotplug or anything else. Even if I run  ```
modprobe usbmouse
```, when I plug in the mouse, nothing happens, not even the mouse light doesn't turn on.

Previously I had debian pure64 port on this laptop and the usb mouse was working, but I was stupid enough to not save its /etc.

Any hint is appreciated.

---

### Post by mache on 2005-05-30
Problem solved by Bios Upgrade from HP. With Bios revision F.34, the USB ports are working just fine.

---

