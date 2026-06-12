---
title: "dapper irq wireless problem"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by predator29 on 2006-06-03
hi there,
i've a problem with my wireless card, in amilo a7640. it worked fine in breezy, with ndiswrapper. it's working on dapper, but not with network manager. i have to write the options manually. this wouldn't be a problem, but then why is there nm :D
so, the solution of getting alive the card in breezy was removing the prism54 module from kernel, and there everything went fine.
now the solution is nearly the same, but dapper not installed the prism54 modul either the islsm modules. the problem wont be really big, but three devices are on the same irq. when i unload the module islsm_pci from my kernel got the following in dmesg:
[4294819.736000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[4294819.737000] Unloaded islsm_pci driver
that means the dirver is unloaded. then i want to load the ndiswrapper driver, and my apic goes crazy:
[4295649.388000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[4295649.470000] ndiswrapper: driver prisma00 (Conexant,07/20/2004, 2.1.25.0) loaded
[4295649.470000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 209
[4295649.471000] ndiswrapper: using irq 209
[4295650.399000] APIC error on CPU0: 00(40)
and the error continues.
i think this is due to the wrong apic, or i dunno. there are 3 devices on same irq, and when unloading the module it disables the interreupts i think. than wanna to load a module on the same irq, and due to this my apic goes crazy.
i tryed acpi=noirq, then the ndiswrapper module's malloc gone wrong, and there were memory prolems with it, if i try the noapic boot parameter my gnome won't log in, and plays severeal times the gdm sound (still some problem with irq's i think).
my interrupt table is:
           CPU0
  0:    1292819    IO-APIC-edge  timer
  1:       7776    IO-APIC-edge  i8042
  8:          3    IO-APIC-edge  rtc
 10:        712   IO-APIC-level  acpi
 12:     118269    IO-APIC-edge  i8042
 14:       8101    IO-APIC-edge  ide0
 15:      22433    IO-APIC-edge  ide1
169:         14   IO-APIC-level  yenta, yenta
177:        822   IO-APIC-level  SiS SI7012
185:          0   IO-APIC-level  ohci_hcd:usb1
193:          0   IO-APIC-level  ohci_hcd:usb2
201:          0   IO-APIC-level  ehci_hcd:usb3
209:      10508   IO-APIC-level  ohci1394, eth0, ndiswrapper
NMI:          0
LOC:    1291529
ERR:        324
MIS:          0
the strange thin is that card sometimes is working if i mannually scan, and give the parameters to iwconfig. but with network manager notthing happens. the error mesages periodically continues...
i dunno how to solve this problem. my laptops bios suxx, there isn't any settings...

---

