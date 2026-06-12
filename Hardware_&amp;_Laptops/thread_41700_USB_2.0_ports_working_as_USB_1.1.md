---
title: "USB 2.0 ports working as USB 1.1"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by bae22 on 2005-06-14
I recently installed Ubuntu 5.04 on my new Acer 1522WLMi laptop. Everything is working perfectly, except the USB ports.

I have 4 USB2 ports on the back of the laptop. Looking in Device Manager or USBview, it does show up as a USB2 VIA interface (with 6 ports supposedly). However, there are also three entries for;

VT82xxxxx UHCI USB 1.1 controller

each with 2 ports. Anything connected to my first two USB ports seems to connect to the first USB 1.1 controller, and the other two ports to the second 1.1 controller.

I have tried only plugging in my devices that are USB2 (and they are recognised as such), but they still connect to the USB 1.1 interface.

I have heard talk of using the "noapic" option at bootup, but this just caused the bootup to hang shortly after it said "starting hotplug system", so that doesn't help.

The relevant part of dmesg is;

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0x1c20
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0x1c40
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0x1c60
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xc0006800
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
irda_init()
NET: Registered protocol family 23
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4050710123b]
usbcore: registered new driver hiddev
usbhid: probe of 1-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 1-1: USB disconnect, address 2


Also, does bit help?
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:05: ioport range 0x600-0x60f has been reserved
pnp: 00:05: ioport range 0x1c0-0x1cf has been reserved
pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:05: ioport range 0xfe10-0xfe11 could not be reserved


The output from "lsmod | grep -i usb" is

usb_storage            64064  0
usblp                  12032  0
usbhid                 29376  0
usbcore               107384  6 usb_storage,usblp,usbhid,ehci_hcd,uhci_hcd
scsi_modat t              119936  4 sd_mod,usb_storage,sr_mod,sbp2
ide_core              118988  5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk

So the ehci mdule is loaded, and it seems happy enough to recognise the USB2 interface, but not let anyting connect.

If anyone has any ideas I would be very grateful!!

---

### Post by bae22 on 2005-06-16
Please, does anyone have any idea about this problem?

I can supply more logs if that will help anyone.

---

