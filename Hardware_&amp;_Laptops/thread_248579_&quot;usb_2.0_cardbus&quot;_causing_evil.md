---
title: "&quot;usb 2.0 cardbus&quot; causing evil"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by jas20 on 2006-09-01
I have a "Swann usb 2.0 cardbus" card. It seems to cause my wireless (ralink rt2500, also cardbus) to go weird.

I also suspect it's the reason why my keyboard "locksup" sometimes when I pull it out to try to get the wireless working again.

I've already updated the driver for the ralink card to fix that problem, but now this USB card is, is there an updated driver?

Here is a chop out of what I get from inserting the card, to the end of dmesg:
```
[17194679.468000] pccard: CardBus card inserted into slot 1
[17194681.908000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17194681.908000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[17194681.912000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [C142] -> GSI 11 (level, low) -> IRQ 11
[17194681.912000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17194681.912000] ohci_hcd 0000:06:00.0: OHCI Host Controller
[17194681.912000] ohci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 2
[17194681.912000] ohci_hcd 0000:06:00.0: irq 11, io mem 0x16000000
[17194681.996000] hub 2-0:1.0: USB hub found
[17194681.996000] hub 2-0:1.0: 3 ports detected
[17194682.100000] PCI: Enabling device 0000:06:00.1 (0000 -> 0002)
[17194682.100000] ACPI: PCI Interrupt 0000:06:00.1[B] -> Link [C142] -> GSI 11 (level, low) -> IRQ 11
[17194682.100000] PCI: Setting latency timer of device 0000:06:00.1 to 64
[17194682.100000] ohci_hcd 0000:06:00.1: OHCI Host Controller
[17194682.100000] ohci_hcd 0000:06:00.1: new USB bus registered, assigned bus number 3
[17194682.100000] ohci_hcd 0000:06:00.1: irq 11, io mem 0x16001000
[17194682.196000] hub 3-0:1.0: USB hub found
[17194682.196000] hub 3-0:1.0: 2 ports detected
[17194682.304000] PCI: Enabling device 0000:06:00.2 (0000 -> 0002)
[17194682.308000] ACPI: PCI Interrupt 0000:06:00.2[C] -> Link [C142] -> GSI 11 (level, low) -> IRQ 11
[17194682.308000] ehci_hcd 0000:06:00.2: EHCI Host Controller
[17194682.332000] ehci_hcd 0000:06:00.2: new USB bus registered, assigned bus number 4
[17194682.332000] ehci_hcd 0000:06:00.2: irq 11, io mem 0x16002000
[17194682.332000] ehci_hcd 0000:06:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17194682.332000] hub 4-0:1.0: USB hub found
[17194682.332000] hub 4-0:1.0: 5 ports detected
[17194881.336000] ohci_hcd 0000:06:00.1: HC died; cleaning up
[17194881.336000] ehci_hcd 0000:06:00.2: HC died; cleaning up
[17197825.612000] ohci_hcd 0000:06:00.0: HC died; cleaning up
[17197825.612000] pccard: card ejected from slot 1
[17197825.648000] ohci_hcd 0000:06:00.0: remove, state 0
[17197825.648000] usb usb2: USB disconnect, address 1
[17197825.648000] ohci_hcd 0000:06:00.0: USB bus 2 deregistered
[17197825.648000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[17197825.648000] ohci_hcd 0000:06:00.1: remove, state 0
[17197825.648000] usb usb3: USB disconnect, address 1
[17197825.648000] ohci_hcd 0000:06:00.1: USB bus 3 deregistered
[17197825.648000] ACPI: PCI interrupt for device 0000:06:00.1 disabled
[17197825.648000] ehci_hcd 0000:06:00.2: remove, state 0
[17197825.648000] usb usb4: USB disconnect, address 1
[17197825.672000] ehci_hcd 0000:06:00.2: USB bus 4 deregistered
[17197825.672000] ACPI: PCI interrupt for device 0000:06:00.2 disabled
```

Any ideas?

---

