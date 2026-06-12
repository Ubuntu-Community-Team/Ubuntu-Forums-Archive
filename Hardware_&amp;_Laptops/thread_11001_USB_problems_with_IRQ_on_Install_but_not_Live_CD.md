---
title: "USB problems with IRQ on Install but not Live CD"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by phill on 2005-01-13
I've just installed Warty on my new HP laptop (AMD 64 running in 386 mode) and I'm having great deal of trouble with my USB setup.  The live warty CD recognises the USB properly, here are the appropriate bits from dmesg:

> ACPI: Subsystem revision 20040326
ACPI: Interpreter disabled.

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
ohci_hcd 0000:00:02.0: nVidia Corporation nForce3 USB 1.1
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 11, pci mem e0b17000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ohci_hcd 0000:00:02.1: nVidia Corporation nForce3 USB 1.1 (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 10, pci mem e0b2a000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ieee1394: Initialized config rom entry `ip1394'
usb 2-1: new full speed USB device using address 2
hub 2-1:1.0: USB hub found
hub 2-1:1.0: 4 ports detected
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[e0108000-e01087ff]  Max Packet=[2048]
usb 2-1.1: new full speed USB device using address 3
usb 2-1.1: can't connect bus-powered hub to this port
usb 2-1.2: new low speed USB device using address 4
usb 2-1.3: new full speed USB device using address 5
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4c3f02004c3f0200]usb 2-1.4: new full speed USB device using address 6
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.1-1.2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver


However having installed Warty using the install CD there seems to be a problem initialising my USB ports:

> ACPI: Subsystem revision 20040816
ACPI: Interpreter enabled

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low)
-> IRQ 11
ohci_hcd 0000:00:02.0: nVidia Corporation nForce3 USB 1.1
ohci_hcd 0000:00:02.0: USB HC TakeOver failed!
ohci_hcd 0000:00:02.0: can't reset
ohci_hcd 0000:00:02.0: init 0000:00:02.0 fail, -1
ohci_hcd: probe of 0000:00:02.0 failed with error -1
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 10 (level, low)
-> IRQ 10
ohci_hcd 0000:00:02.1: nVidia Corporation nForce3 USB 1.1 (#2)
ohci_hcd 0000:00:02.1: USB HC TakeOver failed!
ohci_hcd 0000:00:02.1: can't reset
ohci_hcd 0000:00:02.1: init 0000:00:02.1 fail, -1
ohci_hcd: probe of 0000:00:02.1 failed with error -1
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid



The laptop doesn't seem to have a problem recognising the USB 2 ports though (the Live CD picks them up fine too):

> 
ehci_hcd 0000:00:02.2: nVidia Corporation nForce3 USB 2.0
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 10, pci mem e09cd000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1 (***live CD gives this bus number 3***)
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 6 ports detected


Can anyone help me get my USB 1.1 ports working please?  I don't understand why it is having a problem initialising the ohci module...

BTW here's the current lsusb:

Bus 001 Device 001: ID 0000:0000  (the USB2 port)

and here's what it should look like

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 011: ID 04bf:0320 TDK Corp.
Bus 002 Device 010: ID 0bda:8150 Realtek Semiconductor Corp. RTL8150 Fast Ethernet Adapter
Bus 002 Device 009: ID 046d:c016 Logitech, Inc.
Bus 002 Device 007: ID 05e3:0604 Genesys Logic, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


Also the modules loaded between the two system were not quite identical.  The install CD never loaded uhci-hcd or hci_usb but adding them to /etc/modules made no difference to the start up.

Thanks.

---

### Post by phill on 2005-01-13
There is of course the short term fix is to add acpi=off to the kernel line of /boot/grub/menu.lst however that means I loose all acpi features such as battery monitoring :-(

---

### Post by phill on 2005-01-17
Hmm.  My salvation came in the words "BIOS Update".  It seems the HP nx9105 with bios F30 has issues with USB under Win2k and that was solved with a new bios shipped 14 days later.  Sadly my machine was built during that window :-(

---

