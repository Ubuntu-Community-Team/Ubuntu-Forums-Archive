---
title: "Can't Find IRQ For USB Port"
date: 2012-09-03
forum: Hardware
---

### Post by frigginpenguin on 2012-09-03
Hey folks,

I've done as much homework as I could on this issue before posting, so I'll try and include all the necessary details.

First of all, my USB port is in working physical condition.  It works under Windows and also worked in Xubuntu 8.10.  Once I upgraded to 12.04, I was no longer able to use it.  The error given by lsusb was a -99 initialization error for the libusb library.

Upon further investigation with dmesg, I noted the following pertinent information:
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ohci_hcd USB 1.1 'Open' Host Controller (OHCI) Driver
uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:07.2: can't find IRQ for PCI INT D; please try using pci=biosirq
uhci_hcd 0000:00:07.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:07.2 setup!
uhci_hcd 0000:00:07.2: init 0000:00:07.2 fail, -19
usbcore: registered new interface driver libusual

Clearly there is an issue involving ACPI compatibility between my BIOS and Xubuntu 12.04.  I have the latest available BIOS firmware, and the setup does not have settings for the USB port or legacy/pnp operating systems, so I'm SOL on that end.

I have tried various combinations of boot options, turning ACPI and APIC on and off, using biosirq and noirq and so on, nothing seems to have hit the spot yet.

I ran lshw and got the following:
*-usb UNCLAIMED
description: USB controller
product 82371AB/EB/MB PIIX4 USB
vendor: Intel Corporation
physical id: 7.2
bus info: pci@0000:00:07.2
version: 01
width: 32 bits
clock: 33MHz
capabilities: uhci
configuration: latency=64
resources: ioport:fcc0(size=32)
*-bridge:1
description: Bridge
product 82371AB/EB/MB PIIX4 ACPI
vendor: Intel Corporation
physical id: 7.3
bus info: pci@0000:00:07.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: bridge
configuration: driver=piix4_smbus latency=0
resources: irq:9

So that's where I'm at, I think all the pieces are there, I'm just hoping someone can help me put them together, being a novice Linux user.

Thanks in advance to anyone who can help!

---

### Post by TheFu on 2012-09-03
First I want to thank you for trying to be as helpful as you have been.  You appear to have provided relevant data for the issue at hand. Nice job.

Before delving too deep into irqs and drivers, I'll ask some other questions for clarification:
* Do all the USB ports fail the same way? Try the front and back ports.
* Which specific USB devices have you tried?
* Could a bad USB cable be involved?
* Did you do an upgrade install or a fresh new install?

Based on the output, you should use ACPI, IRQ 9 and a PIIX4 driver.  Do the messages in dmesg and syslog show that?

What does **lsusb -v** say?  Any buses and devices seen?

---

### Post by frigginpenguin on 2012-09-03
Thanks right back, that was an amazingly fast response!  I really appreciate the fact that folks give up their time like this to help one another, but then again, I guess that's what open source is all about :)

First off, there is only one USB port, so we don't have much to work with in that regard.

I've tried to get a variety of devices working, including a thumb drive, external hard drive, and other storage devices, but the one of highest importance is my network adapter.  As you know, network access is a pretty essential component of installing various packages as one custom-builds a linux installation.  

I know that the cable is not the issue, the network adapter doesn't have one and the cables for the storage devices have been swapped and verified as working.

The installation was fresh onto a blank hard drive.

ACPI is indeed enabled, and while dmesg shows the bridge on irq 9, the usb controller shows up as unclaimed with ioport:fcc0 for resources instead of an irq.

lsusb -v yields the same results as lsusb alone (unable to initialize libusb: -99)

Thanks again for your help, please let me know if you need any further information.

---

### Post by aaronLund on 2012-11-29
I can't offer help and am only leaving a comment to watch this thread.

I'm in a similar situation.

---

