---
title: "My AMD gpu s not displayed in the details window"
date: 2016-06-07
forum: Hardware
---

### Post by Raviteja_Chatta on 2016-06-07
I have recenly installed ubuntu 16 on my laptop with amd gpu and intel integrated chipset but my amd gpu is disabled. Is there any way to use AMG gpu by default.
GPU details are isted below.
ilspci output is 
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: Lenovo Haswell-ULT DRAM Controller [17aa:3978]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: hsw_uncore


00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Haswell-ULT Integrated Graphics Controller [17aa:380c]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Lenovo Haswell-ULT HD Audio Controller [17aa:3978]
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at d0710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo 8 Series USB xHCI HC [17aa:3978]
    Flags: bus master, medium devsel, latency 0, IRQ 45
    Memory at d0700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Lenovo 8 Series HECI [17aa:3978]
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at d0718000 (64-bit, non-prefetchable) [size=32]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Lenovo 8 Series HD Audio Controller [17aa:3978]
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at d0714000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0600000-d06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 4 [8086:9c16] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: d0500000-d05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 5 [8086:9c18] (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0400000-d04fffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller [0c03]: Intel Corporation 8 Series USB EHCI #1 [8086:9c26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo 8 Series USB EHCI [17aa:3978]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d071c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
    Subsystem: Lenovo 8 Series LPC Controller [17aa:3978]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo 8 Series SATA Controller 1 [AHCI mode] [17aa:3978]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at 5088 [size=8]
    I/O ports at 5094 [size=4]
    I/O ports at 5080 [size=8]
    I/O ports at 5090 [size=4]
    I/O ports at 5060 [size=32]
    Memory at d071b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Lenovo 8 Series SMBus Controller [17aa:3978]
    Flags: medium devsel, IRQ 11
    Memory at d0719000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:380a]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at 4000 [size=256]
    Memory at d0604000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0621]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0500000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: bcma, wl


03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun LE [Radeon HD 8550M / R5 M230] [1002:666f]
    Subsystem: Lenovo Sun LE [Radeon HD 8550M / R5 M230] [17aa:380c]
    Flags: fast devsel, IRQ 49
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=256]
    Expansion ROM at d0440000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

---

