---
title: "USB keyboard doesn't work"
date: 2015-01-27
forum: Hardware
---

### Post by Marcoman on 2015-01-27
I have an IBM Model M keyboard with USB-SDL-6-pin adapter. The keyboard works fine on a Macbook Pro and on my desktop when I'm running Win7. The keyboard works at the bios screen and the grub menu. However, once xubuntu boots the keyboard fails to work very often. dmesg gives me this.

```
[94239.798037] usb 1-1.3: new low-speed USB device number 10 using ehci-pci
[94239.896671] usb 1-1.3: New USB device found, idVendor=154a, idProduct=0002
[94239.896675] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[94239.896678] usb 1-1.3: Product: Input Device
[94239.896681] usb 1-1.3: Manufacturer: ID Innovations Inc.
[94239.908080] input: ID Innovations Inc. Input Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input38
[94239.908263] hid-generic 0003:154A:0002.0029: input,hidraw1: USB HID v1.00 Keyboard       [ID Innovations Inc. Input Device] on usb-0000:00:1a.0-1.3/input0
[94249.918111] hid-generic 0003:154A:0002.002A: usb_submit_urb(ctrl) failed: -1
[94249.918137] hid-generic 0003:154A:0002.002A: timeout initializing reports
[94249.918513] hid-generic 0003:154A:0002.002A: hiddev0,hidraw3: USB HID v1.00 Device [ID Innovations Inc. Input Device] on usb-0000:00:1a.0-1.3/input1
[94357.731852] usb 1-1.3: USB disconnect, device number 10
[94357.960908] usb 1-1.3: new low-speed USB device number 11 using ehci-pci
[94358.059834] usb 1-1.3: New USB device found, idVendor=154a, idProduct=0002
[94358.059840] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[94358.059844] usb 1-1.3: Product: Input Device
[94358.059848] usb 1-1.3: Manufacturer: ID Innovations Inc.
[94358.068368] input: ID Innovations Inc. Input Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input39
[94358.068567] hid-generic 0003:154A:0002.002B: input,hidraw1: USB HID v1.00 Keyboard [ID Innovations Inc. Input Device] on usb-0000:00:1a.0-1.3/input0
[94358.080163] hid-generic 0003:154A:0002.002C: hiddev0,hidraw3: USB HID v1.00 Device [ID Innovations Inc. Input Device] on usb-0000:00:1a.0-1.3/input1
```

The keyboard doesn't work when I connect it and dmesg says "usb_submit_urb(ctrl) failed"

How do I fix this?

---

