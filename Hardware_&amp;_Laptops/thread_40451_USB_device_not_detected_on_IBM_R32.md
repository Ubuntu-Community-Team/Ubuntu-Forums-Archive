---
title: "USB device not detected on IBM R32"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by peter.butler on 2005-06-09
My IBM R32 laptop has two USB ports.  When I plug a device (e.g. USB mouse) into one port, it is detected properly, the driver loaded and the device works.  dmesg shows:

usb 2-1: new low speed USB device using uhci_hcd and address 14
input: USB HID v1.10 Mouse [KYE EasyTrack Optical U+P] on usb-0000:00:1d.1-1

However, when I plug the same device into the second USB port, the following appears in dmesg:

usb 2-2: new low speed USB device using uhci_hcd and address 12
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71
usb 2-2: new low speed USB device using uhci_hcd and address 13
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71

I read elsewhere that I should try the kernel parameter "pci=noacpi" but this has not fixed the problem.  This USB port works in Windows XP, so it's not a hardware problem.

Does anyone have any ideas on how to fix this?

Thanks in advance

Peter Butler

Update:
I added the following to /etc/modprobe.d/usbcore.modprobe:

options usbcore old_scheme_first=Y use_both_schemes=Y

This now gives the following error in dmesg:
usb 2-2: new low speed USB device using uhci_hcd and address 9
usb 2-2: device not accepting address 9, error -71
usb 2-2: new low speed USB device using uhci_hcd and address 10
usb 2-2: device not accepting address 10, error -71
usb 2-2: new low speed USB device using uhci_hcd and address 11
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71
usb 2-2: new low speed USB device using uhci_hcd and address 12
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71

I've googled around for advice on this but haven't had any luck.  Anyone got any ideas?

Cheers

Peter

---

