---
title: "USB 2 EHCI Host Controller FAILURE"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by Tallowwood on 2006-11-21
Hi all

Just starting with edgy 6.10. Have spent a few days trying to get PCI USB 2 Host Controller working. Tried various devices - power is ok but device not seen. USB 1 HC is working as expected. Seems to be a hardware issue. dmsg says:

ACPI: PCI Interrupt 0000:02:0b.2[C] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:02:0b.2: EHCI Host Controller
ehci_hcd 0000:02:0b.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:02:0b.2: irq 11, io mem 0xe0000000
ehci_hcd 0000:02:0b.2: startup error -19
ehci_hcd 0000:02:0b.2: USB bus 1 deregistered
ACPI: PCI interrupt for device 0000:02:0b.2 disabled
ehci_hcd 0000:02:0b.2: init 0000:02:0b.2 fail, -19

google does not seem to know about startup error -19
 
Any advice on how to fix this?

---

