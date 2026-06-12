---
title: "USB 3 drive not recognized"
date: 2017-04-08
forum: Hardware
---

### Post by shoeleshunter78 on 2017-04-08
I just moved from Kubuntu 16.10 to Ubuntu 16.10. In the process, my USB 3 drive is no longer recognized by the system using fdisk or gsmartcontrol, for example.

dmesg | grep USB

```
[    0.419963] ACPI: bus type USB registered[    1.806227] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.806328] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.820825] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.820915] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.820919] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.821078] hub 1-0:1.0: USB hub found
[    1.821300] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.836828] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.836919] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.836922] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.837151] hub 2-0:1.0: USB hub found
[    1.837388] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.852784] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.852870] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.852874] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.853058] hub 3-0:1.0: USB hub found
[    1.853186] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.853264] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.916803] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.916805] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.916965] hub 4-0:1.0: USB hub found
[    1.917149] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.980807] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.980809] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.980974] hub 5-0:1.0: USB hub found
[    1.981163] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.044807] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.044809] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.044969] hub 6-0:1.0: USB hub found
[    2.045117] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.108834] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.108836] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.108995] hub 7-0:1.0: USB hub found
[    2.109121] uhci_hcd: USB Universal Host Controller Interface driver
[    2.109192] xhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 8
[    2.436791] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    2.627914] usb 4-1: New USB device found, idVendor=0a12, idProduct=0001
[    2.627916] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.920841] usb 4-2: new low-speed USB device number 3 using ohci-pci
[    3.108912] usb 4-2: New USB device found, idVendor=045e, idProduct=00d1
[    3.108916] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.400875] usb 4-4: new full-speed USB device number 4 using ohci-pci
[    3.593982] usb 4-4: New USB device found, idVendor=046d, idProduct=c52b
[    3.593983] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.593984] usb 4-4: Product: USB Receiver
[   19.043838] xhci_hcd 0000:01:00.0: USB bus 8 deregistered
[   19.043954] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[   35.729502] xhci_hcd 0000:03:00.0: USB bus 8 deregistered
[   35.833246] usbhid: USB HID core driver
[   35.845548] hid-generic 0003:045E:00D1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:12.0-2/input0
[   35.850327] logitech-djreceiver 0003:046D:C52B.0004: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-4/input2
[   35.991392] logitech-hidpp-device 0003:046D:401B.0005: input,hidraw2: USB HID v1.11 Mouse [Logitech M215 2nd Gen] on usb-0000:00:12.0-4:1
[   36.011464] logitech-hidpp-device 0003:046D:4016.0006: input,hidraw3: USB HID v1.11 Keyboard [Logitech K330] on usb-0000:00:12.0-4:2
```


lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't know why moving laterally between Ubuntu distros would affect this, but it has. The drive has critical data, but I don't want to install Kubuntu just to access it.

---

### Post by oldfred on 2017-04-09
Not familiar with issue, but my lsusb from Ubuntu 16.04 shows another driver for USB3.

fred@Z170N:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

What brand/model system or what motherboard? 
Some require boot parameters to enable USB3 ports. And Gigabyte has IOMMU settings that need to be changed. Full UEFI update resets to defaults, so if updating UEFI you may have to change IOMMU setting again.

---

