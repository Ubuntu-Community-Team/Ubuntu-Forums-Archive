---
title: "iFox HSPA USB Modem (air card) - desperately need help"
date: 2010-02-05
forum: Hardware
---

### Post by ktulhu on 2010-02-05
Hello!

I bought the subj 2 days ago and tried everything (including all tutorials on 3G and air cars) and it simply does not work.

At first the card was shown as usb mass-storage device, but ffter installing usb_modswitch package - kubuntu was silent.

No linux drivers were found on the mass-storage (however, the manufacturer claims it's should work under linux; only win and mac drivers are there).

The card works perfectly under Win7 (using the drivers) and Win7 reports "Qualcomm Configuration" device in the device list and the driver provider is "Mobile Connector".

Below you will find some info I gathered:

```
lsusb
Bus 006 Device 002: ID 046d:c052 Logitech, Inc.
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp.
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 17ef:4807 Lenovo
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1c9e:f000
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-------------------------

usr/sbin/usb_modeswitch -v 0x1c9e -p 0xf000

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 000 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry

Device description data (identification)
-------------------------
Error: could not get description string "manufacturer"
Manufacturer:
Error: could not get description string "product"
     Product:
Error: could not get description string "serial number"
  Serial No.:
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.


---------------

  dmesg | grep usb
[    0.234556] usbcore: registered new interface driver usbfs
[    0.234556] usbcore: registered new interface driver hub
[    0.234556] usbcore: registered new device driver usb
[    0.944074] usb usb1: configuration #1 chosen from 1 choice
[    0.964065] usb usb2: configuration #1 chosen from 1 choice
[    0.964812] usb usb3: configuration #1 chosen from 1 choice
[    0.964988] usb usb4: configuration #1 chosen from 1 choice
[    0.965686] usb usb5: configuration #1 chosen from 1 choice
[    0.966914] usb usb6: configuration #1 chosen from 1 choice
[    0.967090] usb usb7: configuration #1 chosen from 1 choice
[    0.967269] usb usb8: configuration #1 chosen from 1 choice
[    1.480059] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.618228] usb 1-6: configuration #1 chosen from 1 choice
[    1.784047] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.919048] usb 2-2: configuration #1 chosen from 1 choice
[    2.164920] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.229896] usbcore: registered new interface driver usb-storage
[    2.229943] usb-storage: device found at 3
[    2.229944] usb-storage: waiting for device to settle before scanning
[    2.338029] usb 4-1: configuration #1 chosen from 1 choice
[    2.580044] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    2.749027] usb 4-2: configuration #1 chosen from 1 choice
[    3.000538] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    3.178948] usb 6-1: configuration #1 chosen from 1 choice
[    3.196064] usbcore: registered new interface driver hiddev
[    3.211071] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input6
[    3.211120] generic-usb 0003:046D:C052.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1d.0-1/input0
[    3.211131] usbcore: registered new interface driver usbhid
[    3.211132] usbhid: v2.6:USB HID core driver
[    7.228673] usb-storage: device scan complete
[   18.010562] usbcore: registered new interface driver btusb
[   18.027778] input: UVC Camera (17ef:4807) as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8
[   18.027815] usbcore: registered new interface driver uvcvideo
[  194.063005] usbcore: registered new interface driver usbserial
[  194.063050] usbcore: registered new interface driver usbserial_generic
[  194.063051] usbserial: USB Serial Driver core
[  205.538366] usb 2-2: USB disconnect, address 3
[  219.164126] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  219.299383] usb 2-2: configuration #1 chosen from 1 choice
[  219.301364] usb-storage: device found at 4
[  219.301369] usb-storage: waiting for device to settle before scanning
[  273.920648] usb 2-2: USB disconnect, address 4
[  288.364175] usb 2-2: new high speed USB device using ehci_hcd and address 5
[  288.499343] usb 2-2: configuration #1 chosen from 1 choice
[  288.519968] usb-storage: device found at 5
[  288.519973] usb-storage: waiting for device to settle before scanning
[  471.435870] usb 2-2: USB disconnect, address 5
[  490.956086] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  491.091504] usb 2-2: configuration #1 chosen from 1 choice
[  491.104704] usb-storage: device found at 6
[  491.104710] usb-storage: waiting for device to settle before scanning
[  546.865730] usb 2-2: USB disconnect, address 6
[  563.772096] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  563.907354] usb 2-2: configuration #1 chosen from 1 choice
[  563.921887] usb-storage: device found at 7
[  563.921892] usb-storage: waiting for device to settle before scanning

------------------
```

ANY help would be greatly appreciated. Thanks!

UPD: Here's the official page of the device [http://www.ifoxonline.com/product-detail.php?ProductID=66](http://www.ifoxonline.com/product-detail.php?ProductID=66)

---

