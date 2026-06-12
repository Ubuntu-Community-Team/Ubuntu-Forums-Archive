---
title: "USB joysticks cause delay during boot"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by heldal on 2006-11-04
The HID-system seems to be confused during boot on a system with PS/2 keyboard and mouse combined with joysticks. After the kernel has been loaded, but before any filesystems are mounted, it seems to spend some time discovering attached USB input devices. After some timeout the system reports:

```
drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
drivers/usb/input/hid-core.c: timeout initializing reports
```

.. on the console, and then continues normally (without splash). Everything works ok thereafter, but the delay is annoying. I first noticed this problem on breezy (5.10) . On dapper (6.06) it was fixed, and now with edgy (6.10) it is back.

Attached USB devices are:
```
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:08a2 Logitech, Inc. Labtec WebCam Pro
Bus 004 Device 002: ID 03f0:6004 Hewlett-Packard DeskJet 5550
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:c215 Logitech, Inc. 
Bus 003 Device 003: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

(046d:c215 is a Logitech Extreme 3D joystick)

The system boots with no delay if the joysticks are disconnected


//per

---

