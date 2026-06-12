---
title: "Wireless Logitech USB Mouse on 8.10"
date: 2009-03-15
forum: Hardware
---

### Post by yaroto98 on 2009-03-15
My USB mouse no longer works in 8.10.  It used to work like a charm, then it digressed to flakey, and now it no longer works.  It's not the mouse itself, it works in Windows, and in my other linux boxes. The odd part is that it completely shows up in dmesg.

> [22075.597095] usb 5-1: new low speed USB device using uhci_hcd and address 2
[22075.774080] usb 5-1: configuration #1 chosen from 1 choice
[22075.889832] usbcore: registered new interface driver hiddev
[22075.904453] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input11
[22075.908149] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[22075.925372] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1
[22075.925616] usbcore: registered new interface driver usbhid
[22075.925747] usbhid: v2.6:USB HID core driver

I've looked through the forums, and haven't found any definitive answer. Any thoughts guys?

---

### Post by yaroto98 on 2009-04-15
Just fyi for those who have a similar problem, the latest kernel upgrade fixed this issue.

---

