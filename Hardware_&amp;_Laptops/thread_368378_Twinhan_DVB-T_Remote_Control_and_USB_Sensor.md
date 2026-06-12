---
title: "Twinhan DVB-T Remote Control and USB Sensor"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by kafkaian on 2007-02-23
Interesting issue with the usb sensor/remote control for my Twinhan VisionPlus DVB bt878 PCI Card.

With the sensor installed on system power up the boot sequence hangs. 

With the sensor plugged in after logging into gnome, it works! But of course the mapping is wrong.

Anyone recommend how I should approach this on my Dapper system and to get it recognised without hanging the system on boot up?


[quote="dmesg"][17180202.384000] usb 3-2: new low speed USB device using uhci_hcd and address 2[17180202.660000] usbcore: registered new driver hiddev
[17180202.684000] input: Twinhan Tech Remote Control as /class/input/input3
[17180202.684000] input: USB HID v1.10 Keyboard [Twinhan Tech Remote Control] on usb-0000:00:1d.2-2
[17180202.708000] input: Twinhan Tech Remote Control as /class/input/input4
[17180202.708000] input: USB HID v1.10 Mouse [Twinhan Tech Remote Control] on usb-0000:00:1d.2-2
[17180202.708000] usbcore: registered new driver usbhid
[17180202.708000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver[/quote]

---

