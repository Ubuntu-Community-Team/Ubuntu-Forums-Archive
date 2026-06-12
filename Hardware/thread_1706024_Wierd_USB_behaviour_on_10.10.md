---
title: "Wierd USB behaviour on 10.10"
date: 2011-03-13
forum: Hardware
---

### Post by sinurge on 2011-03-13
Every some time, i lose my USB mouse, no device activity. There is not dump if use dmesg| tail

This happens often, i remove the usb and reattach it it works again for some time before that same happening again.

I earlier has a PCI  mouse and it worked with no issues. Would it be a mouse hw issue.

Lost today again post boot, and looked up dmesg, can anyone help. At 85 seconds i attached the USB mouse again.

 77.776075] usb 2-1: USB disconnect, address 2
[   79.864036] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   80.023046] usb 3-2: config index 0 descriptor too short (expected 34, got 32)
[   80.023052] usb 3-2: config 1 has an invalid descriptor of length 7, skipping remainder of the config
[   80.023058] usb 3-2: config 1 interface 0 altsetting 0 has 0 endpoint descriptors, different from the interface descriptor's value: 1
[   80.053129] usbhid 3-2:1.0: couldn't find an input interrupt endpoint
[   85.960047] usb 3-2: USB disconnect, address 2
[   91.476017] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   91.676691] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input4
[   91.676835] generic-usb 0003:15D9:0A4C.0002: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:10.0-1/input0
[  184.144021] usb 2-1: reset low speed USB device using uhci_hcd and address 3

---

### Post by sinurge on 2011-04-04
Bump

---

