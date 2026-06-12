---
title: "Ubuntu needs 3 boot up attempts till it is successfull"
date: 2011-09-08
forum: Hardware
---

### Post by chichali on 2011-09-08
Hello everybody!
I am having a HP Pavillion dv6 notebook which i use.
just at the beginning where i was about to install ubuntu 11.04 via live cd, i was't
able to boot the system up. I recognized thath i've had to leave the poweradapter connected in order to boot my system successfully.

After installation, and System Update i've wondered why i still can not boot every time. so i checked the logs and found an "i915 unable to load symbols error" so i added the command "i915.modeset=1" after "quiet splash" and updated grub with the new startup parameters.
now everytime i boot up my notebook it boots into a dark screen, and there it stays untill i reset the laptop. then if i do so, the grub bootloader appears and give me the choice to boot normal or recovery etc. when i check the bootoptions with "e" the "i915.modeset" command is there, so i press ctrl + x to boot. this time the same thing happens as at first try. now if i try one more time, it successfully boots to ubuntu.

my lspci -v is:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c4400000-c44fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
    Capabilities: [88] Subsystem: Hewlett-Packard Company Device 163c
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5050 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c4504000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c450a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c3400000-c43fffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c13fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 163c
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c2400000-c33fffff
    Prefetchable memory behind bridge: 00000000c1400000-00000000c23fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 163c
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at c4509000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device 163c

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 5048 [size=8]
    I/O ports at 505c [size=4]
    I/O ports at 5040 [size=8]
    I/O ports at 5058 [size=4]
    I/O ports at 5020 [size=32]
    Memory at c4508000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: medium devsel, IRQ 10
    Memory at c4506000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at c4507000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at c4400000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 4000 [size=256]
    Expansion ROM at c4440000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at c4420000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 1483
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c3400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-82-ff-ff-a5-e0-2a
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 2000 [size=256]
    Memory at c1404000 (64-bit, prefetchable) [size=4K]
    Memory at c1400000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at c1410000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Hewlett-Packard Company Device 163c
    Flags: bus master, fast devsel, latency 0

```

dmesg is:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 (Ubuntu 2.6.38-11.48-generic 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009b63f000 (usable)
[    0.000000]  BIOS-e820: 000000009b63f000 - 000000009b6bf000 (reserved)
[    0.000000]  BIOS-e820: 000000009b6bf000 - 000000009b7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009b7bf000 - 000000009b7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009b7ff000 - 000000009b800000 (usable)
[    0.000000]  BIOS-e820: 000000009b800000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000158000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv6 Notebook PC/163C, BIOS F.23 10/21/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x9b800 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 09B800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 158000000 mask FF8000000 uncachable
[    0.000000]   7 base 160000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3676a000 - 373ad000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 9b7fe120 0007C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 9b7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 9b7e9000 0F2FB (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 9b75e000 00040
[    0.000000] ACPI: ASF! 9b7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 9b7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 9b7fa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 9b7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 9b7e8000 00176 (v01 HPQOEM SLIC-MPC 00000001 SLIC 000F4240)
[    0.000000] ACPI: BOOT 9b7e5000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 9b7e2000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 9b7e1000 00224 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 9b7e0000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 9b7de000 01B34 (v01 AmdRef  AmdTabl 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1600MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009b800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009b63f
[    0.000000]     0: 0x0009b7ff -> 0x0009b800
[    0.000000] On node 0 totalpages: 636365
[    0.000000] free_area_init_node: node 0, pgdat c1784180, node_mem_map f53fa200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3201 pages used for memmap
[    0.000000]   HighMem zone: 405953 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:50000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4c00000 s28800 r0 d24448 u524288
[    0.000000] pcpu-alloc: s28800 r0 d24448 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 631388
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=6bdf6bda-4f71-45d5-8fbb-247b42d1f90a ro quiet splash i915.modeset=1 vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12738240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009b800)
[    0.000000] Memory: 2489932k/2547712k available (5190k kernel code, 55528k reserved, 2538k data, 700k init, 1636616k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511ba1 - 0xc178c500   (2538 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511ba1   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f380a000 soft=f380c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2659.513 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.02 BogoMIPS (lpj=10638052)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000022] Security Framework initialized
[    0.000032] AppArmor: AppArmor initialized
[    0.000033] Yama: becoming mindful.
[    0.000075] Mount-cache hash table entries: 512
[    0.000175] Initializing cgroup subsys ns
[    0.000178] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.000180] Initializing cgroup subsys cpuacct
[    0.000183] Initializing cgroup subsys memory
[    0.000190] Initializing cgroup subsys devices
[    0.000191] Initializing cgroup subsys freezer
[    0.000193] Initializing cgroup subsys net_cls
[    0.000194] Initializing cgroup subsys blkio
[    0.000219] CPU: Physical Processor ID: 0
[    0.000220] CPU: Processor Core ID: 0
[    0.000224] mce: CPU supports 9 MCE banks
[    0.000234] CPU0: Thermal monitoring enabled (TM1)
[    0.000240] using mwait in idle threads.
[    0.002187] ACPI: Core revision 20110112
[    0.034912] ftrace: allocating 23649 entries in 47 pages
[    0.041114] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.041511] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.522514] CPU0: Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz stepping 05
[    0.627287] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.627293] ... version:                3
[    0.627294] ... bit width:              48
[    0.627295] ... generic registers:      4
[    0.627296] ... value mask:             0000ffffffffffff
[    0.627297] ... max period:             000000007fffffff
[    0.627298] ... fixed-purpose events:   3
[    0.627299] ... event mask:             000000070000000f
[    0.627620] CPU 1 irqstacks, hard=f38ce000 soft=f38d8000
[    0.627623] Booting Node   0, Processors  #1
[    0.637865] Initializing CPU#1
[    0.735435] CPU 2 irqstacks, hard=f3900000 soft=f3902000
[    0.735439]  #2
[    0.745590] Initializing CPU#2
[    0.843485] CPU 3 irqstacks, hard=f3910000 soft=f3912000
[    0.843488]  #3
[    0.853639] Initializing CPU#3
[    0.951365] Brought up 4 CPUs
[    0.951367] Total of 4 processors activated (21278.66 BogoMIPS).
[    0.953590] devtmpfs: initialized
[    0.954496] print_constraints: dummy: 
[    0.954524] Time:  5:23:42  Date: 09/08/11
[    0.954559] NET: Registered protocol family 16
[    0.954636] EISA bus registered
[    0.954641] Trying to unpack rootfs image as initramfs...
[    0.954643] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.954645] ACPI: bus type pci registered
[    0.954704] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.954706] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.954708] PCI: Using MMCONFIG for extended config space
[    0.954709] PCI: Using configuration type 1 for base access
[    0.955325] bio: create slab <bio-0> at 0
[    0.957432] ACPI: EC: Look up EC in DSDT
[    0.991431] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.997044] ACPI: SSDT 9b691a18 00474 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.997520] ACPI: Dynamic OEM Table Load:
[    0.997522] ACPI: SSDT   (null) 00474 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.997662] ACPI: SSDT 9b68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.998119] ACPI: Dynamic OEM Table Load:
[    0.998120] ACPI: SSDT   (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.051655] ACPI: SSDT 9b690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.052175] ACPI: Dynamic OEM Table Load:
[    1.052178] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.079526] ACPI: SSDT 9b68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.080015] ACPI: Dynamic OEM Table Load:
[    1.080017] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.164526] Freeing initrd memory: 12556k freed
[    1.168554] ACPI: Interpreter enabled
[    1.168562] ACPI: (supports S0 S3 S4 S5)
[    1.168594] ACPI: Using IOAPIC for interrupt routing
[    1.596253] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    1.596387] ACPI: No dock devices found.
[    1.596389] HEST: Table not found.
[    1.596393] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.596704] \_SB_.PCI0:_OSC invalid UUID
[    1.596705] _OSC request data:1 8 1f 
[    1.596709] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    1.597219] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.597221] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.597223] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.597226] pci_root PNP0A08:00: host bridge window [mem 0xa0000000-0xfeafffff]
[    1.597238] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.597256] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.597271] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
[    1.597295] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.597298] pci 0000:00:01.0: PME# disabled
[    1.597308] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.597318] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    1.597324] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.597328] pci 0000:00:02.0: reg 20: [io  0x5050-0x5057]
[    1.597385] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.597412] pci 0000:00:16.0: reg 10: [mem 0xc4504000-0xc450400f 64bit]
[    1.597486] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.597491] pci 0000:00:16.0: PME# disabled
[    1.597530] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.597946] pci 0000:00:1a.0: reg 10: [mem 0xc450a000-0xc450a3ff]
[    1.600376] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.600381] pci 0000:00:1a.0: PME# disabled
[    1.600410] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.600430] pci 0000:00:1b.0: reg 10: [mem 0xc4500000-0xc4503fff 64bit]
[    1.600504] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.600509] pci 0000:00:1b.0: PME# disabled
[    1.600535] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.600612] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.600616] pci 0000:00:1c.0: PME# disabled
[    1.600643] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.600720] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.600724] pci 0000:00:1c.1: PME# disabled
[    1.600765] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.601181] pci 0000:00:1d.0: reg 10: [mem 0xc4509000-0xc45093ff]
[    1.603609] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.603614] pci 0000:00:1d.0: PME# disabled
[    1.603637] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.603712] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.603828] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.603854] pci 0000:00:1f.2: reg 10: [io  0x5048-0x504f]
[    1.603864] pci 0000:00:1f.2: reg 14: [io  0x505c-0x505f]
[    1.603875] pci 0000:00:1f.2: reg 18: [io  0x5040-0x5047]
[    1.603886] pci 0000:00:1f.2: reg 1c: [io  0x5058-0x505b]
[    1.603896] pci 0000:00:1f.2: reg 20: [io  0x5020-0x503f]
[    1.603907] pci 0000:00:1f.2: reg 24: [mem 0xc4508000-0xc45087ff]
[    1.603954] pci 0000:00:1f.2: PME# supported from D3hot
[    1.603958] pci 0000:00:1f.2: PME# disabled
[    1.603979] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.603999] pci 0000:00:1f.3: reg 10: [mem 0xc4506000-0xc45060ff 64bit]
[    1.604028] pci 0000:00:1f.3: reg 20: [io  0x5000-0x501f]
[    1.604074] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.604100] pci 0000:00:1f.6: reg 10: [mem 0xc4507000-0xc4507fff 64bit]
[    1.604209] pci 0000:01:00.0: [1002:68c1] type 0 class 0x000300
[    1.604222] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.604233] pci 0000:01:00.0: reg 18: [mem 0xc4400000-0xc441ffff 64bit]
[    1.604241] pci 0000:01:00.0: reg 20: [io  0x4000-0x40ff]
[    1.604256] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    1.604274] pci 0000:01:00.0: supports D1 D2
[    1.604292] pci 0000:01:00.1: [1002:aa60] type 0 class 0x000403
[    1.604307] pci 0000:01:00.1: reg 10: [mem 0xc4420000-0xc4423fff 64bit]
[    1.604356] pci 0000:01:00.1: supports D1 D2
[    1.604379] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.604382] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.604384] pci 0000:00:01.0:   bridge window [mem 0xc4400000-0xc44fffff]
[    1.604387] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.604498] pci 0000:02:00.0: [14e4:4727] type 0 class 0x000280
[    1.604528] pci 0000:02:00.0: reg 10: [mem 0xc3400000-0xc3403fff 64bit]
[    1.604650] pci 0000:02:00.0: supports D1 D2
[    1.604701] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.604705] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.604710] pci 0000:00:1c.0:   bridge window [mem 0xc3400000-0xc43fffff]
[    1.604717] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.604786] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    1.604804] pci 0000:03:00.0: reg 10: [io  0x2000-0x20ff]
[    1.604834] pci 0000:03:00.0: reg 18: [mem 0xc1404000-0xc1404fff 64bit pref]
[    1.604853] pci 0000:03:00.0: reg 20: [mem 0xc1400000-0xc1403fff 64bit pref]
[    1.604866] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    1.604905] pci 0000:03:00.0: supports D1 D2
[    1.604906] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.604911] pci 0000:03:00.0: PME# disabled
[    1.604946] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.604951] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    1.604955] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc33fffff]
[    1.604962] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.605034] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    1.605039] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.605043] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.605051] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.605052] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.605054] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.605056] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.605057] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    1.605079] pci_bus 0000:00: on NUMA node 0
[    1.605081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.605204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.605235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.605248] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20110112/nspredef-456)
[    1.605274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.605305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.605376] \_SB_.PCI0:_OSC invalid UUID
[    1.605377] _OSC request data:1 1f 1f 
[    1.605381]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.605408] \_SB_.PCI0:_OSC invalid UUID
[    1.605409] _OSC request data:1 0 1d 
[    1.609084] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 7f])
[    1.609133] pci 0000:7f:00.0: [8086:2c62] type 0 class 0x000600
[    1.609150] pci 0000:7f:00.1: [8086:2d01] type 0 class 0x000600
[    1.609168] pci 0000:7f:02.0: [8086:2d10] type 0 class 0x000600
[    1.609182] pci 0000:7f:02.1: [8086:2d11] type 0 class 0x000600
[    1.609197] pci 0000:7f:02.2: [8086:2d12] type 0 class 0x000600
[    1.609212] pci 0000:7f:02.3: [8086:2d13] type 0 class 0x000600
[    1.609235] pci_bus 0000:7f: on NUMA node 0
[    1.609241]  pci0000:7f: Requesting ACPI _OSC control (0x1d)
[    1.609423] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.609462] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.609498] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.609535] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.609572] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.609609] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.609646] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.609682] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.609767] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.609774] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.609778] vgaarb: loaded
[    1.609931] SCSI subsystem initialized
[    1.609984] libata version 3.00 loaded.
[    1.610018] usbcore: registered new interface driver usbfs
[    1.610026] usbcore: registered new interface driver hub
[    1.610043] usbcore: registered new device driver usb
[    1.610220] wmi: Mapper loaded
[    1.610222] PCI: Using ACPI for IRQ routing
[    1.610223] PCI: pci_cache_line_size set to 64 bytes
[    1.610299] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
[    1.610301] reserve RAM buffer: 000000009b63f000 - 000000009bffffff 
[    1.610303] reserve RAM buffer: 000000009b800000 - 000000009bffffff 
[    1.610389] NetLabel: Initializing
[    1.610390] NetLabel:  domain hash size = 128
[    1.610391] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.610399] NetLabel:  unlabeled traffic allowed by default
[    1.610443] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.610447] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.612469] Switching to clocksource hpet
[    1.615370] Switched to NOHz mode on CPU #0
[    1.615414] Switched to NOHz mode on CPU #3
[    1.615421] Switched to NOHz mode on CPU #1
[    1.615461] Switched to NOHz mode on CPU #2
[    1.617548] AppArmor: AppArmor Filesystem Enabled
[    1.617569] pnp: PnP ACPI init
[    1.617581] ACPI: bus type pnp registered
[    1.617883] pnp 00:00: [bus 00-7e]
[    1.617885] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.617887] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.617888] pnp 00:00: [io  0x0d00-0xffff window]
[    1.617890] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.617891] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.617893] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.617894] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.617896] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.617897] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.617899] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.617900] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.617902] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.617903] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.617904] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.617906] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.617907] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.617910] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.617912] pnp 00:00: [mem 0xa0000000-0xfeafffff window]
[    1.617973] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.618042] pnp 00:01: [io  0x0000-0x001f]
[    1.618044] pnp 00:01: [io  0x0081-0x0091]
[    1.618045] pnp 00:01: [io  0x0093-0x009f]
[    1.618046] pnp 00:01: [io  0x00c0-0x00df]
[    1.618048] pnp 00:01: [dma 4]
[    1.618072] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.618078] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.618101] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.618174] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.618198] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.618206] pnp 00:04: [io  0x00f0]
[    1.618216] pnp 00:04: [irq 13]
[    1.618240] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.618248] pnp 00:05: [io  0x002e-0x002f]
[    1.618250] pnp 00:05: [io  0x004e-0x004f]
[    1.618251] pnp 00:05: [io  0x0061]
[    1.618252] pnp 00:05: [io  0x0063]
[    1.618253] pnp 00:05: [io  0x0065]
[    1.618254] pnp 00:05: [io  0x0067]
[    1.618255] pnp 00:05: [io  0x0070]
[    1.618257] pnp 00:05: [io  0x0080]
[    1.618258] pnp 00:05: [io  0x0092]
[    1.618259] pnp 00:05: [io  0x00b2-0x00b3]
[    1.618260] pnp 00:05: [io  0x0680-0x069f]
[    1.618262] pnp 00:05: [io  0x0800-0x080f]
[    1.618263] pnp 00:05: [io  0xffff]
[    1.618264] pnp 00:05: [io  0xffff]
[    1.618265] pnp 00:05: [io  0x0400-0x047f]
[    1.618266] pnp 00:05: [io  0x0500-0x057f]
[    1.618268] pnp 00:05: [io  0x164e-0x164f]
[    1.618269] pnp 00:05: [io  0x0380-0x038e]
[    1.618320] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.618322] system 00:05: [io  0x0800-0x080f] has been reserved
[    1.618324] system 00:05: [io  0xffff] has been reserved
[    1.618325] system 00:05: [io  0xffff] has been reserved
[    1.618327] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.618329] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.618330] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.618332] system 00:05: [io  0x0380-0x038e] has been reserved
[    1.618334] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.618341] pnp 00:06: [io  0x0070-0x0077]
[    1.618345] pnp 00:06: [irq 8]
[    1.618372] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.618380] pnp 00:07: [io  0x0060]
[    1.618381] pnp 00:07: [io  0x0064]
[    1.618385] pnp 00:07: [irq 1]
[    1.618410] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.618424] pnp 00:08: [irq 12]
[    1.618450] pnp 00:08: Plug and Play ACPI device, IDs SYN1e1d SYN1e00 SYN0002 PNP0f13 (active)
[    1.618529] pnp 00:09: [irq 23]
[    1.618564] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.618726] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.618728] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    1.618729] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.618731] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.618732] pnp 00:0a: [mem 0xf0000000-0xf1ffffff]
[    1.618733] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.618735] pnp 00:0a: [mem 0xfed90000-0xfed8ffff disabled]
[    1.618736] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.618738] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.618739] pnp 00:0a: [mem 0xc4600000-0xc4600fff]
[    1.618790] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.618793] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.618794] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.618796] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.618798] system 00:0a: [mem 0xf0000000-0xf1ffffff] has been reserved
[    1.618800] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.618802] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.618804] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.618805] system 00:0a: [mem 0xc4600000-0xc4600fff] has been reserved
[    1.618808] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.816823] pnp 00:0b: [bus 7f]
[    1.816861] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.816874] pnp: PnP ACPI: found 12 devices
[    1.816875] ACPI: ACPI bus type pnp unregistered
[    1.816878] PnPBIOS: Disabled by ACPI PNP
[    1.852556] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.852559] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.852598] pci 0000:01:00.0: BAR 6: assigned [mem 0xc4440000-0xc445ffff pref]
[    1.852601] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.852603] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.852605] pci 0000:00:01.0:   bridge window [mem 0xc4400000-0xc44fffff]
[    1.852608] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.852611] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.852614] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.852620] pci 0000:00:1c.0:   bridge window [mem 0xc3400000-0xc43fffff]
[    1.852624] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.852632] pci 0000:03:00.0: BAR 6: assigned [mem 0xc1410000-0xc141ffff pref]
[    1.852633] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.852636] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    1.852642] pci 0000:00:1c.1:   bridge window [mem 0xc2400000-0xc33fffff]
[    1.852647] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.852654] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    1.852655] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.852660] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.852665] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.852680] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.852683] pci 0000:00:01.0: setting latency timer to 64
[    1.852693] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.852697] pci 0000:00:1c.0: setting latency timer to 64
[    1.852704] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.852708] pci 0000:00:1c.1: setting latency timer to 64
[    1.852716] pci 0000:00:1e.0: setting latency timer to 64
[    1.852720] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.852722] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.852724] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.852725] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.852727] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.852728] pci_bus 0000:01: resource 1 [mem 0xc4400000-0xc44fffff]
[    1.852730] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    1.852732] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    1.852733] pci_bus 0000:02: resource 1 [mem 0xc3400000-0xc43fffff]
[    1.852735] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.852737] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    1.852738] pci_bus 0000:03: resource 1 [mem 0xc2400000-0xc33fffff]
[    1.852740] pci_bus 0000:03: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.852742] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.852743] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.852745] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.852746] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.852771] NET: Registered protocol family 2
[    1.852820] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.852962] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.853263] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.853401] TCP: Hash tables configured (established 131072 bind 65536)
[    1.853402] TCP reno registered
[    1.853404] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.853410] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.853479] NET: Registered protocol family 1
[    1.853490] pci 0000:00:02.0: Boot video device
[    1.884517] PCI: CLS 64 bytes, default 64
[    1.884542] Simple Boot Flag at 0x44 set to 0x1
[    1.884781] cpufreq-nforce2: No nForce2 chipset.
[    1.884910] audit: initializing netlink socket (disabled)
[    1.884917] type=2000 audit(1315459422.264:1): initialized
[    1.891832] highmem bounce pool size: 64 pages
[    1.891836] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.893044] VFS: Disk quotas dquot_6.5.2
[    1.893087] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.893541] fuse init (API version 7.16)
[    1.893608] msgmni has been set to 1691
[    1.893801] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.893825] io scheduler noop registered
[    1.893827] io scheduler deadline registered
[    1.893838] io scheduler cfq registered (default)
[    1.893916] pcieport 0000:00:01.0: setting latency timer to 64
[    1.893942] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.894093] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.894109] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.894147] intel_idle: MWAIT substates: 0x1120
[    1.894149] intel_idle: v0.4 model 0x25
[    1.894150] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.945474] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.997479] ACPI: AC Adapter [ACAD] (on-line)
[    1.997537] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.997542] ACPI: Power Button [PWRB]
[    1.997572] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.997887] ACPI: Lid Switch [LID0]
[    1.997931] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.997934] ACPI: Power Button [PWRF]
[    1.998068] ACPI: acpi_idle yielding to intel_idle
[    2.197635] [Firmware Bug]: Invalid critical threshold (0)
[    2.199169] thermal LNXTHERM:00: registered as thermal_zone0
[    2.199171] ACPI: Thermal Zone [TZ01] (53 C)
[    2.199216] ERST: Table is not found!
[    2.199268] isapnp: Scanning for PnP cards...
[    2.199277] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.403429] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.403436] ACPI: Battery Slot [BAT0] (battery present)
[    2.553555] isapnp: No Plug & Play device found
[    2.558004] Linux agpgart interface v0.103
[    2.558078] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    2.558129] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.558783] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    2.558922] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    2.559784] brd: module loaded
[    2.560182] loop: module loaded
[    2.560251] i2c-core: driver [adp5520] using legacy suspend method
[    2.560252] i2c-core: driver [adp5520] using legacy resume method
[    2.560577] Fixed MDIO Bus: probed
[    2.560604] PPP generic driver version 2.4.2
[    2.560630] tun: Universal TUN/TAP device driver, 1.6
[    2.560632] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.560694] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.560713] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.560729] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.560733] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.560758] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.560818] ehci_hcd 0000:00:1a.0: debug port 2
[    2.564734] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.564753] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc450a000
[    2.580534] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.580686] hub 1-0:1.0: USB hub found
[    2.580690] hub 1-0:1.0: 3 ports detected
[    2.580753] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.580763] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.580766] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.580792] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.580836] ehci_hcd 0000:00:1d.0: debug port 2
[    2.584725] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.584737] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xc4509000
[    2.600536] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.600672] hub 2-0:1.0: USB hub found
[    2.600675] hub 2-0:1.0: 3 ports detected
[    2.600723] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.600732] uhci_hcd: USB Universal Host Controller Interface driver
[    2.600808] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.621161] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.621166] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.621258] mousedev: PS/2 mouse device common for all mice
[    2.623888] rtc_cmos 00:06: RTC can wake from S4
[    2.623937] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.623966] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.624018] device-mapper: uevent: version 1.0.3
[    2.624070] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.624121] device-mapper: multipath: version 1.2.0 loaded
[    2.624124] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.624171] EISA: Probing bus 0 at eisa.0
[    2.624173] EISA: Cannot allocate resource for mainboard
[    2.624175] Cannot allocate resource for EISA slot 1
[    2.624176] Cannot allocate resource for EISA slot 2
[    2.624177] Cannot allocate resource for EISA slot 3
[    2.624178] Cannot allocate resource for EISA slot 4
[    2.624179] Cannot allocate resource for EISA slot 5
[    2.624180] Cannot allocate resource for EISA slot 6
[    2.624181] Cannot allocate resource for EISA slot 7
[    2.624182] Cannot allocate resource for EISA slot 8
[    2.624183] EISA: Detected 0 cards.
[    2.624300] cpuidle: using governor ladder
[    2.624415] cpuidle: using governor menu
[    2.624674] TCP cubic registered
[    2.624880] NET: Registered protocol family 10
[    2.625719] NET: Registered protocol family 17
[    2.625741] Registering the dns_resolver key type
[    2.627522] Using IPI No-Shortcut mode
[    2.627589] PM: Hibernation image not present or could not be loaded.
[    2.627597] registered taskstats version 1
[    2.627880]   Magic number: 11:967:364
[    2.627998] rtc_cmos 00:06: setting system clock to 2011-09-08 05:23:43 UTC (1315459423)
[    2.628000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.628001] EDD information not available.
[    2.628117] Freeing unused kernel memory: 700k freed
[    2.628288] Write protecting the kernel text: 5192k
[    2.628355] Write protecting the kernel read-only data: 2148k
[    2.645625] <30>udev[72]: starting version 167
[    2.646147] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.789071] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.789096] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.789140] r8169 0000:03:00.0: setting latency timer to 64
[    2.789207] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[    2.789761] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf8102000, 98:4b:e1:94:ee:d1, XID 083000c0 IRQ 41
[    2.796259] ahci 0000:00:1f.2: version 3.0
[    2.796278] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.796323] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.796416] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    2.796420] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    2.796426] ahci 0000:00:1f.2: setting latency timer to 64
[    2.809501] scsi0 : ahci
[    2.809681] scsi1 : ahci
[    2.809784] scsi2 : ahci
[    2.809867] scsi3 : ahci
[    2.809959] scsi4 : ahci
[    2.810031] scsi5 : ahci
[    2.810086] ata1: SATA max UDMA/133 abar m2048@0xc4508000 port 0xc4508100 irq 42
[    2.810090] ata2: SATA max UDMA/133 abar m2048@0xc4508000 port 0xc4508180 irq 42
[    2.810093] ata3: DUMMY
[    2.810094] ata4: DUMMY
[    2.810095] ata5: DUMMY
[    2.810099] ata6: SATA max UDMA/133 abar m2048@0xc4508000 port 0xc4508380 irq 42
[    2.884637] Refined TSC clocksource calibration: 2659.999 MHz.
[    2.884644] Switching to clocksource tsc
[    2.892632] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.025295] hub 1-1:1.0: USB hub found
[    3.025376] hub 1-1:1.0: 6 ports detected
[    3.128634] ata6: SATA link down (SStatus 0 SControl 300)
[    3.128672] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.128709] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.129186] ata1.00: ATA-9: C300-CTFDDAC128MAG, 0006, max UDMA/100
[    3.129192] ata1.00: 250069680 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    3.129696] ata1.00: configured for UDMA/100
[    3.129873] scsi 0:0:0:0: Direct-Access     ATA      C300-CTFDDAC128M 0006 PQ: 0 ANSI: 5
[    3.130079] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.130082] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    3.130154] sd 0:0:0:0: [sda] Write Protect is off
[    3.130156] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.130180] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.131072]  sda: sda1 sda2 sda3 < sda5 >
[    3.131541] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.132155] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0200, max UDMA/100
[    3.134549] ata2.00: configured for UDMA/100
[    3.136639] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.138452] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0200 PQ: 0 ANSI: 5
[    3.148295] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.148299] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.148435] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.148499] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.177474] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    3.177477] EXT4-fs (sda2): write access will be enabled during recovery
[    3.181282] EXT4-fs (sda2): recovery complete
[    3.181517] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.273401] hub 2-1:1.0: USB hub found
[    3.273520] hub 2-1:1.0: 8 ports detected
[    3.348772] usb 1-1.2: new low speed USB device using ehci_hcd and address 3
[    3.364051] Adding 3905532k swap on /dev/sda1.  Priority:-1 extents:1 across:3905532k SS
[    3.417486] <30>udev[339]: starting version 167
[    3.426770] lp: driver loaded but no devices found
[    3.517715] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
[    3.573006] lib80211: common routines for IEEE802.11 drivers
[    3.573010] lib80211_crypt: registered algorithm 'NULL'
[    3.575056] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.575059] Disabling lock debugging due to kernel taint
[    3.579551] hp_accel: laptop model unknown, using default axes configuration
[    3.580169] lis3lv02d: 8 bits sensor found
[    3.605744] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[    3.605760] intel ips 0000:00:1f.6: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.605903] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[    3.622189] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[    3.623421] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.623429] wl 0000:02:00.0: setting latency timer to 64
[    3.644360] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input4
[    3.644471] Registered led device: hp::hddprotect
[    3.644487] hp_accel: driver loaded
[    3.661899] [drm] Initialized drm 1.1.0 20060810
[    3.670621] lib80211_crypt: registered algorithm 'TKIP'
[    3.684796] usb 2-1.3: new full speed USB device using ehci_hcd and address 3
[    3.687916] input: HP WMI hotkeys as /devices/virtual/input/input5
[    3.717892] [drm] radeon defaulting to kernel modesetting.
[    3.717895] [drm] radeon kernel modesetting enabled.
[    3.717913] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    3.717952] radeon 0000:01:00.0: power state changed by ACPI to D0
[    3.717956] radeon 0000:01:00.0: power state changed by ACPI to D0
[    3.717960] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    3.717969] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.717975] radeon 0000:01:00.0: setting latency timer to 64
[    3.718772] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68C1).
[    3.718812] [drm] register mmio base: 0xC4400000
[    3.718814] [drm] register mmio size: 131072
[    3.739463] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[    3.759302] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.759306] i915 0000:00:02.0: setting latency timer to 64
[    3.848857] usb 2-1.5: new high speed USB device using ehci_hcd and address 4
[    4.212109] ATOM BIOS: MADISON
[    4.212137] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    4.212139] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    4.212146] mtrr: no more MTRRs available
[    4.212148] [drm] Detected VRAM RAM=1024M, BAR=256M
[    4.212149] [drm] RAM width 128bits DDR
[    4.212211] [TTM] Zone  kernel: Available graphics memory: 433286 kiB.
[    4.212212] [TTM] Zone highmem: Available graphics memory: 1251594 kiB.
[    4.212214] [TTM] Initializing pool allocator.
[    4.212229] [drm] radeon: 1024M of VRAM memory ready
[    4.212230] [drm] radeon: 512M of GTT memory ready.
[    4.212240] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.212241] [drm] Driver supports precise vblank timestamp query.
[    4.212277] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[    4.212281] radeon 0000:01:00.0: radeon: using MSI.
[    4.212315] [drm] radeon: irq initialized.
[    4.212318] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.212646] [drm] Loading REDWOOD Microcode
[    4.232395] Linux video capture interface: v2.00
[    4.235301] uvcvideo: Found UVC 1.00 device HP Webcam (064e:f209)
[    4.240377] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input6
[    4.240429] usbcore: registered new interface driver uvcvideo
[    4.240430] USB Video Class driver (v1.0.0)
[    4.478775] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    4.490962] type=1400 audit(1315459425.359:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=500 comm="apparmor_parser"
[    4.490969] type=1400 audit(1315459425.359:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
[    4.491590] type=1400 audit(1315459425.359:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[    4.491706] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    4.491885] type=1400 audit(1315459425.359:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=573 comm="apparmor_parser"
[    4.491988] type=1400 audit(1315459425.359:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[    4.492471] type=1400 audit(1315459425.359:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=573 comm="apparmor_parser"
[    4.492896] type=1400 audit(1315459425.363:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=573 comm="apparmor_parser"
[    4.494119] type=1400 audit(1315459425.363:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=500 comm="apparmor_parser"
[    4.494622] type=1400 audit(1315459425.363:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=500 comm="apparmor_parser"
[    5.548404] input: USB Wheel Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8
[    5.548693] generic-usb 0003:04FC:0003.0001: input,hidraw0: USB HID v1.00 Mouse [USB Wheel Mouse] on usb-0000:00:1a.0-1.2/input0
[    5.548721] usbcore: registered new interface driver usbhid
[    5.548723] usbhid: USB HID core driver
[    5.586841] Bluetooth: Core ver 2.15
[    5.586868] NET: Registered protocol family 31
[    5.586870] Bluetooth: HCI device and connection manager initialized
[    5.586872] Bluetooth: HCI socket layer initialized
[    5.589012] radeon 0000:01:00.0: WB enabled
[    5.590973] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    5.591474] usbcore: registered new interface driver btusb
[    5.605516] [drm] ring test succeeded in 1 usecs
[    5.605699] [drm] radeon: ib pool ready.
[    5.605785] [drm] ib test succeeded in 0 usecs
[    5.606236] [drm] Radeon Display Connectors
[    5.606238] [drm] Connector 0:
[    5.606239] [drm]   LVDS
[    5.606242] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    5.606244] [drm]   Encoders:
[    5.606246] [drm]     LCD1: INTERNAL_UNIPHY
[    5.606247] [drm] Connector 1:
[    5.606249] [drm]   HDMI-A
[    5.606250] [drm]   HPD1
[    5.606252] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    5.606254] [drm]   Encoders:
[    5.606255] [drm]     DFP1: INTERNAL_UNIPHY1
[    5.606257] [drm] Connector 2:
[    5.606258] [drm]   VGA
[    5.606260] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[    5.606262] [drm]   Encoders:
[    5.606263] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.796868] [drm] Internal thermal controller with fan control
[    5.796922] [drm] radeon: power management initialized
[    6.094999] [drm] fb mappable at 0xA0141000
[    6.095001] [drm] vram apper at 0xA0000000
[    6.095002] [drm] size 4325376
[    6.095003] [drm] fb depth is 24
[    6.095004] [drm]    pitch is 5632
[    6.095680] Console: switching to colour frame buffer device 170x48
[    6.095699] fb0: radeondrmfb frame buffer device
[    6.095700] drm: registered panic notifier
[    6.095706] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[    6.107040] mtrr: no more MTRRs available
[    6.107043] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    6.107453] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    6.107458] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.107459] [drm] Driver supports precise vblank timestamp query.
[    6.177175] vga_switcheroo: enabled
[    6.177207] radeon atpx: version is 1
[    6.238340] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    6.238345] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    6.312247] fbcon: inteldrmfb (fb1) is primary device
[    6.312251] fbcon: Remapping primary device, fb1, to tty 1-63
[    6.368069] fb1: inteldrmfb frame buffer device
[    6.374274] acpi device:02: registered as cooling_device4
[    6.374427] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    6.374461] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    6.377678] acpi device:14: registered as cooling_device5
[    6.382626] acpi device:15: registered as cooling_device6
[    6.382686] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/LNXVIDEO:02/input/input10
[    6.382728] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    6.382908] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[    6.382964] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.383036] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    6.383069] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.532441] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.661379] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.661547] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.662090] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.662177] HDA Intel 0000:01:00.1: irq 46 for MSI/MSI-X
[    7.662206] HDA Intel 0000:01:00.1: setting latency timer to 64
[    7.677115] hda-intel: Enable sync_write for AMD chipset
[    7.832476] ppdev: user-space parallel port driver
[    7.852738] type=1400 audit(1315459428.719:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=939 comm="apparmor_parser"
[    7.853505] type=1400 audit(1315459428.723:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=939 comm="apparmor_parser"
[    7.881974] r8169 0000:03:00.0: eth0: link down
[    7.881982] r8169 0000:03:00.0: eth0: link down
[    7.882173] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.537628] type=1400 audit(1315459429.407:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=996 comm="apparmor_parser"
[    8.537926] type=1400 audit(1315459429.407:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=997 comm="apparmor_parser"
[    8.538545] type=1400 audit(1315459429.407:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=997 comm="apparmor_parser"
[    8.538953] type=1400 audit(1315459429.407:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=997 comm="apparmor_parser"
[    8.540268] type=1400 audit(1315459429.407:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1001 comm="apparmor_parser"
[    8.542372] type=1400 audit(1315459429.411:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=998 comm="apparmor_parser"
[    8.542739] type=1400 audit(1315459429.411:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1000 comm="apparmor_parser"
[    8.543369] type=1400 audit(1315459429.411:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1000 comm="apparmor_parser"
[    8.614398] Bluetooth: L2CAP ver 2.15
[    8.614402] Bluetooth: L2CAP socket layer initialized
[    8.621822] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.621826] Bluetooth: BNEP filters: protocol multicast

```


also i am not able to install the ati proprietary graphics driver for my ATI MobilityHD5600 so it seems that i am running now on my intel onboard graphics, at least it works this way.

I would like to thank you guys in advance for your awesome help!!!

Charly

---

