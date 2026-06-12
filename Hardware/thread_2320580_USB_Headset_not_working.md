---
title: "USB Headset not working"
date: 2016-04-15
forum: Hardware
---

### Post by Henrique_Cunha on 2016-04-15
Hello, I've been trying to get my headset to work on Ubuntu 14.04 LTS.
It doesn't show on sound settings.

Here's what lsusb looks like:
```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 0c45:64ad Microdia 
Bus 003 Device 006: ID 0cf3:e004 Atheros Communications, Inc. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1c4f:0034 SiGma Micro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And "dmesg | grep usb":
```

[    0.198402] usbcore: registered new interface driver usbfs
[    0.198411] usbcore: registered new interface driver hub
[    0.198430] usbcore: registered new device driver usb
[    0.626622] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.626626] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.626630] usb usb1: Product: xHCI Host Controller
[    0.626633] usb usb1: Manufacturer: Linux 3.19.0-58-generic xhci-hcd
[    0.626636] usb usb1: SerialNumber: 0000:00:14.0
[    0.627568] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.627570] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.627571] usb usb2: Product: xHCI Host Controller
[    0.627573] usb usb2: Manufacturer: Linux 3.19.0-58-generic xhci-hcd
[    0.627575] usb usb2: SerialNumber: 0000:00:14.0
[    0.642468] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.642472] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.642475] usb usb3: Product: EHCI Host Controller
[    0.642478] usb usb3: Manufacturer: Linux 3.19.0-58-generic ehci_hcd
[    0.642481] usb usb3: SerialNumber: 0000:00:1a.0
[    0.658544] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.658547] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.658550] usb usb4: Product: EHCI Host Controller
[    0.658552] usb usb4: Manufacturer: Linux 3.19.0-58-generic ehci_hcd
[    0.658553] usb usb4: SerialNumber: 0000:00:1d.0
[    0.938406] usb 1-3: new low-speed USB device number 2 using xhci_hcd
[    0.954402] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    0.970384] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    1.086731] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
[    1.086734] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.103103] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
[    1.103107] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.126982] usb 1-3: New USB device found, idVendor=1c4f, idProduct=0034
[    1.126985] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.126986] usb 1-3: Product: Usb Mouse
[    1.126988] usb 1-3: Manufacturer: SIGMACHIP
[    1.127076] usb 1-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.133162] usbcore: registered new interface driver usbhid
[    1.133164] usbhid: USB HID core driver
[    1.134345] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:1C4F:0034.0001/input/input7
[    1.134476] hid-generic 0003:1C4F:0034.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-3/input0
[    1.358185] usb 3-1.3: new high-speed USB device number 3 using ehci-pci
[    1.450984] usb 3-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    1.450988] usb 3-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.450991] usb 3-1.3: Product: USB2.0-CRW
[    1.450993] usb 3-1.3: Manufacturer: Generic
[    1.450994] usb 3-1.3: SerialNumber: 20100201396000000
[    1.522134] usb 3-1.4: new full-speed USB device number 4 using ehci-pci
[    1.619553] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=e004
[    1.619557] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.619560] usb 3-1.4: Product: Bluetooth USB Host Controller
[    1.619562] usb 3-1.4: Manufacturer: Atheros Communications
[    1.619564] usb 3-1.4: SerialNumber: Alaska Day 2006
[    1.690080] usb 3-1.6: new high-speed USB device number 5 using ehci-pci
[    1.858700] usb 3-1.6: New USB device found, idVendor=0c45, idProduct=64ad
[    1.858705] usb 3-1.6: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.858708] usb 3-1.6: Product: Laptop_Integrated_Webcam_HD
[    1.858710] usb 3-1.6: Manufacturer: CN0Y3PX872487379A0B6A01
[    2.043302] usbcore: registered new interface driver rtsx_usb
[    2.112329] usbcore: registered new interface driver btusb
[    2.121811] usbcore: registered new interface driver ath3k
[    2.224112] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.6/3-1.6:1.0/input/input11
[    2.224228] usbcore: registered new interface driver uvcvideo
[  356.066306] usb 1-3: USB disconnect, device number 2
[  363.390925] usb 1-3: new low-speed USB device number 3 using xhci_hcd
[  363.523271] usb 1-3: New USB device found, idVendor=1c4f, idProduct=0034
[  363.523275] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  363.523276] usb 1-3: Product: Usb Mouse
[  363.523277] usb 1-3: Manufacturer: SIGMACHIP
[  363.523418] usb 1-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  363.525825] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:1C4F:0034.0002/input/input15
[  363.578942] hid-generic 0003:1C4F:0034.0002: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-3/input0
[  454.117916] usb 3-1.4: USB disconnect, device number 4
[  460.331623] usb 3-1.4: new full-speed USB device number 6 using ehci-pci
[  460.425490] usb 3-1.4: New USB device found, idVendor=0cf3, idProduct=e004
[  460.425493] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  460.425495] usb 3-1.4: Product: Bluetooth USB Host Controller
[  460.425496] usb 3-1.4: Manufacturer: Atheros Communications
[  460.425497] usb 3-1.4: SerialNumber: Alaska Day 2006

```

And "cat /proc/asound/cards"
```
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7910000 irq 33

```



Anyone can help?

---

### Post by mörgæs on 2016-04-16
Hi, welcome to the fora.
How does it work in a live boot of 16.04?

---

