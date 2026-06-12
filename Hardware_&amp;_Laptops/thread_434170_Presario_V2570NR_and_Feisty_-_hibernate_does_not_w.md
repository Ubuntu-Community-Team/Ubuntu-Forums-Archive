---
title: "Presario V2570NR and Feisty - hibernate does not work"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by xundaman on 2007-05-05
**[size=3]Here is the /var/log/syslog (bolded on what seems to be the error):[/size]**

```
May  5 18:45:48 chuck-laptop kernel: [ 2429.444000] Stopping tasks ... done.
May  5 18:45:48 chuck-laptop kernel: [ 2429.792000] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^Hdone (55697 pages freed)
May  5 18:45:48 chuck-laptop kernel: [ 2437.436000] Freed 222788 kbytes in 7.66 seconds (29.08 MB/s)
May  5 18:45:48 chuck-laptop kernel: [ 2437.436000] Suspending console(s)
May  5 18:45:48 chuck-laptop kernel: [ 2437.436000] ac97 1-0:unknown codec: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2437.436000] ac97 0-0:unknown codec: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2437.436000] ide-cdrom 1.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2437.440000] ide-disk 0.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev3.1_ep81: PM: suspend 0->1, parent 3-0:1.0 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 3-0:1.0: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 3-0:1.0: PM: suspend 2->1, parent usb3 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev3.1_ep00: PM: suspend 0->1, parent usb3 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] usb usb3: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev2.1_ep81: PM: suspend 0->1, parent 2-0:1.0 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 2-0:1.0: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 2-0:1.0: PM: suspend 2->1, parent usb2 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev2.1_ep00: PM: suspend 0->1, parent usb2 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] usb usb2: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 1-0:1.0: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000]  usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] usb usb1: PM: suspend 2-->1
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] platform vesafb.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] platform eisa.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2438.828000] i8042 i8042: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] serial8250 serial8250: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pcspkr pcspkr: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] system 00:09: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] system 00:08: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] i8042 aux 00:07: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] i8042 kbd 00:06: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pnp 00:05: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pnp 00:04: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pnp 00:03: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pnp 00:02: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] system 00:01: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] pnp 00:00: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] sdhci 0000:05:09.4: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.416000] ACPI: PCI interrupt for device 0000:05:09.4 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2439.432000] tifm_7xx1 0000:05:09.3: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.432000] ACPI: PCI interrupt for device 0000:05:09.3 disabled
[b]May  5 18:45:48 chuck-laptop kernel: [ 2439.448000] ohci1394 0000:05:09.2: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.448000] ohci1394 does not fully support suspend and resume yet
May  5 18:45:48 chuck-laptop kernel: [ 2439.448000] ieee1394: hpsb_bus_reset called while bus reset already in progress[/b]
May  5 18:45:48 chuck-laptop kernel: [ 2439.464000] yenta_cardbus 0000:05:09.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.464000] pci 0000:05:02.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.464000] pci 0000:05:00.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2439.464000] fglrx_pci 0000:01:05.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.272000] [fglrx] firegl_gps_setpowerdown .
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ACPI: PCI interrupt for device 0000:01:05.0 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] k8temp 0000:00:18.3: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] pci 0000:00:18.2: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] pci 0000:00:18.1: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] pci 0000:00:18.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ATI IXP MC97 controller 0000:00:14.6: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ATI IXP AC97 controller 0000:00:14.5: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ACPI: PCI interrupt for device 0000:00:14.5 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] pci 0000:00:14.4: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] pci 0000:00:14.3: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ATIIXP_IDE 0000:00:14.1: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] piix4_smbus 0000:00:14.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ehci_hcd 0000:00:13.2: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.292000] ACPI: PCI interrupt for device 0000:00:13.2 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.1: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ACPI: PCI interrupt for device 0000:00:13.1 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ACPI: PCI interrupt for device 0000:00:13.0 disabled
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:01.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:00.0: freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] acpi acpi: freeze
[b]May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] PM: snapshotting memory.
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] platform vesafb.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] platform eisa.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] i8042 i8042: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] serial8250 serial8250: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pcspkr pcspkr: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] sdhci 0000:05:09.4: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] tifm_7xx1 0000:05:09.3: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci1394 0000:05:09.2: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] yenta_cardbus 0000:05:09.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:05:02.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:05:00.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] k8temp 0000:00:18.3: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.2: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.1: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATI IXP MC97 controller 0000:00:14.6: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATI IXP AC97 controller 0000:00:14.5: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:14.4: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:14.3: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATIIXP_IDE 0000:00:14.1: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] piix4_smbus 0000:00:14.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:01.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:00.0: LATE freeze
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] swsusp: critical section: 
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] swsusp: Need to copy 50143 pages
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] swsusp: Normal pages needed: 50143 + 1024 + 12, available pages: 47887
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] swsusp: Not enough free memory
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] Error -12 suspending[/b]
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:00.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:01.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.1: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ehci_hcd 0000:00:13.2: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] piix4_smbus 0000:00:14.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATIIXP_IDE 0000:00:14.1: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:14.3: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:14.4: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATI IXP AC97 controller 0000:00:14.5: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ATI IXP MC97 controller 0000:00:14.6: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.1: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:18.2: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] k8temp 0000:00:18.3: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] fglrx_pci 0000:01:05.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:05:00.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:05:02.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] yenta_cardbus 0000:05:09.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci1394 0000:05:09.2: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] tifm_7xx1 0000:05:09.3: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] sdhci 0000:05:09.4: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pcspkr pcspkr: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] serial8250 serial8250: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] i8042 i8042: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] platform eisa.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] platform vesafb.0: EARLY resume
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] acpi acpi: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:00.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] pci 0000:00:01.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ohci_hcd 0000:00:13.1: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
May  5 18:45:48 chuck-laptop kernel: [ 2442.308000] ehci_hcd 0000:00:13.2: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] PCI: Enabling device 0000:00:13.2 (0000 -> 0002)
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] PM: Writing back config space on device 0000:00:13.2 at offset 1 (was 2b00006, writing 2b00017)
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] piix4_smbus 0000:00:14.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ATIIXP_IDE 0000:00:14.1: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] pci 0000:00:14.3: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] pci 0000:00:14.4: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ATI IXP AC97 controller 0000:00:14.5: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ATI IXP MC97 controller 0000:00:14.6: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] pci 0000:00:18.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] pci 0000:00:18.1: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] pci 0000:00:18.2: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] k8temp 0000:00:18.3: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] fglrx_pci 0000:01:05.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
May  5 18:45:48 chuck-laptop kernel: [ 2442.324000] [fglrx] firegl_gps_setpowerup .
May  5 18:45:48 chuck-laptop kernel: [ 2442.376000] pci 0000:05:00.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.376000] pci 0000:05:02.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.376000] yenta_cardbus 0000:05:09.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.376000] ohci1394 0000:05:09.2: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.392000] PM: Writing back config space on device 0000:05:09.2 at offset f (was 4030300, writing 4030304)
May  5 18:45:48 chuck-laptop kernel: [ 2442.392000] PM: Writing back config space on device 0000:05:09.2 at offset 5 (was 0, writing c0200000)
May  5 18:45:48 chuck-laptop kernel: [ 2442.392000] PM: Writing back config space on device 0000:05:09.2 at offset 4 (was 0, writing c0208800)
May  5 18:45:48 chuck-laptop kernel: [ 2442.392000] PM: Writing back config space on device 0000:05:09.2 at offset 3 (was 800000, writing 804008)
May  5 18:45:48 chuck-laptop kernel: [ 2442.392000] PM: Writing back config space on device 0000:05:09.2 at offset 1 (was 2100000, writing 2100016)
May  5 18:45:48 chuck-laptop kernel: [ 2442.440000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May  5 18:45:48 chuck-laptop kernel: [ 2442.440000] tifm_7xx1 0000:05:09.3: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] PM: Writing back config space on device 0000:05:09.3 at offset f (was 40701ff, writing 407010a)
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] PM: Writing back config space on device 0000:05:09.3 at offset 4 (was 0, writing c0206000)
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] PM: Writing back config space on device 0000:05:09.3 at offset 3 (was 800000, writing 804008)
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] PM: Writing back config space on device 0000:05:09.3 at offset 1 (was 2100000, writing 2100006)
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 16
May  5 18:45:48 chuck-laptop kernel: [ 2442.456000] sdhci 0000:05:09.4: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset f (was 40701ff, writing 407010a)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset 6 (was 0, writing c0208400)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset 5 (was 0, writing c0209000)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset 4 (was 0, writing c0209400)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset 3 (was 800000, writing 804008)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] PM: Writing back config space on device 0000:05:09.4 at offset 1 (was 2100000, writing 2100006)
May  5 18:45:48 chuck-laptop kernel: [ 2442.472000] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 16
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp 00:00: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] system 00:01: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp 00:02: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp 00:03: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp 00:04: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp 00:05: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] i8042 kbd 00:06: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp: Device 00:06 does not support activation.
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] i8042 aux 00:07: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pnp: Device 00:07 does not support activation.
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] system 00:08: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] system 00:09: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] pcspkr pcspkr: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] serial8250 serial8250: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] i8042 i8042: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.496000] atkbd serio0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.536000] platform eisa.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2442.536000] psmouse serio1: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000] platform vesafb.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev1.1_ep00: PM: resume from 0, parent usb1 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev1.1_ep81: PM: resume from 0, parent 1-0:1.0 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev2.1_ep00: PM: resume from 0, parent usb2 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev2.1_ep81: PM: resume from 0, parent 2-0:1.0 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
May  5 18:45:48 chuck-laptop kernel: [ 2443.076000] ide-disk 0.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.156000] ide-cdrom 1.0: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.160000] ac97 0-0:unknown codec: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.160000] ac97 1-0:unknown codec: resuming
May  5 18:45:48 chuck-laptop kernel: [ 2443.160000] Restarting tasks ... done.
May  5 18:45:48 chuck-laptop kernel: [ 2443.160000] Enabling non-boot CPUs ...
```

[b][size=3]Don't know why it shows "swsusp: not enough memory". On Win XP it used to work normally even with a lot of programs running. Any ideas, tutorials?
Thanks![/size][/b]

---

### Post by xundaman on 2007-05-06
up
too many topics are created :)

---

### Post by chele on 2007-05-13
Are you trying to hibernate or suspend? Hibernate saves the contents of ram to the harddrive, then turns off the computer. Suspend puts everything in a really  low power state.

What about it does not work?

---

### Post by WilliamAnderson on 2007-05-15
Hi

xundaman is trying to hibernate to disk.  I am periodically having the same problem with my IBM Thinkpad R50p. The important part of the syslog file on my system is:

May 15 08:56:01 tate kernel: [563614.666000] swsusp: critical section:

May 15 08:56:01 tate kernel: [563614.666000] swsusp: Need to copy 68122 pages

May 15 08:56:01 tate kernel: [563614.666000] swsusp: Normal pages needed: 68122 + 1024 + 14, available pages: 62788

May 15 08:56:01 tate kernel: [563614.666000] swsusp: Not enough free memory

May 15 08:56:01 tate kernel: [563614.666000] Error -12 suspending



The key is the line that talks about “Normal pages needed:”. To save the system's state, swsusp needs 68122 pages of space but only has 62788 pages available. (I do not know off the top of my head how big it bytes a page is on an Intel processor) This is saved in the swap partition by default. 

This is caused by not having enough space in the swap partition. Now my system has 512 Mb of RAM and 1.5 Gb of swap space. At the time this hibernate failed, there were several megabytes of swap space in use, the cause of the problem?

When hibernate works, everything including multimedia comes back up fine and playing. 

Is this a case for creating a dedicated suspend partition?

William

---

### Post by xundaman on 2007-06-01
I'm trying to hibernate, clicking on the top right icon and clicking on hibernate. The same on Win XP, when I close the lid, it turns off and saves my last session.

---

