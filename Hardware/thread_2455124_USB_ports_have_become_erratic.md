---
title: "USB ports have become erratic"
date: 2020-12-12
forum: Hardware
---

### Post by cscj01 on 2020-12-12
I am on Ubuntu 18.04.5 x64 with Gnome Flashback.  I have a Gigabyte Z77X-UD5H MB.  In the last few days, I have been having issues with my USB ports.  Sometimes my keyboard does not respond.  I have USB desktop HDs that work on ports at times and at other times they do not.  lsusb looks fine:```
 lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 007: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 006: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
Bus 001 Device 003: ID 04b8:0030 Seiko Epson Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 2109:8110 VIA Labs, Inc. Hub
Bus 004 Device 005: ID 1058:25a3 Western Digital Technologies, Inc. 
Bus 004 Device 004: ID 1058:10a8 Western Digital Technologies, Inc. Elements Portable (WDBUZG)
Bus 004 Device 002: ID 2109:8110 VIA Labs, Inc. Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04b0:4001 Nikon Corp. LS 50 ED/Coolscan V ED
Bus 003 Device 002: ID 04b8:013a Seiko Epson Corp. GT-X820 [Perfection V600 Photo]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```dmesg doesn't show any USB ports that couldn't be configured:```
[    3.479956] usb 4-3: new SuperSpeed Gen 1 USB device number 2 using xhci_hcd
[    3.503980] usb 4-3: New USB device found, idVendor=2109, idProduct=8110, bcdDevice=83.e1
[    3.503980] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.503980] usb 4-3: Product: 4-Port USB 3.0 Hub
[    3.503980] usb 4-3: Manufacturer: VIA Labs, Inc.
[    3.504034] hub 4-3:1.0: USB hub found
[    3.504042] hub 4-3:1.0: 4 ports detected
[    3.531974]  sde: sde1
[    3.532099] sd 7:0:0:0: [sde] Attached SCSI removable disk
[    3.563991] usb 1-1.2: New USB device found, idVendor=0baf, idProduct=0303, bcdDevice= 2.00
[    3.563991] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=10
[    3.563991] usb 1-1.2: Product: USB Modem
[    3.563991] usb 1-1.2: Manufacturer: U.S.Robotics
[    3.563991] usb 1-1.2: SerialNumber: 0000002
[    3.643972] usb 1-1.3: new low-speed USB device number 5 using ehci-pci
[    3.695976] usb 3-4: new high-speed USB device number 3 using xhci_hcd
[    3.755974] usb 1-1.3: New USB device found, idVendor=093a, idProduct=2510, bcdDevice= 1.00
[    3.755974] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.755974] usb 1-1.3: Product: USB Optical Mouse
[    3.755974] usb 1-1.3: Manufacturer: PixArt
[    3.761274] hidraw: raw HID events driver (C) Jiri Kosina
[    3.764060] usbcore: registered new interface driver usbhid
[    3.764060] usbhid: USB HID core driver
[    3.768031] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:093A:2510.0001/input/input1
[    3.768057] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1a.0-1.3/input0
[    3.835984] usb 1-1.4: new low-speed USB device number 6 using ehci-pci
[    3.912059] usb 3-4: New USB device found, idVendor=04b0, idProduct=4001, bcdDevice= 1.02
[    3.912059] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.912059] usb 3-4: Product: LS-50 ED
[    3.912059] usb 3-4: Manufacturer: Nikon
[    3.959983] usb 1-1.4: New USB device found, idVendor=046a, idProduct=0011, bcdDevice= 1.00
[    3.959983] usb 1-1.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.976146] input: HID 046a:0011 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:046A:0011.0002/input/input2
[    4.036034] hid-generic 0003:046A:0011.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0011] on usb-0000:00:1a.0-1.4/input0
[    4.116001] usb 1-1.5: new high-speed USB device number 7 using ehci-pci
[    4.156024]  sdd: sdd1
[    4.156105] sd 4:0:0:0: [sdd] Attached SCSI disk
[    4.224066] usb 1-1.5: New USB device found, idVendor=2109, idProduct=3431, bcdDevice=42.47
[    4.224066] usb 1-1.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    4.224066] usb 1-1.5: Product: USB2.0 Hub
[    4.224403] hub 1-1.5:1.0: USB hub found
[    4.224415] hub 1-1.5:1.0: 4 ports detected
[    4.316006] usb 1-1.6: new high-speed USB device number 8 using ehci-pci
[    4.424041] usb 1-1.6: New USB device found, idVendor=2109, idProduct=3431, bcdDevice=42.47
[    4.424041] usb 1-1.6: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    4.424041] usb 1-1.6: Product: USB2.0 Hub
[    4.424077] hub 1-1.6:1.0: USB hub found
[    4.424079] hub 1-1.6:1.0: 4 ports detected
[    4.940059] usb 4-4: new SuperSpeed Gen 1 USB device number 3 using xhci_hcd
[    4.960106] usb 4-4: New USB device found, idVendor=2109, idProduct=8110, bcdDevice=83.e1
[    4.960106] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.960106] usb 4-4: Product: 4-Port USB 3.0 Hub
[    4.960106] usb 4-4: Manufacturer: VIA Labs, Inc.
[    4.964071] hub 4-4:1.0: USB hub found
[    4.964083] hub 4-4:1.0: 4 ports detected
[    5.040067] usb 4-3.3: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd
[    5.060077] usb 4-3.3: New USB device found, idVendor=1058, idProduct=10a8, bcdDevice=10.42
[    5.060077] usb 4-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.060077] usb 4-3.3: Product: Elements 10A8
[    5.060077] usb 4-3.3: Manufacturer: Western Digital
[    5.060077] usb 4-3.3: SerialNumber: 575839314132345339303635
[    5.144084] usb 4-3.4: new SuperSpeed Gen 1 USB device number 5 using xhci_hcd
[    5.164102] usb 4-3.4: New USB device found, idVendor=1058, idProduct=25a3, bcdDevice=10.30
[    5.164102] usb 4-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.164102] usb 4-3.4: Product: Elements 25A3
[    5.164102] usb 4-3.4: Manufacturer: Western Digital
[    5.164102] usb 4-3.4: SerialNumber: 575832324432304A37593244
[    5.172213] usb-storage 4-3.3:1.0: USB Mass Storage device detected
[    5.173095] scsi host10: usb-storage 4-3.3:1.0
[    5.173095] usb-storage 4-3.4:1.0: USB Mass Storage device detected
[    5.173095] scsi host11: usb-storage 4-3.4:1.0
[    5.173095] usbcore: registered new interface driver usb-storage
[    5.173095] usbcore: registered new interface driver uas
```Any ideas on what may be going on?

---

### Post by vincelaconte on 2020-12-13
Same here - I'm on 20.10 with an amd64 and a Gigabyte mb (B450 AORUS Pro/Wifi) and the USB has been testy  under some recent kernels (I keep on the rolling HWE). At various times since 20.10 release

[LIST]
[*]USB keyboard intermittently does not load in BIOS (prior to login) - workaround: enabled Accessibility/Virtual Keyboard on greeter screen. i think the BIOS settings enabling Legacy USB and XHCI Handoff are a factor too, at least for my kbd. 
[*]Logitech USB Unifying receiver stopped recognizing or pairing with MX Master mouse over USB, continued working over Bluetooth. Then after another kernel update, Bluetooth pairing of MX Master would not persist reboot, and had to be re-paired  every time. FWIW eventually this seemed to fix the logitech + BT issues: [https://community.linuxmint.com/tutorial/view/703](https://community.linuxmint.com/tutorial/view/703) (move device listing in [FONT=lucida sans unicode]/lib/udev/rules.d/hid2hci.rules[/FONT]  under "hidraw" instead of "hiddev") 
[*]I also have several WD/Seagate/Toshiba external HDs over the USB hub(s), and the ones inside SATA enclosures add about 60-90 seconds (per drive) to boot, regardless of  BIOS or udev settings I've tried. 
[*]I set the Gigabyte mbs without any of that Fast Boot nonsense and generally leave Legacy BIOS/non-UEFI support turned on, in general that's been better for the various hardware, although sometimes the opposite is true. 
[*](HDA and HDMI audio drivers have also been intermittently silently failing to load, after working flawlessly under 18.x or 19.x.) 
[/LIST]
  FWIW!

---

