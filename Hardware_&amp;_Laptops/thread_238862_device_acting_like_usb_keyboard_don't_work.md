---
title: "device acting like usb keyboard don't work"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Jaa on 2006-08-18
Hi, I have bought a usb RFID chip card reader which appears like a keyboard for the system. It works fine under Windows and Debian(the system realy things, that it is a keyboard), but when I plug it into an Ubuntu machine, there is blinking led on the reader which means "I'm initializing" and it's all what the device is doing. dmesg output is here:> [17180669.116000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[17180669.348000] usbcore: registered new driver hiddev
[17180679.356000] drivers/usb/input/hid-core.c: timeout initializing reports
[17180679.356000]
[17180679.356000] input: Ikos Liberec s.r.o. IT-7004 as /class/input/input3
[17180679.356000] input: USB HID v1.11 Keyboard [Ikos Liberec s.r.o. IT-7004] on usb-0000:00:1d.0-1
[17180679.356000] usbcore: registered new driver usbhid
[17180679.356000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

It looks like the device is waiting for some signal from the system. But who knows. Do anyone know how to resolve this problem? Thanks

---

