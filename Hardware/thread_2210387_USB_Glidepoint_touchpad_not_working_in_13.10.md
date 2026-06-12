---
title: "USB Glidepoint touchpad not working in 13.10"
date: 2014-03-10
forum: Hardware
---

### Post by pdesjardins on 2014-03-10
Hi. I am using a System76 laptop with Ubuntu 13.10. I just bought a Cirque glidepoint USB touchpad (model GP-160UB) but it does not work at all. I do not see a pointer and neither button has any effect I can see. A different USB pointer (optical mouse) works just fine.

This is surprising for me because I have been using a much older USB Cirque touchpad for many years on my Ubuntu 12.04 desktop. Also, I see that other people solved similar problems with this touchpad in 2011 ([http://ubuntuforums.org/showthread.php?t=1803492](http://ubuntuforums.org/showthread.php?t=1803492)).

I've tried using each of the USB ports, no success. The software updater reports that there are no updates available.

Does anyone know what else I can try to make this USB touchpad work?

Thanks!

Peter

This is what I see in the output of the dmesg command when I plug the touchpad into a USB port.

[16536.125818] usb 3-1: new full-speed USB device number 17 using xhci_hcd
[16536.144249] usb 3-1: New USB device found, idVendor=0488, idProduct=0280
[16536.144262] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[16536.144270] usb 3-1: Product: 9925 AG Touchpad
[16536.144277] usb 3-1: Manufacturer: Cirque Corporation
[16536.144554] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[16536.146380] input: Cirque Corporation 9925 AG Touchpad as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input28
[16536.146804] hid-generic 0003:0488:0280.0010: input,hidraw0: USB HID v1.11 Mouse [Cirque Corporation 9925 AG Touchpad] on usb-0000:00:14.0-1/input0

---

