---
title: "USB HID device detected by kernel, but not usable"
date: 2009-10-08
forum: Hardware
---

### Post by aldoric on 2009-10-08
Hello,

I bought a hardware that uses USB HID drivers for communication.

After I insert it into my USB slot the kernel Log shows:
usb 4-2: new full speed USB device using uhci_hcd and address 38
usb 4-2: configuration #1 chosen from 1 choice
generic-usb 0003:155D:0002.00A1: hiddev96,hidraw1: USB HID v1.10 Device [I-removed-the-name-for-posting-USB-HID-DEV-01] on usb-0000:00:1a.1-2/input0

So, the USB device seems to be found correctly.
But, if I call "lsusb" the device is not listed:
Bus 002 Device 005: ID 07ca:a309 AVerMedia Technologies, Inc. 
Bus 002 Device 003: ID 0408:03ba Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

"lsusb -t" shows a "HID"
2-8:1.0: No such file or directory
6-1:1.0: No such file or directory
7-2:1.2: No such file or directory
7-2:1.3: No such file or directory
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 2: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 2: Dev 2, If 3, Class=app., Driver=, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 63, If 0, Class=HID, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 8: Dev 5, If 0, Class=vend., Driver=, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M

But "lsusb -v" does not show the device.

Using libhid I can not access the device (even as root).

Can someone tell me, how to analyse why this device is not accessable from applications and why it's not really detected?

On another PC it works for some reason.

Thanks in advance : D

---

