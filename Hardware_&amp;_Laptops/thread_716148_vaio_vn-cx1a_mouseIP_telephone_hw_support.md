---
title: "vaio vn-cx1a mouse/IP telephone hw support?"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by doddo on 2008-03-05
Hello! I got this vaio vn-cx1a usb connected mouse/Skype telephone from my mom a few days ago (a late christmas gift)

My issue is of course that I can not get the telephone part of the thing working. The mouse works like a charm

Has anyone of you similar issues? Is there a way to get this working under linux??

Here is the output of my dmesg when I've just connected the device
```

ehci_hcd 0000:00:02.1: GetStatus port 8 status 001803 POWER sig=j CSC CONNECT
hub 1-0:1.0: port 8, status 0501, change 0001, 480 Mb/s
hub 1-0:1.0: debounce: port 8: total 100ms stable 100ms status 0x501
ehci_hcd 0000:00:02.1: port 8 full speed --> companion
ehci_hcd 0000:00:02.1: GetStatus port 8 status 003001 POWER OWNER sig=se0 CONNECT
hub 1-0:1.0: port 8 not reset yet, waiting 50ms
ehci_hcd 0000:00:02.1: GetStatus port 8 status 003802 POWER OWNER sig=j CSC
hub 2-0:1.0: state 7 ports 10 chg 0000 evt 0100
ohci_hcd 0000:00:02.0: GetStatus roothub.portstatus [7] = 0x00010101 CSC PPS CCS
hub 2-0:1.0: port 8, status 0101, change 0001, 12 Mb/s
hub 2-0:1.0: debounce: port 8: total 100ms stable 100ms status 0x101
ohci_hcd 0000:00:02.0: GetStatus roothub.portstatus [7] = 0x00100103 PRSC PPS PES CCS
usb 2-8: new full speed USB device using ohci_hcd and address 6
ohci_hcd 0000:00:02.0: GetStatus roothub.portstatus [7] = 0x00100103 PRSC PPS PES CCS
usb 2-8: ep0 maxpacket = 8
usb 2-8: new device strings: Mfr=0, Product=0, SerialNumber=0
usb 2-8: uevent
usb 2-8: usb_probe_device
usb 2-8: configuration #1 chosen from 1 choice
usb 2-8: adding 2-8:1.0 (config #1, interface 0)
usb 2-8:1.0: uevent
usb 2-8:1.0: uevent
hub 2-8:1.0: usb_probe_interface
hub 2-8:1.0: usb_probe_interface - got id
hub 2-8:1.0: USB hub found
hub 2-8:1.0: 2 ports detected
hub 2-8:1.0: compound device; port removable status: FF
hub 2-8:1.0: individual port power switching
hub 2-8:1.0: individual port over-current protection
hub 2-8:1.0: power on to power good time: 100ms
hub 2-8:1.0: hub controller current requirement: 100mA
hub 2-8:1.0: 100mA bus power budget for each child
hub 2-8:1.0: enabling power on all ports
hub 2-8:1.0: individual port over-current protection
hub 2-8:1.0: power on to power good time: 100ms
hub 2-8:1.0: hub controller current requirement: 100mA
hub 2-8:1.0: 100mA bus power budget for each child
hub 2-8:1.0: enabling power on all ports
drivers/usb/core/inode.c: creating file '006'
hub 1-0:1.0: state 7 ports 10 chg 0000 evt 0100
hub 2-0:1.0: state 7 ports 10 chg 0000 evt 0100
hub 2-8:1.0: state 7 ports 2 chg 0000 evt 0000
hub 2-8:1.0: port 1, status 0101, change 0001, 12 Mb/s
hub 2-8:1.0: debounce: port 1: total 100ms stable 100ms status 0x101
usb 2-8.1: new full speed USB device using ohci_hcd and address 7
usb 2-8.1: ep0 maxpacket = 8
usb 2-8.1: skipped 1 descriptor after interface
usb 2-8.1: new device strings: Mfr=0, Product=0, SerialNumber=0
usb 2-8.1: uevent
usb 2-8.1: usb_probe_device
usb 2-8.1: configuration #1 chosen from 1 choice
usb 2-8.1: adding 2-8.1:1.0 (config #1, interface 0)
usb 2-8.1:1.0: uevent
usb 2-8.1:1.0: uevent
usbhid 2-8.1:1.0: usb_probe_interface
usbhid 2-8.1:1.0: usb_probe_interface - got id
input: HID 054c:028b as /class/input/input5
input: USB HID v1.00 Mouse [HID 054c:028b] on usb-0000:00:02.0-8.1
drivers/usb/core/inode.c: creating file '007'
hub 2-8:1.0: 300mA power budget left
hub 2-8:1.0: port 2, status 0101, change 0001, 12 Mb/s
hub 2-8:1.0: debounce: port 2: total 100ms stable 100ms status 0x101
usb 2-8.2: new full speed USB device using ohci_hcd and address 8
usb 2-8.2: skipped 7 descriptors after interface
usb 2-8.2: skipped 2 descriptors after interface
usb 2-8.2: skipped 1 descriptor after endpoint
usb 2-8.2: skipped 2 descriptors after interface
usb 2-8.2: skipped 1 descriptor after endpoint
usb 2-8.2: skipped 1 descriptor after interface
usb 2-8.2: new device strings: Mfr=0, Product=0, SerialNumber=0
usb 2-8.2: uevent
usb 2-8.2: usb_probe_device
usb 2-8.2: configuration #1 chosen from 1 choice
usb 2-8.2: adding 2-8.2:1.0 (config #1, interface 0)
usb 2-8.2:1.0: uevent
usb 2-8.2:1.0: uevent
usb 2-8.2: adding 2-8.2:1.1 (config #1, interface 1)
usb 2-8.2:1.1: uevent
usb 2-8.2:1.1: uevent
usb 2-8.2: adding 2-8.2:1.2 (config #1, interface 2)
usb 2-8.2:1.2: uevent
usb 2-8.2:1.2: uevent
usb 2-8.2: adding 2-8.2:1.3 (config #1, interface 3)
usb 2-8.2:1.3: uevent
usb 2-8.2:1.3: uevent
usbhid 2-8.2:1.3: usb_probe_interface
usbhid 2-8.2:1.3: usb_probe_interface - got id
input: HID 054c:028d as /class/input/input6
input: USB HID v1.00 Device [HID 054c:028d] on usb-0000:00:02.0-8.2
drivers/usb/core/inode.c: creating file '008'
hub 2-8:1.0: 200mA power budget left
hub 2-8:1.0: state 7 ports 2 chg 0000 evt 0004

```

---

