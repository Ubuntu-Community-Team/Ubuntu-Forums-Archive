---
title: "hci doesn't see my usb bluetooth dongle"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by jjfraney on 2008-02-29
```
hciconfig -a
```

returns empty.

lsusb shows the usb device:
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 

dmesg shows usb and bluetooth driver action:

[   91.735483] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   91.780239] usb 3-2: configuration #1 chosen from 1 choice
[   91.782110] hub 3-2:1.0: USB hub found
[   91.785121] hub 3-2:1.0: 3 ports detected
[   91.937461] usb 3-2.2: new full speed USB device using uhci_hcd and address 3
[   92.016116] usb 3-2.2: configuration #1 chosen from 1 choice
[   92.170362] usb 3-2.3: new full speed USB device using uhci_hcd and address 4
[   92.204075] usb 3-2.3: configuration #1 chosen from 1 choice
[   92.207810] usbcore: registered new interface driver hiddev
[   92.212282] input: Broadcom Corp BCM2045B3 ROM as /class/input/input8
[   92.212778] input: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-2.2
[   92.217578] input: Broadcom Corp BCM2045B3 ROM as /class/input/input9
[   92.218086] input: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-2.3
[   92.236082] usbcore: registered new interface driver usbhid
[   92.236465] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  315.907882] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  567.594663] Bluetooth: HCI USB driver ver 2.9
[  567.595571] usbcore: registered new interface driver hci_usb


any suggestion?

I've seen other post where this usb-bluetooth dongle was succesfully used with a bluetooth keyboard.  I also am able to use the dongle in Windows XP.

I have a Dell lattitude 830.  Ubuntu 7.10 installed with latest patches.

Thanks,
John

---

