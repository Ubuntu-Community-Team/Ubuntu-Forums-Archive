---
title: "Various nVidia Corporation Unknown device"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by johnstanton on 2007-12-08
Hello, 

I just installed ubuntu 7.10 on an acer 5520-5626. I have got sound and wireless working(Atheros)
Now when i do an lspci i am seeing various nVidia Corporation Unknown device messages, Anyone know howto resolve any of these? Will this damage my laptop if i leave it like this? Should i just go back to windows xp where everything installs?

Thanks, 

 lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

sudo lspci -nnv
00:00.0 RAM memory [0500]: nVidia Corporation Unknown device [10de:0547] (rev a2)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [dc] HyperTransport: MSI Mapping

00:01.0 ISA bridge [0601]: nVidia Corporation Unknown device [10de:0548] (rev a2)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 1d00 [size=256]

00:01.1 SMBus [0c05]: nVidia Corporation Unknown device [10de:0542] (rev a2)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3080 [size=64]
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

00:01.2 RAM memory [0500]: nVidia Corporation Unknown device [10de:0541] (rev a2)
        Subsystem: nVidia Corporation Unknown device [10de:cb84]
        Flags: 66MHz, fast devsel

00:01.3 Co-processor [0b40]: nVidia Corporation Unknown device [10de:0543] (rev a2)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at f2400000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:055e] (rev a2) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f2686000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:055f] (rev a2) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f2689000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:04.0 USB Controller [0c03]: nVidia Corporation Unknown device [10de:055e] (rev a2) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at f2687000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:04.1 USB Controller [0c03]: nVidia Corporation Unknown device [10de:055f] (rev a2) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f2689400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:06.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0560] (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 30c0 [size=16]
        Capabilities: [44] Power Management version 2

00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f2680000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0561] (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f2300000-f23fffff
        Capabilities: [b8] Subsystem: nVidia Corporation Unknown device [10de:cb84]
        Capabilities: [8c] HyperTransport: MSI Mapping

00:09.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:0550] (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 30f0 [size=8]
        I/O ports at 30e4 [size=4]
        I/O ports at 30e8 [size=8]
        I/O ports at 30e0 [size=4]
        I/O ports at 30d0 [size=16]
        Memory at f2684000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2
        Capabilities: [8c] #12 [0010]
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0a.0 Ethernet controller [0200]: nVidia Corporation Unknown device [10de:054c] (rev a2)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f2688000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30f8 [size=8]
        Memory at f2689c00 (32-bit, non-prefetchable) [size=256]
        Memory at f2689800 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:0c.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0563] (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f2000000-f21fffff
        Prefetchable memory behind bridge: 00000000f2800000-00000000f29fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device [10de:0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:0563] (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: f2200000-f22fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device [10de:0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:12.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0533] (rev a2) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
        Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
        Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:04.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2300000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2300800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

01:04.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2300c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

01:04.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2301000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

01:04.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
        Subsystem: Acer Incorporated [ALI] Unknown device [1025:0126]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f2301400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

05:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device [1468:0428]
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f2200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

---

