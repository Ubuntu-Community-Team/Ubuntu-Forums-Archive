---
title: "Having trouble with Intel wifi and sound..."
date: 2015-05-21
forum: Hardware
---

### Post by ArgentWarrior on 2015-05-21
I'm trying to streamline linux-pf to my hardware. I know, I know, I can't submit crash reports on a custom kernel, the mainline one just works, blah blah blah. There's no point in using Linux if you're not going to **use **Linux.

Anyway, I'm trying to build an initrd-less and module-less kernel, for the benefits that come with it (like increased boot times). I've managed to get everything working in Linux-pf 4.0, except wifi. Graphics work, touchpad works, USB works, and my sound is having some issues but it works. But no matter what I do, I can't get my Centrino 6150 to work. I pointed the config to the proper firmware, and set it to build the firmware into the kernel. Build, drop the image in /boot, update GRUB, and still no wifi. What am I doing wrong here guys? Here's the output of "sudo lspci -knnv", any help is greatly appreciated.
My sound snaps, crackles and pops more than a 1940s telephone on my custom kernels, but I think I might be able to solve that one. Again, thanks guys.
```

[COLOR=#3D3D3D][FONT=intel-clear]00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [e0] Vendor Specific Information: Len=0c <?>[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 36[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c0000000 (64-bit, non-prefetchable) [size=4M][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at b0000000 (64-bit, prefetchable) [size=256M][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5000 [size=64][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Expansion ROM at <unassigned> [disabled][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [d0] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a4] PCI Advanced Features[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: i915[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 35[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c6504000 (64-bit, non-prefetchable) [size=16][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: mei_me[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) (prog-if 20 [EHCI])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, medium devsel, latency 0, IRQ 16[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c650a000 (32-bit, non-prefetchable) [size=1K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [58] Debug port: BAR=1 offset=00a0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [98] PCI Advanced Features[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: ehci-pci[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 38[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c6500000 (64-bit, non-prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Virtual Channel[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [130] Root Complex Link[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: snd_hda_intel[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Bus: primary=00, secondary=01, subordinate=06, sec-latency=0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O behind bridge: 00004000-00004fff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory behind bridge: c5500000-c64fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Prefetchable memory behind bridge: 00000000c0400000-00000000c13fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Express Root Port (Slot+), MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a0] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: pcieport[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Bus: primary=00, secondary=07, subordinate=0c, sec-latency=0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O behind bridge: 00003000-00003fff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory behind bridge: c4500000-c54fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Prefetchable memory behind bridge: 00000000c1400000-00000000c23fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Express Root Port (Slot+), MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a0] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: pcieport[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Bus: primary=00, secondary=0d, subordinate=12, sec-latency=0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O behind bridge: 00002000-00002fff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory behind bridge: c3500000-c44fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Prefetchable memory behind bridge: 00000000c2400000-00000000c33fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Express Root Port (Slot+), MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a0] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: pcieport[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Bus: primary=00, secondary=13, subordinate=13, sec-latency=0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory behind bridge: c3400000-c34fffff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Express Root Port (Slot+), MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a0] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: pcieport[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) (prog-if 20 [EHCI])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, medium devsel, latency 0, IRQ 20[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c6509000 (32-bit, non-prefetchable) [size=1K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] Power Management version 2[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [58] Debug port: BAR=1 offset=00a0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [98] PCI Advanced Features[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: ehci-pci[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, medium devsel, latency 0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [e0] Vendor Specific Information: Len=0c <?>[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: lpc_ich[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) (prog-if 01 [AHCI 1.0])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5088 [size=8][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 509c [size=4][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5080 [size=8][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5098 [size=4][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5060 [size=32][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c6508000 (32-bit, non-prefetchable) [size=2K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [70] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a8] SATA HBA v1.0[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [b0] PCI Advanced Features[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: ahci[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: medium devsel, IRQ 10[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c6506000 (64-bit, non-prefetchable) [size=256][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 5040 [size=32][/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 33[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  I/O ports at 4000 [size=256][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c0404000 (64-bit, prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c0400000 (64-bit, prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [70] Express Endpoint, MSI 01[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [b0] MSI-X: Enable- Count=4 Masked-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [d0] Vital Product Data[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Advanced Error Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [140] Virtual Channel[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [160] Device Serial Number d1-00-00-00-68-4c-e0-00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: r8169[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 37[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c4500000 (64-bit, non-prefetchable) [size=8K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [c8] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [e0] Express Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Advanced Error Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [140] Device Serial Number 40-25-c2-ff-ff-8b-e8-c8[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: iwlwifi[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]0d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 32[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c3501000 (32-bit, non-prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Expansion ROM at c3510000 [disabled] [size=64K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [40] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [70] Express Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Advanced Error Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: rtsx_pci[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]0d:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:165b][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 19[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c3500000 (32-bit, non-prefetchable) [size=256][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [80] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [b0] Express Endpoint, MSI 01[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Advanced Error Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: sdhci-pci[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]13:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04) (prog-if 30 [XHCI])[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Subsystem: Hewlett-Packard Company Device [103c:1658][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Flags: bus master, fast devsel, latency 0, IRQ 19[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Memory at c3400000 (64-bit, non-prefetchable) [size=8K][/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [50] Power Management version 3[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [90] MSI-X: Enable+ Count=8 Masked-[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [a0] Express Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [100] Advanced Error Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Capabilities: [150] Latency Tolerance Reporting[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]  Kernel driver in use: xhci_hcd[/FONT][/COLOR]

```

---

