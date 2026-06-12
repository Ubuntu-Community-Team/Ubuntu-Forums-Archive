---
title: "PM cap regs trouble"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by blackflag456 on 2009-09-30
i looked at a few other threads to solve the problem i was having with the PM cap regs being unsupported (showing up when i boot up). i ran "sudo lspci -v" but i have no idea whats wrong. is it something to do with whats at the bottom (the " Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+")? if so what do i do? im fairly new to ubuntu/linux. i did however get a beginners guide to ubuntu just yesterday so i do know a little more than i did before.




gregory@holtzg-laptop:~$ sudo lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d6200000-d63fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d5200000-d61fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff6a
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: d4200000-d51fffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d20fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff6a
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d3100000-d41fffff
    Prefetchable memory behind bridge: 00000000d2100000-00000000d30fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff6a
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff6a
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 7038 [size=8]
    I/O ports at 704c [size=4]
    I/O ports at 7030 [size=8]
    I/O ports at 7048 [size=4]
    I/O ports at 7010 [size=16]
    Memory at d6408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d6407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d6406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d6408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d6405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d6404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d6408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 7000 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff
    Kernel modules: shpchp

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

01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=256]
    Memory at d6300000 (32-bit, non-prefetchable) [size=64K]
    Memory at d6200000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff6a
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at 3000 [size=256]
    Memory at d1010000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=64K]
    Capabilities: [40] Power Management version 7
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-08
    Kernel driver in use: r8169
    Kernel modules: r8169

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d3100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

---

