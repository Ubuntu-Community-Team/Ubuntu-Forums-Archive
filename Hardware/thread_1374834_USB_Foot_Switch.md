---
title: "USB Foot Switch"
date: 2010-01-07
forum: Hardware
---

### Post by hughsaunders on 2010-01-07
Hello All, 

I have a USB foot switch from Cleware

lsusb shows:
```
Bus 001 Device 011: ID 0d50:0141 Cleware GmbH
```

On insertion dmesg shows:
```
[4396540.654479] usb 1-2.4.1: new low speed USB device using uhci_hcd and address 11
[4396540.788416] usb 1-2.4.1: configuration #1 chosen from 1 choice
[4396540.810340] input: Cleware GmbH USB-Keys01 as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2.4/1-2.4.1/1-2.4.1:1.0/input/input13
[4396540.833219] input,hidraw3: USB HID v1.00 Keyboard [Cleware GmbH USB-Keys01] on usb-0000:00:10.0-2.4.1

```

So it looks like it's detected as a keyboard (even though it only has a single switch) How can I set which code it sends when it is pressed?

The aim is to use it to play/pause audio when transcribing. 

Thanks in advance, 

Hugh.

---

