---
title: "8-second startup delay"
date: 2009-06-06
forum: Hardware
---

### Post by kabe2007 on 2009-06-06
Hi all,

I am getting a 8 second delay when starting up. See dmesg output below (partial). I am using a Gateway P7811-fx laptop. Ubuntu 9.04 64 bit, kernel 2.6.28-generic

It seems it is something related to the ACPI. 

Any help or hints are appreciated. 

Thanks!

-----------
dmesg output (partial):

[    1.970438] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4200000-0xf42fffff]
[    1.970477] bus 00 -> node 0
[    1.970489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.970905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    1.971159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.971415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.971619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.971818] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.972036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    9.972617] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    9.972814] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    9.973008] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
[    9.973199] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    9.973391] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    9.973588] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    9.973780] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    9.973972] ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
[    9.974293] ACPI: WMI: Mapper loaded
[    9.974340] SCSI subsystem initialized
[    9.974340] libata version 3.00 loaded.
[    9.974340] usbcore: registered new interface driver usbfs
[    9.974340] usbcore: registered new interface driver hub

---

