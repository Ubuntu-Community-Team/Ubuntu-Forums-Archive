---
title: "USB Keyboard disconnect"
date: 2017-10-22
forum: Hardware
---

### Post by ellipticblue on 2017-10-22
I usually use a PS/2 keyboard however after buying a USB keyboard I am able to use it. It works correctly in bios and so I believe it is not a problem with the hardware.


lsusb does not show the device
dmesg says the device has been disconnected, however it is physically connected.

```
[  267.428057] usb 2-1.2: new low-speed USB device number 5 using ehci-pci
[  267.555545] usb 2-1.2: New USB device found, idVendor=1017, idProduct=2010
[  267.555550] usb 2-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[  267.555552] usb 2-1.2: Product: Gaming Keyboard
[  267.569972] input: Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:1017:2010.0006/input/input19
[  267.624549] hid-generic 0003:1017:2010.0006: input,hidraw5: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:1d.0-1.2/input0
[  268.235649] input: Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:1017:2010.0007/input/input20
[  268.288697] hid-generic 0003:1017:2010.0007: input,hiddev0,hidraw6: USB HID v1.10 Mouse [Gaming Keyboard] on usb-0000:00:1d.0-1.2/input1
[  268.288980] usb 2-1.2: USB disconnect, device number 5

```

Any suggestion for identifying the cause of this?

---

