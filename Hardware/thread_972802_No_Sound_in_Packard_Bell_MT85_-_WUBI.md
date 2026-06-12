---
title: "No Sound in Packard Bell MT85 - WUBI"
date: 2008-11-06
forum: Hardware
---

### Post by firatkaratas on 2008-11-06
Hi all,

I have a problem about my sound card. I am using 8.10 amd84 version with WUBI. I can see it on lspci -v, but I can not hear any sound. What I see on the lspci -v is the following:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fddffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fddf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fdf00000-fdffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe000000-fe9fffff
	Prefetchable memory behind bridge: 00000000fa000000-00000000fcefffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000fcf00000-00000000fcffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Packard Bell B.V. Device c211
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b480 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fddff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: feb00000-febfffff
	Capabilities: [50] Subsystem: Packard Bell B.V. Device c211

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=32]
	Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
	Subsystem: Packard Bell B.V. Device c221
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fdec0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fdeec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at fdffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 60-4a-65-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	I/O ports at e800 [size=256]
	Memory at fcfff000 (64-bit, prefetchable) [size=4K]
	Memory at fcfe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-e0-4c-68-80-24-04-31
	Kernel driver in use: r8169
	Kernel modules: r8169

09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Packard Bell B.V. Device c211
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at febff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2


what can I do?

Thanks for your help.

P.S. I am newbie

---

