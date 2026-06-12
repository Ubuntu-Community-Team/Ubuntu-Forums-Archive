---
title: "The bluetooth dongle from Logitech doesnt seem to work"
date: 2009-06-14
forum: Hardware
---

### Post by Hund on 2009-06-14
I bought the Logitech DiNovo Mini keyboard the other day and everything works very well. But I cant use the bluetooth in Ubuntu, I would like to pair my mobile phone with my computer but when I open the bluetooth manager everything is just greyed out? I have no idéa what to do?

Output from lsusb:

> Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 046d:c71f Logitech, Inc. 
Bus 007 Device 003: ID 046d:c71e Logitech, Inc. 
Bus 007 Device 002: ID 046d:0b07 Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 002 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Output from dmesg:

> [...]
[    4.791023] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input4
[    4.812544] input,hidraw3: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.2
[    4.824061] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input5
[    4.864110] input,hiddev96,hidraw4: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.3
[    4.864126] usbcore: registered new interface driver usbhid
[    4.864128] usbhid: v2.6:USB HID core driver
[...]

---

