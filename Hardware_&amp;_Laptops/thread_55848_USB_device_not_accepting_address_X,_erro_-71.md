---
title: "USB: device not accepting address X, erro -71"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by tommie-lie on 2005-08-10
Hi,

I recently bought an external USB2.0 HDD case with a Cypress controller (CY7C68300A-56PVC) and a USB2.0 PCI host controller with NEC chipset, as my mainboard only has USB1.1 hubs and I was not satisfied with the transfer rate of full speed USB.
When I plug the HDD in, the kernel gives out the following error messages:
```
usb 3-5: new high speed USB device using ehci_hcd and address 5
usb 3-5: device not accepting address 5, error -71
usb 3-5: new high speed USB device using ehci_hcd and address 6
usb 3-5: device not accepting address 6, error -71
```And so on, with increasing address numbers.
The drive works fine on the on-board USB connectors (USB1.1) and even on the NEC controller if I disable the EHCI driver, however, in full speed mode, of course.
The problem seems known, but none of the provided solutions work for me (Murphy must have known me). It can be an IRQ problem and it is often proposed to boot with acpi=off, noapic or pci=routeirq or other parameters concerning IRQ routing, but none helped. Having had problems with IRQs [earlier](http://ubuntuforums.org/showthread.php?t=19150), I upgraded to the current Breezy kernel (2.6.12-6.8), as a newer kernel seemed to solve the problem for some people. Well, the IRQ problem indeed was solved, but the USB error with USB remains the same.
I found out that the error code -71 stands for EPROTO, which is a protocol error, but that does not help me very much solving this problem.
Unfortunately I don't have another USB2.0 device to test with, so I can only say that the controller itself works for USB1.1 devices (e.g. my mouse or the disk in full speed mode). The drive also seems to be okay, it works fine on a Laptop (Toshiba M30X) running Hoary but with the current Breezy kernel.

I hope someone had similar problems and solved them somehow, or also has a NEC controller running high speed USB devices.


Thanks in advance
Thomas

---

### Post by tommie-lie on 2005-08-17
The problem was a defective USB controller card. I exchanged it with a new one of the same kind and it worked.
Thanks to Alan Stern who helped me to find that out. ;-)

---

