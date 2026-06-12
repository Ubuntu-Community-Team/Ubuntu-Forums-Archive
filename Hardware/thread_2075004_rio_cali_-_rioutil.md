---
title: "rio cali - rioutil"
date: 2012-10-22
forum: Hardware
---

### Post by webdesigncompanyla on 2012-10-22
I've got Ubuntu 12.04.01 installed and rioutil 1.5x installed, but I get this error when running it:

rioutil -l
Attempting to open Rio and retrieve song list.... failed!
Reason: No such file or directory.
librioutil tried to use method: libusb

same thing with sudo


sudo rioutil -l
[sudo] password for user1: 
Attempting to open Rio and retrieve song list.... failed!
Reason: No such file or directory.
librioutil tried to use method: libusb




I  don't mind using a command line to load songs to my Rio Cali but I  can't get it to work.  I have two very nice Rio Cali's and I would love  to get Linux to manage them but I might have to revert back to Windows  if Linux is not up to the task.

Any ideas on how to get my computer to interface with the Rio Cali device in my case?

> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser



> dmesg | grep -i USB
[    0.393720] usbcore: registered new interface driver usbfs
[    0.393720] usbcore: registered new interface driver hub
[    0.393720] usbcore: registered new device driver usb
[    0.803918] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.804067] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.816018] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.816151] hub 1-0:1.0: USB hub found
[    0.816253] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.816352] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.874103] hub 2-0:1.0: USB hub found
[    0.874194] uhci_hcd: USB Universal Host Controller Interface driver
[    0.874243] usbcore: registered new interface driver libusual
[    1.184029] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.319798] Initializing USB Mass Storage driver...
[    1.319938] scsi6 : usb-storage 1-8:1.0
[    1.320082] usbcore: registered new interface driver usb-storage
[    1.320085] USB Mass Storage support registered.
[    1.320229] usbcore: registered new interface driver uas
[    1.620020] usb 2-4: new low-speed USB device number 2 using ohci_hcd
[    1.842954] generic-usb 0003:058F:6362.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:02.1-8/input1
[    1.843046] usbcore: registered new interface driver usbhid
[    1.843048] usbhid: USB HID core driver
[    2.305277] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input2
[    2.305375] logitech 0003:046D:C517.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-4/input0
[    2.315625] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input3
[    2.315765] logitech 0003:046D:C517.0003: input,hiddev0,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4/input1
[    2.320789] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.321279] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.321775] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    2.322274] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[14581.320049] usb 2-6: new low-speed USB device number 3 using ohci_hcd
[14581.500037] usb 2-6: device descriptor read/64, error -62
[14581.784044] usb 2-6: device descriptor read/64, error -62
[14582.064047] usb 2-6: new low-speed USB device number 4 using ohci_hcd
[14582.244048] usb 2-6: device descriptor read/64, error -62
[14582.528048] usb 2-6: device descriptor read/64, error -62
[14582.808042] usb 2-6: new low-speed USB device number 5 using ohci_hcd
[14583.216036] usb 2-6: device not accepting address 5, error -62
[14583.392038] usb 2-6: new low-speed USB device number 6 using ohci_hcd
[14583.800036] usb 2-6: device not accepting address 6, error -62
[14583.800053] hub 2-0:1.0: unable to enumerate USB device on port 6
[14693.992049] hub 1-0:1.0: unable to enumerate USB device on port 6
[14826.564053] usb 2-6: new low-speed USB device number 7 using ohci_hcd
[14826.744049] usb 2-6: device descriptor read/64, error -62
[14827.028037] usb 2-6: device descriptor read/64, error -62
[14827.308050] usb 2-6: new low-speed USB device number 8 using ohci_hcd
[14827.488043] usb 2-6: device descriptor read/64, error -62
[14827.772045] usb 2-6: device descriptor read/64, error -62
[14828.052029] usb 2-6: new low-speed USB device number 9 using ohci_hcd
[14828.460038] usb 2-6: device not accepting address 9, error -62
[14828.636052] usb 2-6: new low-speed USB device number 10 using ohci_hcd
[14829.044028] usb 2-6: device not accepting address 10, error -62
[14829.044049] hub 2-0:1.0: unable to enumerate USB device on port 6
[14908.632055] hub 2-0:1.0: unable to enumerate USB device on port 6
[16080.124044] usb 2-6: new low-speed USB device number 12 using ohci_hcd
[16080.308035] usb 2-6: device descriptor read/64, error -62
[16080.596049] usb 2-6: device descriptor read/64, error -62
[16080.876051] usb 2-6: new low-speed USB device number 13 using ohci_hcd
[16081.060050] usb 2-6: device descriptor read/64, error -62
[16081.348044] usb 2-6: device descriptor read/64, error -62
[16081.628036] usb 2-6: new low-speed USB device number 14 using ohci_hcd
[16082.036039] usb 2-6: device not accepting address 14, error -62
[16082.212055] usb 2-6: new low-speed USB device number 15 using ohci_hcd
[16082.620017] usb 2-6: device not accepting address 15, error -62
[16082.620032] hub 2-0:1.0: unable to enumerate USB device on port 6


---

