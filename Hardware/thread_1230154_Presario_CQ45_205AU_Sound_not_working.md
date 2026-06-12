---
title: "Presario CQ45 205AU Sound not working"
date: 2009-08-03
forum: Hardware
---

### Post by rajatjpatel on 2009-08-03
Hi Everyone,

I got Presario CQ45 205AU last week and i'm using Ubuntu 9.04 everything is working fine only sound card is not working 

#lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

#lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: 92300000-924fffff
    Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30fb
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00006fff
    Memory behind bridge: 91300000-922fffff
    Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30fb
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: 91200000-912fffff
    Prefetchable memory behind bridge: 0000000070000000-00000000700fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30fb
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: 91100000-911fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30fb
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 70100000-701fffff
    Prefetchable memory behind bridge: 0000000091000000-00000000910fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30fb
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8038 [size=8]
    I/O ports at 804c [size=4]
    I/O ports at 8030 [size=8]
    I/O ports at 8048 [size=4]
    I/O ports at 8010 [size=16]
    Memory at 92508000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at 92507000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at 92506000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at 92508500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 92505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 92504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at 92508400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8000 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at 92400000 (32-bit, non-prefetchable) [size=64K]
    Memory at 92300000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Subsystem: ATI Technologies Inc RS780 Azalia controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 91200300 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 70000000 [disabled] [size=64K]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: fast devsel, IRQ 17
    Memory at 91200200 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at 91200100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at 91200000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 137d
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 91100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 21-00-af-ff-ff-00-cb-ef
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at 2000 [size=256]
    Memory at 91010000 (64-bit, prefetchable) [size=4K]
    Memory at 91000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 91020000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-01-68
    Kernel driver in use: r8169
    Kernel modules: r8169

if any one has set this driver pls let me know...

---

