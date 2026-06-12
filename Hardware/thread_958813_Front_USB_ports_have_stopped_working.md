---
title: "Front USB ports have stopped working"
date: 2008-10-25
forum: Hardware
---

### Post by mistergoomba on 2008-10-25
Hello, everyone. I have a Powerspec 7114 and have had Ubuntu 8.04 on it for a while. The hardware didn't agree with me at first, but apparently changing my boot command fixed the issue.

After having Linux for almost a year, all of a sudden the USB Ports in front have stopped working. Nothing being plugged in is recognized. There are no issues with the ports in back.

If anyone knows how to fix this, it would be greatly appreciated.

---

### Post by ddrichardson on 2008-10-25
Is there anything in dmesg?

---

### Post by mistergoomba on 2008-10-26
There was over 2000 lines of output: [http://pastebin.com/mb2026db](http://pastebin.com/mb2026db)

---

### Post by ddrichardson on 2008-10-26
Do you remove USB devices without unmounting them a lot?

Try plugging in a device to the front port and typing:
```
dmesg | grep -i usb
```

---

### Post by mistergoomba on 2008-10-26
the family unplugs usb drives quite frequently without unmounting

```
[   40.934877] usbcore: registered new interface driver usbfs
[   40.934909] usbcore: registered new interface driver hub
[   40.934960] usbcore: registered new device driver usb
[   40.936256] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.936631] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   40.995713] usb usb1: configuration #1 chosen from 1 choice
[   40.995747] hub 1-0:1.0: USB hub found
[   41.100483] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   41.159286] usb usb2: configuration #1 chosen from 1 choice
[   41.159324] hub 2-0:1.0: USB hub found
[   41.241012] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   41.464571] usb 2-2: configuration #1 chosen from 1 choice
[   41.808882] usbcore: registered new interface driver hiddev
[   41.492722] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input1
[   41.520266] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.1-2
[   41.533465] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.1/input/input2
[   41.544189] input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.1-2
[   41.544210] usbcore: registered new interface driver usbhid
[   41.544215] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.231530] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   43.242652] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.242805] usb usb3: configuration #1 chosen from 1 choice
[   43.242839] hub 3-0:1.0: USB hub found
[   42.976424] usb 2-2: USB disconnect, address 2
[   43.774297] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   43.998064] usb 2-2: configuration #1 chosen from 1 choice
[   44.010221] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.0/input/input3
[   44.033662] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.1-2
[   44.046999] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.1/usb2/2-2/2-2:1.1/input/input4
[   44.065578] input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.1-2
[   73.575849] usb 3-1: new high speed USB device using ehci_hcd and address 3
[   73.709784] usb 3-1: configuration #1 chosen from 1 choice
[   73.860593] usbcore: registered new interface driver libusual
[   73.882339] Initializing USB Mass Storage driver...
[   73.885472] scsi4 : SCSI emulation for USB Mass Storage devices
[   73.887725] usbcore: registered new interface driver usb-storage
[   73.887734] USB Mass Storage support registered.
[   73.889301] usb-storage: device found at 3
[   73.889305] usb-storage: waiting for device to settle before scanning
[   78.874098] usb-storage: device scan complete
[   78.875477] scsi 4:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[  469.637850] usb 3-1: USB disconnect, address 3
[  473.343419] usb 3-1: new high speed USB device using ehci_hcd and address 4
[  473.477322] usb 3-1: configuration #1 chosen from 1 choice
[  473.481038] scsi5 : SCSI emulation for USB Mass Storage devices
[  473.493146] usb-storage: device found at 4
[  473.493152] usb-storage: waiting for device to settle before scanning
[  478.482149] usb-storage: device scan complete
[  478.808479] scsi 5:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[  514.566414] usb 3-1: USB disconnect, address 4
[  521.839756] usb 3-2: new high speed USB device using ehci_hcd and address 5
[  521.973629] usb 3-2: configuration #1 chosen from 1 choice
[  521.996497] scsi6 : SCSI emulation for USB Mass Storage devices
[  522.003911] usb-storage: device found at 5
[  522.003917] usb-storage: waiting for device to settle before scanning
[  526.990374] usb-storage: device scan complete
[  526.991607] scsi 6:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[  882.054042] usb 3-2: USB disconnect, address 5
[  885.618072] usb 3-1: new high speed USB device using ehci_hcd and address 6
[  885.751934] usb 3-1: configuration #1 chosen from 1 choice
[  885.755427] scsi7 : SCSI emulation for USB Mass Storage devices
[  885.759665] usb-storage: device found at 6
[  885.759672] usb-storage: waiting for device to settle before scanning
[  890.748767] usb-storage: device scan complete
[  890.750009] scsi 7:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[25740.383573] usb 3-1: USB disconnect, address 6
[84426.964809] usb 2-3: new full speed USB device using ohci_hcd and address 4
[84427.144338] usb 2-3: device descriptor read/64, error -62
[84427.428758] usb 2-3: device descriptor read/64, error -62
[84427.690905] usb 2-3: new full speed USB device using ohci_hcd and address 5
[84427.870427] usb 2-3: device descriptor read/64, error -62
[84428.153686] usb 2-3: device descriptor read/64, error -62
[84428.432950] usb 2-3: new full speed USB device using ohci_hcd and address 6
[84428.839943] usb 2-3: device not accepting address 6, error -62
[84429.015413] usb 2-3: new full speed USB device using ohci_hcd and address 7
[84429.423863] usb 2-3: device not accepting address 7, error -62

```

---

### Post by ddrichardson on 2008-10-26
Is the front port connected properly? Is it part of the mainboard or connected to a card? Did you have a recent kernel update? Is it only this pendrive that is problematic?

The fact that it isn't getting an address and was working, suggests a possible hardware issue.

---

