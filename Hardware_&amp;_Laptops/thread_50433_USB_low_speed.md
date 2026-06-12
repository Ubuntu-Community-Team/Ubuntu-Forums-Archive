---
title: "USB low speed"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by kwisatz on 2005-07-20
Hi, I've my Ubuntu installed on my HP Laptop (DV1000), everything works fine but I have a little problem, Ubuntu sees my USB 2.0 ports as 1.1 low speed ports! 
This is a dmesg | grep usb output: 

usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 2-1: new low speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [CHESEN USB MOUSE] on usb-0000:00:1d.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 2-1: USB disconnect, address 2
usb 2-1: new low speed USB device using uhci_hcd and address 3
input: USB HID v1.10 Mouse [CHESEN USB MOUSE] on usb-0000:00:1d.1-1

My USB memory are very slow...
With usbview I see:
- Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
- Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
- Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
- Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3

The last three are usb 1.1...
I know that my USB ports are 2.0 and my USB device works perfectly, but should I do for using my devices at full speed?
Thanks in advance,

Matteo

---

### Post by luca_linux on 2005-07-21
Type lsmod and see if UHCI modules are loaded.

---

### Post by muriloq on 2006-10-31
> **luca_linux said:**
> Type lsmod and see if UHCI modules are loaded.

I'm having the same problem, but it only occurs with my DVD drive. An external USB hard disk is working flawlessly. 

I don't have the module UHCI installed, but I have EHCI and OCHI:

$ lsmod | grep -i hci
ehci_hcd               34696  0
ohci_hcd               22532  0
usbcore               134912  6 usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd

Do you know where I can learn more about these modules, and about how USB support is implemented ?

---

### Post by muriloq on 2006-11-01
I've found the origin of my problem: ACPI support. After turning it off (in BIOS setup, changing "ACPI Aware OS" to "No"), all the USB devices were correctly detected. 

The DVD-ROM drive (ID 0402:5621 ALi Corp. USB 2.0 Storage Device) sometimes isn't detected, but turning it off and then on again solves the problem.

In order to verify easily if everything is alright I'm using the utility usbview. The USB 2.0 devices should be listed under EHCI, and their speed should be 480 Mb/s.

---

