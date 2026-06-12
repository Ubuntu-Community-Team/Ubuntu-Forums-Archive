---
title: "Vantec pci usb card not being detected or not detecting usb drives in ubuntu 18"
date: 2019-01-26
forum: Hardware
---

### Post by mcilie on 2019-01-26
So i bought this usb pcie card. It has 2 usb 3 type A ports and 1 usb type c port. It is called the Vantec 3-Port USB 3.0 Type-A/C PCIe Host Card. I installed it in my system (in a pcie 2.0 slot), disabled legacy usb compatibility in BIOS ( as suggested by another post), and when I boot Ubuntu 18 and plug in a flash drive, The flash drive is not recognized. Nothing is. Here are some error logs and information, How do I fix this? Thanks in advance:
`lspci | grep -i usb`: 
===


    00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 06)
    00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 06)
    01:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
    81:00.2 USB controller: NVIDIA Corporation Device 1ad6 (rev a1)


`lsusb`:
===


    Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 003: ID 046b:ff10 American Megatrends, Inc. Virtual Keyboard and Mouse
    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 004: ID 046d:c537 Logitech, Inc. 
    Bus 001 Device 003: ID 413c:301d Dell Computer Corp. 
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


`demsg| grep -i usb`:
====


    [    1.133850] ACPI: bus type USB registered
    [    1.133850] usbcore: registered new interface driver usbfs
    [    1.133850] usbcore: registered new interface driver hub
    [    1.133850] usbcore: registered new device driver usb
    [    3.373011] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    [    3.373321] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
    [    3.392069] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
    [    3.392135] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
    [    3.392136] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.392138] usb usb1: Product: EHCI Host Controller
    [    3.392140] usb usb1: Manufacturer: Linux 4.15.0-43-generic ehci_hcd
    [    3.392141] usb usb1: SerialNumber: 0000:00:1a.0
    [    3.392396] hub 1-0:1.0: USB hub found
    [    3.392767] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
    [    3.412065] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
    [    3.412126] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
    [    3.412127] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.412129] usb usb2: Product: EHCI Host Controller
    [    3.412130] usb usb2: Manufacturer: Linux 4.15.0-43-generic ehci_hcd
    [    3.412132] usb usb2: SerialNumber: 0000:00:1d.0
    [    3.412403] hub 2-0:1.0: USB hub found
    [    3.412587] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
    [    3.412649] uhci_hcd: USB Universal Host Controller Interface driver
    [    3.412880] xhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 3
    [    3.413224] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
    [    3.413226] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.413228] usb usb3: Product: xHCI Host Controller
    [    3.413229] usb usb3: Manufacturer: Linux 4.15.0-43-generic xhci-hcd
    [    3.413231] usb usb3: SerialNumber: 0000:01:00.0
    [    3.413461] hub 3-0:1.0: USB hub found
    [    3.413555] xhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 4
    [    3.413559] xhci_hcd 0000:01:00.0: Host supports USB 3.0  SuperSpeed
    [    3.413571] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
    [    3.413589] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
    [    3.413591] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.413593] usb usb4: Product: xHCI Host Controller
    [    3.413595] usb usb4: Manufacturer: Linux 4.15.0-43-generic xhci-hcd
    [    3.413596] usb usb4: SerialNumber: 0000:01:00.0
    [    3.413818] hub 4-0:1.0: USB hub found
    [    3.414296] xhci_hcd 0000:81:00.2: new USB bus registered, assigned bus number 5
    [    3.415083] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
    [    3.415085] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.415087] usb usb5: Product: xHCI Host Controller
    [    3.415088] usb usb5: Manufacturer: Linux 4.15.0-43-generic xhci-hcd
    [    3.415090] usb usb5: SerialNumber: 0000:81:00.2
    [    3.415373] hub 5-0:1.0: USB hub found
    [    3.415535] xhci_hcd 0000:81:00.2: new USB bus registered, assigned bus number 6
    [    3.415539] xhci_hcd 0000:81:00.2: Host supports USB 3.10 Enhanced SuperSpeed
    [    3.415562] usb usb6: We don't know the algorithms for LPM for this host, disabling LPM.
    [    3.415583] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
    [    3.415584] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
    [    3.415586] usb usb6: Product: xHCI Host Controller
    [    3.415587] usb usb6: Manufacturer: Linux 4.15.0-43-generic xhci-hcd
    [    3.415588] usb usb6: SerialNumber: 0000:81:00.2
    [    3.415825] hub 6-0:1.0: USB hub found
    [    3.744037] usb 1-1: new high-speed USB device number 2 using ehci-pci
    [    3.752038] usb 3-1: new high-speed USB device number 2 using xhci_hcd
    [    3.752040] usb 2-1: new high-speed USB device number 2 using ehci-pci
    [    3.900358] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
    [    3.900360] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
    [    3.900664] hub 1-1:1.0: USB hub found
    [    3.908359] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
    [    3.908361] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
    [    3.908875] hub 2-1:1.0: USB hub found
    [    4.188121] usb 1-1.4: new full-speed USB device number 3 using ehci-pci
    [    4.208112] usb 2-1.4: new full-speed USB device number 3 using ehci-pci
    [    4.300472] usb 1-1.4: New USB device found, idVendor=413c, idProduct=301d
    [    4.300495] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [    4.300497] usb 1-1.4: Product: Dell Universal Receiver
    [    4.300498] usb 1-1.4: Manufacturer: Dell
    [    4.312166] usbcore: registered new interface driver usbhid
    [    4.312167] usbhid: USB HID core driver
    [    4.314979] input: Dell Dell Universal Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:413C:301D.0001/input/input2
    [    4.332712] usb 2-1.4: New USB device found, idVendor=046b, idProduct=ff10
    [    4.332714] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
    [    4.332715] usb 2-1.4: Product: Virtual Keyboard and Mouse
    [    4.332716] usb 2-1.4: Manufacturer: American Megatrends Inc.
    [    4.332717] usb 2-1.4: SerialNumber: serial
    [    4.334004] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:046B:FF10.0004/input/input3
    [    4.372234] hid-generic 0003:413C:301D.0001: input,hidraw0: USB HID v1.11 Keyboard [Dell Dell Universal Receiver] on usb-0000:00:1a.0-1.4/input0
    [    4.372338] hid-generic 0003:046B:FF10.0004: input,hidraw1: USB HID v1.10 Keyboard [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1d.0-1.4/input0
    [    4.372448] input: Dell Dell Universal Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:413C:301D.0002/input/input4
    [    4.373680] input: American Megatrends Inc. Virtual Keyboard and Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/0003:046B:FF10.0005/input/input5
    [    4.384083] usb 1-1.6: new full-speed USB device number 4 using ehci-pci
    [    4.432507] hid-generic 0003:413C:301D.0002: input,hidraw2: USB HID v1.11 Mouse [Dell Dell Universal Receiver] on usb-0000:00:1a.0-1.4/input1
    [    4.432789] hid-generic 0003:046B:FF10.0005: input,hidraw3: USB HID v1.10 Mouse [American Megatrends Inc. Virtual Keyboard and Mouse] on usb-0000:00:1d.0-1.4/input1
    [    4.432910] hid-generic 0003:413C:301D.0003: hiddev0,hidraw4: USB HID v1.11 Device [Dell Dell Universal Receiver] on usb-0000:00:1a.0-1.4/input2
    [    4.499597] usb 1-1.6: New USB device found, idVendor=046d, idProduct=c537
    [    4.499629] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [    4.499630] usb 1-1.6: Product: USB Receiver
    [    4.499631] usb 1-1.6: Manufacturer: Logitech
    [    4.501747] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:046D:C537.0006/input/input6
    [    4.502065] hid-generic 0003:046D:C537.0006: input,hidraw5: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/input0
    [    4.504422] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/0003:046D:C537.0007/input/input7
    [    4.564370] hid-generic 0003:046D:C537.0007: input,hiddev1,hidraw6: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/input1
    [    9.052364] usb 3-1: device descriptor read/64, error -110
    [   24.668362] usb 3-1: device descriptor read/64, error -110
    [   37.488110] usb 4-2: device not accepting address 2, error -108
    [   37.488189] usb usb4-port2: couldn't allocate usb_device
    [   37.488210] usb usb3-port1: attempt power cycle
    [   37.804096] usb usb3-port1: couldn't allocate usb_device
    [   38.942510] audit: type=1400 audit(1548516972.984:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=795 comm="apparmor_parser"`

---

### Post by DuckHook on 2019-01-26
Please don't duplicate posts as this confuses those trying to help and dilutes community effort.

*Thread Closed.*

---

