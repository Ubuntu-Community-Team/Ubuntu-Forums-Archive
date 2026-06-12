---
title: "Hardy Heron ata long boot"
date: 2008-05-09
forum: Hardware
---

### Post by User420 on 2008-05-09
Newly installed ubuntu hardy takes very long time to boot compared to the previous installed gutsy.
Examination of the dmesg output shows that there appears to be a problem with the ata drive identification.
```
[   23.745586] ACPI: Thermal Zone [THRM] (75 C)
[   24.068591] SCSI subsystem initialized
[   24.084906] usbcore: registered new interface driver usbfs
[   24.084933] usbcore: registered new interface driver hub
[   24.084948] libata version 3.00 loaded.
[   24.086351] usbcore: registered new device driver usb
[   24.089766] sata_sil 0000:00:12.0: version 2.3
[   24.089837] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   24.090934] scsi0 : sata_sil
[   24.091013] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.091088] scsi1 : sata_sil
[   24.091299] ata1: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 17
[   24.091303] ata2: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 17
[   24.156009] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.156018] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.165350] 8139too Fast Ethernet driver 0.9.28
[   24.555908] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   24.637306] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   24.637310] ata1: failed to recover some devices, retrying in 5 secs
[   30.111685] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   30.181458] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   30.181463] ata1: failed to recover some devices, retrying in 5 secs
[   35.653480] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   35.723252] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   35.723256] ata1: failed to recover some devices, retrying in 5 secs
[   41.196277] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   41.663833] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   41.745152] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   41.745156] ata2: failed to recover some devices, retrying in 5 secs
[   47.218620] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   47.288503] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   47.288506] ata2: failed to recover some devices, retrying in 5 secs
[   52.761416] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   52.831191] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[   52.831195] ata2: failed to recover some devices, retrying in 5 secs
[   58.305208] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   58.305322] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16

```

Reading some threads suggest several solutions such as using irqpoll in the grub, no suggestion fixed the problem.
Does anyone encounter this issue and a solution ?

---

