---
title: "Saitek Joypad P750"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by Corvus on 2005-02-09
Hi:

I am trying to get it working, but i fail on somewhere. The pad is hid usb and it is recognized as /dev/input/js0, joydev and usbhid are loaded too, but when i try to test it for example with cat /dev/input/js0, or jstest, nothing happens. Seems like it is recognized but not working. I tried adding the analog module but is doesn't work too. I tried removing it and conecting again and syslog doesn't show anything special. Here is the output:

Feb  9 14:45:57 localhost udev[5450]: removing device node '/dev/input/event6'
Feb  9 14:45:57 localhost udev[5456]: removing device node '/dev/input/js0'
Feb  9 14:45:57 localhost hal.hotplug[5460]: DEVPATH is not set
Feb  9 14:45:57 localhost kernel: usb 2-1: USB disconnect, address 2
Feb  9 14:46:00 localhost kernel: ohci_hcd 0000:00:02.3: wakeup
Feb  9 14:46:00 localhost kernel: usb 2-1: new low speed USB device using address 3
Feb  9 14:46:00 localhost input.agent[5500]:      evdev: already loaded
Feb  9 14:46:00 localhost input.agent[5536]:      evdev: already loaded
Feb  9 14:46:00 localhost hal.hotplug[5562]: DEVPATH is not set
Feb  9 14:46:00 localhost kernel: input: USB HID v1.00 Joystick [Saitek Saitek P750] on usb-0000:00:02.3-1
Feb  9 14:46:00 localhost input.agent[5500]:      evbug: blacklisted
Feb  9 14:46:00 localhost input.agent[5536]:      evbug: blacklisted
Feb  9 14:46:00 localhost input.agent[5563]:      joydev: already loaded
Feb  9 14:46:00 localhost input.agent[5563]:      evdev: already loaded
Feb  9 14:46:00 localhost input.agent[5563]:      evbug: blacklisted
Feb  9 14:46:00 localhost usb.agent[5622]:      usbhid: already loaded
Feb  9 14:46:00 localhost udev[5655]: configured rule in '/etc/udev/rules.d/udev.rules' at line 49 applied, 'event6' becomes 'input/%k'
Feb  9 14:46:00 localhost udev[5655]: creating device node '/dev/input/event6'
Feb  9 14:46:00 localhost udev[5656]: configured rule in '/etc/udev/rules.d/udev.rules' at line 50 applied, 'js0' becomes 'input/%k'
Feb  9 14:46:00 localhost udev[5656]: creating device node '/dev/input/js0'

Maybe it has something todo with those blacklisted modules. The joypad is working in other os like windows. Any hints ?

Thank you,

---

