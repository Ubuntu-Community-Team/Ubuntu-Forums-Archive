---
title: "Problems with Rode NT USB micro on Ubuntu"
date: 2020-02-18
forum: Hardware
---

### Post by fuggl on 2020-02-18
Hi everyone,

I'm on Ubuntu 18.04.4 LTS and have bought a Rode NT USB microphone. When I plug it in I repeatedly get error messages like the following:

```
22:06:55 kernel: usb 5-3: Manufacturer: RODE Microphones
22:06:55 kernel: usb 5-3: Product: RODE NT-USB
22:06:55 kernel: usb 5-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
22:06:55 kernel: usb 5-3: New USB device found, idVendor=19f7, idProduct=0003
22:06:55 kernel: usb 5-3: new full-speed USB device number 36 using xhci_hcd
22:06:55 kernel: usb 5-3: device not accepting address 35, error -71
22:06:55 kernel: usb 5-3: Device not responding to setup address.
22:06:55 kernel: usb 5-3: Device not responding to setup address.
22:06:55 kernel: usb 5-3: new full-speed USB device number 35 using xhci_hcd
22:06:54 kernel: usb 5-3: device not accepting address 34, error -71
22:06:54 kernel: usb 5-3: Device not responding to setup address.
22:06:54 kernel: usb 5-3: Device not responding to setup address.
22:06:54 kernel: usb 5-3: new full-speed USB device number 34 using xhci_hcd
22:06:53 kernel: usb 5-3: device not accepting address 33, error -71
22:06:53 kernel: usb 5-3: Device not responding to setup address.
22:06:53 kernel: usb 5-3: Device not responding to setup address.
22:06:53 kernel: usb 5-3: new full-speed USB device number 33 using xhci_hcd
22:06:52 kernel: usb 5-3: device not accepting address 32, error -71
22:06:52 kernel: usb 5-3: Device not responding to setup address.
22:06:52 kernel: usb 5-3: Device not responding to setup address.
22:06:52 kernel: usb 5-3: new full-speed USB device number 32 using xhci_hcd
22:06:51 kernel: usb 5-3: USB disconnect, device number 31
22:06:51 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:51 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:50 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:50 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:45 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:45 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:42 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:42 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:32 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:32 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:13 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:13 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:06:03 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:06:03 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:59 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:59 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:58 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:58 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:54 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:54 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:52 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:52 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:44 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:44 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:43 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:43 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:41 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:41 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:32 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:32 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:29 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:29 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:27 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:27 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:23 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:23 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
22:05:20 kernel: usbhid 5-3:1.3: can't add hid device: -71
22:05:20 kernel: usb 5-3: 10:0: cannot get min/max values for control 2 (id 10)
```

How do I get this fixed? Thanks in advance for any hints!

---

### Post by CatKiller on 2020-02-18
There are plenty of reports of that microphone working fine without any additional configuration. Make sure that whatever port you're plugging it into is able to provide sufficient power.

---

### Post by fuggl on 2020-02-19
You're right, using another USB port helped. Probably should have tested that earlier.. though the ports aren't really any different type wise.
Anyway, thanks!

---

