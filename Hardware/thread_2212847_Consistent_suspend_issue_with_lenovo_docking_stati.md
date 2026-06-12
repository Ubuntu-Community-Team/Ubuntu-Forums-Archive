---
title: "Consistent suspend issue with lenovo docking station."
date: 2014-03-23
forum: Hardware
---

### Post by Paul_Jewell on 2014-03-23
Hello, I have been using ubuntu on my ibm/lenovo thinkpad T60 for many years now. The laptop came with a docking station when I bought it which I like to use sometimes to have two monitors. Whenever I use the laptop with the docking station at any time, if I then decide to suspend / resume the computer will not successfully resume. It starts up and I see the terminal text appear for a half second then the screen starts flashing once or twice a second and no input will do anything (no restart x, no switch to terminal). I must hard poweroff. I would like to be able to know what log to look in to see that terminal text which I saw before the issue occurred and possibly fix the issue in the future. Any ideas?

Here is lspci, by the way:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)	Subsystem: Lenovo ThinkPad T60
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>


00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: ee100000-ee1fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Lenovo Device 2014
	Capabilities: [80] Power Management version 2
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: ee000000-ee0fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: e8000000-e9ffffff
	Prefetchable memory behind bridge: 00000000e4100000-00000000e41fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=13, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: ea000000-ebffffff
	Prefetchable memory behind bridge: 00000000e4200000-00000000e42fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ee404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 0000a000-0000dfff
	Memory behind bridge: e4300000-e7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e3ffffff
	Capabilities: [50] Subsystem: Lenovo Device 2013


00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, lpc_ich, intel-rng


00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]
	Kernel driver in use: ata_piix


00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at ee404400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801


01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV530/M56 GL [Mobility FireGL V5200] (prog-if 00 [VGA controller])
	Subsystem: Lenovo ThinkPad T60p
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ee120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: radeon
	Kernel modules: radeon


02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Lenovo ThinkPad T60
	Physical Slot: 2
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-16-41-ff-ff-56-8e-34
	Kernel driver in use: e1000e
	Kernel modules: e1000e


03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1010
	Physical Slot: 3
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-18-de-ff-ff-66-15-d4
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945


15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: e0000000-e3fff000 (prefetchable)
	Memory window 1: c4000000-c7fff000
	I/O window 0: 0000a000-0000a0ff
	I/O window 1: 0000a400-0000a4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket


16:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)
	Subsystem: 3Com Corporation FE575C-3Com 10/100 LAN CardBus-Fast Ethernet
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at a000 [size=256]
	Memory at c4000000 (32-bit, non-prefetchable) [size=128]
	Memory at c4000080 (32-bit, non-prefetchable) [size=128]
	[virtual] Expansion ROM at e0000000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

```

---

### Post by Paul_Jewell on 2014-03-24
<deleted>

---

### Post by Paul_Jewell on 2014-03-29
bump

---

