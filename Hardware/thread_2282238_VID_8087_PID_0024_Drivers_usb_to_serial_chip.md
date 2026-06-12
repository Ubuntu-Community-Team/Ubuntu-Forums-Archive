---
title: "VID 8087 PID 0024 Drivers usb to serial chip"
date: 2015-06-12
forum: Hardware
---

### Post by ibod on 2015-06-12
Hi, 

I have a usb to serial chip in a ham radio programming cable and can't get Ubuntu 14.04 to recognise the cable.

lsusb shows no change when the cable is plugged in.

I have managed to find the VID 8087 and PID 0024 in a windows pc that also does not recognise the cable.

Thanks for any help or guidance.

Ibod

---

### Post by Yellow Pasque on 2015-06-12
That's probably the VID/PID of the USB controller.
```
8087  Intel Corp.
	0020  Integrated Rate Matching Hub
	0024  Integrated Rate Matching Hub
```

Does dmesg show anything after plugging it in?
```
dmesg
```

---

### Post by ibod on 2015-06-12
Hi

Clean boot and before the cable is plugged in 

```

$ dmesg | grep -i usb
[    0.147597] ACPI: bus type USB registered
[    0.147597] usbcore: registered new interface driver usbfs
[    0.147597] usbcore: registered new interface driver hub
[    0.147597] usbcore: registered new device driver usb
[    0.835336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.835508] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.844029] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.844073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.844075] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.844078] usb usb1: Product: EHCI Host Controller
[    0.844080] usb usb1: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    0.844082] usb usb1: SerialNumber: 0000:00:02.1
[    0.844202] hub 1-0:1.0: USB hub found
[    0.844486] ehci-pci 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.856026] ehci-pci 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.856058] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.856060] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.856063] usb usb2: Product: EHCI Host Controller
[    0.856065] usb usb2: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    0.856066] usb usb2: SerialNumber: 0000:00:04.1
[    0.856170] hub 2-0:1.0: USB hub found
[    0.856323] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.856458] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.914048] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.914050] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.914052] usb usb3: Product: OHCI PCI host controller
[    0.914054] usb usb3: Manufacturer: Linux 3.13.0-44-generic ohci_hcd
[    0.914056] usb usb3: SerialNumber: 0000:00:02.0
[    0.914152] hub 3-0:1.0: USB hub found
[    0.914429] ohci-pci 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.970048] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.970050] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.970052] usb usb4: Product: OHCI PCI host controller
[    0.970054] usb usb4: Manufacturer: Linux 3.13.0-44-generic ohci_hcd
[    0.970056] usb usb4: SerialNumber: 0000:00:04.0
[    0.970157] hub 4-0:1.0: USB hub found
[    0.970311] uhci_hcd: USB Universal Host Controller Interface driver
$ 

```

and after the cable is plugged in 

```

$ dmesg | grep -i usb
[    0.147597] ACPI: bus type USB registered
[    0.147597] usbcore: registered new interface driver usbfs
[    0.147597] usbcore: registered new interface driver hub
[    0.147597] usbcore: registered new device driver usb
[    0.835336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.835508] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.844029] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.844073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.844075] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.844078] usb usb1: Product: EHCI Host Controller
[    0.844080] usb usb1: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    0.844082] usb usb1: SerialNumber: 0000:00:02.1
[    0.844202] hub 1-0:1.0: USB hub found
[    0.844486] ehci-pci 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.856026] ehci-pci 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.856058] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.856060] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.856063] usb usb2: Product: EHCI Host Controller
[    0.856065] usb usb2: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    0.856066] usb usb2: SerialNumber: 0000:00:04.1
[    0.856170] hub 2-0:1.0: USB hub found
[    0.856323] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.856458] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.914048] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.914050] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.914052] usb usb3: Product: OHCI PCI host controller
[    0.914054] usb usb3: Manufacturer: Linux 3.13.0-44-generic ohci_hcd
[    0.914056] usb usb3: SerialNumber: 0000:00:02.0
[    0.914152] hub 3-0:1.0: USB hub found
[    0.914429] ohci-pci 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.970048] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.970050] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.970052] usb usb4: Product: OHCI PCI host controller
[    0.970054] usb usb4: Manufacturer: Linux 3.13.0-44-generic ohci_hcd
[    0.970056] usb usb4: SerialNumber: 0000:00:04.0
[    0.970157] hub 4-0:1.0: USB hub found
[    0.970311] uhci_hcd: USB Universal Host Controller Interface driver
[   62.004045] usb 3-1: new full-speed USB device number 2 using ohci-pci
[   62.184042] usb 3-1: device descriptor read/64, error -62
[   62.468033] usb 3-1: device descriptor read/64, error -62
[   62.748034] usb 3-1: new full-speed USB device number 3 using ohci-pci
[   62.928035] usb 3-1: device descriptor read/64, error -62
[   63.212036] usb 3-1: device descriptor read/64, error -62
[   63.492049] usb 3-1: new full-speed USB device number 4 using ohci-pci
[   63.900024] usb 3-1: device not accepting address 4, error -62
[   64.076034] usb 3-1: new full-speed USB device number 5 using ohci-pci
[   64.484028] usb 3-1: device not accepting address 5, error -62
[   64.484061] hub 3-0:1.0: unable to enumerate USB device on port 1
$ 


```

---

### Post by Yellow Pasque on 2015-06-12
It appears you're using a port that only has USB 1.1 capability (or at least is being initialized that way). Have you tried using different USB ports? Does the device need USB 2.0 features? Any more info you can give on the device might help.

---

### Post by ibod on 2015-06-13
> **Temüjin said:**
> It appears you're using a port that only has USB 1.1 capability (or at least is being initialized that way). Have you tried using different USB ports? Does the device need USB 2.0 features? Any more info you can give on the device might help.

Hi 

Have now tried all ports on the PC 4X rear panel 2X front panel. With no luck.
I have No info on the device. I bought it on Ebay as a programming cable for my Radio
More Info below.

Computer:-
The Motherboard is a MCP78PVM-PM Rev 1.1 
OS is Ubuntu 14.04 LTS 32bit
Memory 3GB 
Processor AMD Phenom 9550 Quad core 
A re-cased Packard Bell iMedia 2426 Desktop PC

Cable:-
The Device in question is a programming cable for a Ham Radio.
It has a USB on one end and plugs into the radios Head Phone and Mic sockets at the other end 
The USB end has a usb to serial chip built in to convert the levels to and from the radio
All tests have been with the radio disconnected 

Radio:- 
Baofeng UV-5R+Plus

USB Ports:-
The board spec states 4X USB 2.0 ports on the read panel and internal 2X USB Headers (one of these is used for the front panel USB sockets. The spec does not specify the headers as 1.1 or 2.0.

Spec at [http://www.findlaptopdriver.com/specs-mcp78pvm-pm-ecs-mainboard/](http://www.findlaptopdriver.com/specs-mcp78pvm-pm-ecs-mainboard/)

Output from lsusb 

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$ 

```

It looks like some ports are being initialized as 1.1 when they are all 2.0

If I plug a USB memory stick into a port it connects as a USB 2.0 using ehci-pci
If I plug the cable into the same port dmesg shows it as using ohci-pci and it is not listed in lsusb

Hope some of this helps 

Ibod

---

