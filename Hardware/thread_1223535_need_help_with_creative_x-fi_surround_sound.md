---
title: "need help with creative x-fi surround sound"
date: 2009-07-26
forum: Hardware
---

### Post by crazyone on 2009-07-26
hi i got a x-fi xtreme music sound card. it has 5.1 surround sound but after trying many things including using alsa drivers, the drivers form creative and a few other things i cant seem to figure out how i did it in the past. i have so far tried the drivers from creative version 1, have used the latest alsa drivers. both work if i just want front channels but i would like to use atleast the bass speaker too but would perfer the full surround sound. i know its possible i jsut cant figure out how. i have also tried the latest version of 9.10 and it detects my card with full chanels. i have also followed pertty much all of the guides on this forum on getting it to work but none of them really say anything about all the channels working.

my system is as follow
ubuntu 9.04 64 bit
asus p5q motherbaord
intel q6600 cpu
4gb ram
nvidia 9800gt

heres what i get for lspci -v

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82d3
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f4000000-f7dfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 82d3
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a880 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ac00 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f3fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] Vendor Specific Information <?>
	Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000f2f00000-00000000f2ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7f00000-f7ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f7e00000-f7efffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 82d4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a080 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a480 [size=32]
	Capabilities: [50] Vendor Specific Information <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f3fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] Vendor Specific Information <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-febfffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 82d4

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 9000 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 8880 [size=8]
	I/O ports at 8800 [size=4]
	I/O ports at 8480 [size=16]
	I/O ports at 8400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information <?>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: medium devsel, IRQ 15
	Memory at f3fff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information <?>
	Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
	Subsystem: eVga.com. Corp. Device c978
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at f7de0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device 8226
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f7ec0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at cc00 [size=128]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-15-22-00-0d-32-20-ff
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82e0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: pata_marvell

05:00.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at ec00 [size=32]
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: SB-XFi
	Kernel modules: snd-ctxfi

05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8294
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394


any help on this would be great becuase i really hate havign to go into windows very often.if there is any more info you need tell me and ill post it. if some one just knows of the driver that ubuntu is using to work with the xfi sound cards so well can you post a link to it for me. thanks

---

