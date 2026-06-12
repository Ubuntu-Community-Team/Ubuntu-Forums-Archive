---
title: "USB Mouse stopped working"
date: 2005-11-28
forum: General Help
---

### Post by smgil on 2005-11-28
Hi.


I've just upgrade from Hoary to Breezy. I have a problem with my USB optical mouse, it just doesn't work. I never had this problem in hoary.

I've seen two post with same problem but with no answer. I'm running Breezy in a toshiba satellite a20. By the way, touchpad does work.

dmesg print something like this.

```

[4294799.887000] hub 3-0:1.0: connect-debounce failed, port 5 disabled
[4294800.064000] usb 1-3: new low speed USB device using ohci_hcd and address 7
[4294800.159000] usb 1-3: unable to read config index 0 descriptor/all
[4294800.159000] usb 1-3: can't read configurations, error -110
[4294800.234000] usb 1-3: new low speed USB device using ohci_hcd and address 8
[4294800.712000] usb 1-3: device not accepting address 8, error -75
[4294800.785000] usb 1-3: new low speed USB device using ohci_hcd and address 9
[4294800.800000] usb 1-3: device descriptor read/8, error -75
[4294800.913000] usb 1-3: device descriptor read/8, error -75
[4294801.087000] usb 1-3: new low speed USB device using ohci_hcd and address 10
[4294801.314000] usb 1-3: config 1 has an invalid interface number: 1 but max is 0
[4294801.314000] usb 1-3: config 1 has no interface number 0
[4294801.347000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:0c.0-3
[4294802.742000] drivers/usb/input/hid-core.c: input irq status -75 received
[4295467.866000] usb 1-3: USB disconnect, address 10
[4295471.513000] hub 3-0:1.0: connect-debounce failed, port 5 disabled
[4295471.690000] usb 1-3: new low speed USB device using ohci_hcd and address 11
[4295471.786000] usb 1-3: config 1 has an invalid interface number: 1 but max is 0
[4295471.786000] usb 1-3: config 1 has no interface number 0
[4295471.810000] usbhid: probe of 1-3:1.1 failed with error -5
[4296117.089000] input: AT Translated Set 2 keyboard on isa0060/serio0

```

---

### Post by amohanty on 2005-11-29
DId you try reconfiguring Xorg via:
sudo dpkg-reconfigure xserver-xorg
and resetting up your mouse?
AM

---

