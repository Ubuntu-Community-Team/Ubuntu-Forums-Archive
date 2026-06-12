---
title: "How install driver or enable support for generic USB game controller ?"
date: 2021-09-21
forum: Hardware
---

### Post by aug7744 on 2021-09-21
How enable or install driver for generic usb controllers (look compatible with PS3 or PC) in Ubuntu 20.04.3 and 21.04 ?
Thanks for your reply.

---

### Post by TheFu on 2021-09-22
There are 100K different USB devices. Each can have a different driver, though most will fall into the USB-Storage or keyboards or mice driver arenas.

Start by looking up the device ID you want to support.  **lsusb** can help with that.  Then take that device ID and search for a Linux driver. There is no "general solution" for all devices. Sorry.

I don't have a PS3, but I have a Thrustmaster joystick.
```
$ lsusb
Bus 001 Device 007: ID **044f:b102** ThrustMaster, Inc. 
.....  {other devices like USB hubs and PS/2 Keyboard+Mouse Adapter}
```

Take the 044f:b102 and google for "linux driver 044f:b102" <--- that's an example. Yours WILL be different. BTW, there is no driver for my joystick. There are these devices, which could be close:
```
	b108  T-Flight Hotas X Flight Stick
	b10a  T.16000M Joystick
``` according to [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)  A generic joystick driver might work for the simple stuff. IDK.

---

### Post by aug7744 on 2021-09-26
Thanks.

---

### Post by Holger_Gehrke on 2021-09-26
Actually, game controllers of all kind are handled by the HID (Human Interface Devices) system. You should find a device file for a connected pad or joystick in /dev/input/js[0-9]. To check whether every input (digital buttons or analog axes) on the device is recognized and correctly interpreted you can use jstest in a terminal or jstest-gtk in a GUI. I currently have a Logitech F310 connected and all 8 axes (two thumbsticks, a dpad and the lower shoulder buttons) and 10 buttons are recognized and the test programs show changing values if I move the sticks or press a button. No installation of drivers necessary, not for this pad or the two others by other manufacturers I used previously.

Holger

---

