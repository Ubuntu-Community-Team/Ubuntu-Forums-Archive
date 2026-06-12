---
title: "Mouse Hangs"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by elitegoodguy on 2007-01-11
I have installed Ubuntu 6.10 on a Dell E521.  I have everything working great I only had two problems (one of which I have solved)

The monitor would not display the proper resolution 1680x1050 (20in Widescreen Dell Monitor) That was fixed by installing the NVidia driver.

But I am having a problem with my USB mouse.  After using it for 10-15 minutes my mouse just stops right in it's tracks.  USB Keyboard still works and I still have an arrow it just will not move.  The only way I can get it to move again is by unplugging it and plugging it back in.  Any idea on what the problem might be?

Before there are some requests for it I will post some system info.

lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d1 (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

dmesg
```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f3cc0
[17179569.184000] On node 0 totalpages: 261856
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32480 pages, LIFO batch:7
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f83d0
[17179569.184000] ACPI: RSDT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x3fee3040
[17179569.184000] ACPI: FADT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x3fee3100
[17179569.184000] ACPI: BOOT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x3fee8b40
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fee8c80
[17179569.184000] ACPI: HPET (v001 DELL    bMk     0x42302e31 AWRD 0x00000098) @ 0x3fee8f00
[17179569.184000] ACPI: MCFG (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x3fee8f80
[17179569.184000] ACPI: SLIC (v001 DELL    bMk     0x42302e31 AWRD 0x0100000e) @ 0x3fee9000
[17179569.184000] ACPI: MADT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x3fee8bc0
[17179569.184000] ACPI: DSDT (v001 DELL    BMK     0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:11 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:11 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x10b9a201 base: 0xfeff0000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] spurious 8259A interrupt: IRQ7.
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1028572k/1047424k available (1910k kernel code, 18128k reserved, 1069k data, 308k init, 129920k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfeff0000 (virtual 0xf8800000), IRQs 2, 8, 31
[17179569.184000] hpet0: 3 32-bit timers, 25000000 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2204.792 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 4413.37 BogoMIPS (lpj=8826753)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179569.268000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179569.268000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.268000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.268000] CPU 0(2) -> Core 0
[17179569.268000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.688000] Freeing initrd memory: 5322k freed
[17179569.688000] ACPI: Core revision 20060707
[17179569.688000] ACPI: Looking for DSDT ... not found!
[17179569.692000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[17179569.692000] SMP alternatives: switching to SMP code
[17179569.692000] Booting processor 1/1 eip 3000
[17179569.700000] Initializing CPU#1
[17179569.784000] Calibrating delay using timer specific routine.. 4408.93 BogoMIPS (lpj=8817863)
[17179569.784000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179569.784000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[17179569.784000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.784000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.784000] CPU 1(2) -> Core 1
[17179569.784000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[17179569.784000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[17179569.784000] Total of 2 processors activated (8822.30 BogoMIPS).
[17179569.784000] ENABLING IO-APIC IRQs
[17179569.788000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179569.796000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179569.796000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179569.796000] ...trying to set up timer as Virtual Wire IRQ... failed.
[17179569.796000] ...trying to set up timer as ExtINT IRQ... works.
[17179570.116000] checking TSC synchronization across 2 CPUs: 
[17179570.120000] Brought up 2 CPUs
[17179570.184000] migration_cost=4000
[17179570.184000] NET: Registered protocol family 16
[17179570.184000] EISA bus registered
[17179570.184000] ACPI: bus type pci registered
[17179570.184000] PCI: Using MMCONFIG
[17179570.184000] PCI: No mmconfig possible on 0:18
[17179570.184000] Setting up standard PCI resources
[17179570.188000] ACPI: Interpreter enabled
[17179570.188000] ACPI: Using IOAPIC for interrupt routing
[17179570.188000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.188000] PCI: Probing PCI hardware (bus 00)
[17179570.196000] Boot video device is 0000:03:00.0
[17179570.196000] PCI: Transparent bridge - 0000:00:10.0
[17179570.196000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.260000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.264000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.264000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.264000] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.264000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.264000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
[17179570.264000] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.264000] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[17179570.268000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179570.268000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[17179570.272000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.276000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.276000] pnp: PnP ACPI init
[17179570.280000] pnp: PnP ACPI: found 9 devices
[17179570.280000] PnPBIOS: Disabled by ACPI PNP
[17179570.280000] PCI: Using ACPI for IRQ routing
[17179570.280000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.280000] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[17179570.280000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[17179570.280000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[17179570.280000] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[17179570.280000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[17179570.280000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[17179570.280000] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[17179570.280000] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[17179570.280000] PCI: Bridge: 0000:00:02.0
[17179570.280000]   IO window: a000-afff
[17179570.280000]   MEM window: fde00000-fdefffff
[17179570.280000]   PREFETCH window: fdb00000-fdbfffff
[17179570.280000] PCI: Bridge: 0000:00:03.0
[17179570.280000]   IO window: 8000-8fff
[17179570.280000]   MEM window: fda00000-fdafffff
[17179570.280000]   PREFETCH window: fd900000-fd9fffff
[17179570.280000] PCI: Bridge: 0000:00:04.0
[17179570.280000]   IO window: b000-bfff
[17179570.280000]   MEM window: f8000000-faffffff
[17179570.280000]   PREFETCH window: d0000000-dfffffff
[17179570.280000] PCI: Bridge: 0000:00:10.0
[17179570.280000]   IO window: 9000-9fff
[17179570.280000]   MEM window: fdd00000-fddfffff
[17179570.280000]   PREFETCH window: fdc00000-fdcfffff
[17179570.280000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179570.280000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179570.280000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179570.280000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[17179570.280000] NET: Registered protocol family 2
[17179570.320000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.320000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.320000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.320000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.320000] TCP reno registered
[17179570.320000] Simple Boot Flag at 0x3a set to 0x1
[17179570.320000] audit: initializing netlink socket (disabled)
[17179570.320000] audit(1168358098.320:1): initialized
[17179570.320000] highmem bounce pool size: 64 pages
[17179570.320000] VFS: Disk quotas dquot_6.5.1
[17179570.320000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.320000] Initializing Cryptographic API
[17179570.320000] io scheduler noop registered
[17179570.320000] io scheduler anticipatory registered
[17179570.320000] io scheduler deadline registered
[17179570.320000] io scheduler cfq registered (default)
[17179570.320000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179570.320000] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[17179570.320000] assign_interrupt_mode Found MSI capability
[17179570.320000] Allocate Port Service[0000:00:02.0:pcie00]
[17179570.320000] Allocate Port Service[0000:00:02.0:pcie03]
[17179570.320000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179570.320000] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[17179570.320000] assign_interrupt_mode Found MSI capability
[17179570.320000] Allocate Port Service[0000:00:03.0:pcie00]
[17179570.320000] Allocate Port Service[0000:00:03.0:pcie03]
[17179570.320000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179570.320000] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[17179570.320000] assign_interrupt_mode Found MSI capability
[17179570.320000] Allocate Port Service[0000:00:04.0:pcie00]
[17179570.320000] Allocate Port Service[0000:00:04.0:pcie03]
[17179570.320000] isapnp: Scanning for PnP cards...
[17179570.676000] isapnp: No Plug & Play device found
[17179570.692000] Real Time Clock Driver v1.12ac
[17179570.692000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.692000] mice: PS/2 mouse device common for all mice
[17179570.696000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.696000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.696000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.696000] PNP: No PS/2 controller found. Probing ports directly.
[17179571.264000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.264000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.264000] EISA: Probing bus 0 at eisa.0
[17179571.264000] Cannot allocate resource for EISA slot 1
[17179571.264000] Cannot allocate resource for EISA slot 2
[17179571.264000] Cannot allocate resource for EISA slot 8
[17179571.264000] EISA: Detected 0 cards.
[17179571.268000] TCP bic registered
[17179571.268000] NET: Registered protocol family 1
[17179571.268000] NET: Registered protocol family 8
[17179571.268000] NET: Registered protocol family 20
[17179571.268000] Starting balanced_irq
[17179571.268000] Using IPI No-Shortcut mode
[17179571.268000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.268000] Freeing unused kernel memory: 308k freed
[17179571.352000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.408000] Capability LSM initialized
[17179572.776000] SCSI subsystem initialized
[17179572.776000] libata version 1.20 loaded.
[17179572.776000] sata_nv 0000:00:0e.0: version 0.8
[17179572.776000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179572.776000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 209
[17179572.776000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179572.776000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
[17179572.776000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xE008 irq 209
[17179572.980000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179573.156000] ata1: dev 0 cfg 49:2f00 82:3469 83:7f61 84:4003 85:3468 86:3c41 87:4003 88:407f
[17179573.156000] ata1: dev 0 ATA-6, max UDMA/133, 312500000 sectors: LBA48
[17179573.168000] ata1: dev 0 configured for UDMA/133
[17179573.168000] scsi0 : sata_nv
[17179573.372000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179573.708000] ata2: dev 0 cfg 49:0f00 82:0000 83:4000 84:4000 85:0000 86:0000 87:4000 88:0407
[17179573.708000] ata2: dev 0 ATAPI, max UDMA/33
[17179573.880000] ata2: dev 0 configured for UDMA/33
[17179573.880000] scsi1 : sata_nv
[17179573.880000]   Vendor: ATA       Model: WDC WD1600JD-75H  Rev: 08.0
[17179573.880000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.880000]   Vendor: TSSTcorp  Model: DVD+-RW TS-H653A  Rev: D300
[17179573.880000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179573.880000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[17179573.880000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 217
[17179573.880000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[17179573.880000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xCC00 irq 217
[17179573.880000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xCC08 irq 217
[17179574.084000] ata3: SATA link down (SStatus 0)
[17179574.084000] scsi2 : sata_nv
[17179574.292000] ata4: SATA link down (SStatus 0)
[17179574.292000] scsi3 : sata_nv
[17179574.308000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[17179574.308000] sda: Write Protect is off
[17179574.308000] sda: Mode Sense: 00 3a 00 00
[17179574.308000] SCSI device sda: drive cache: write back
[17179574.308000] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[17179574.308000] sda: Write Protect is off
[17179574.308000] sda: Mode Sense: 00 3a 00 00
[17179574.308000] SCSI device sda: drive cache: write back
[17179574.308000]  sda: sda1 sda2 < sda5 >
[17179574.376000] sd 0:0:0:0: Attached scsi disk sda
[17179574.640000] Probing IDE interface ide0...
[17179574.668000] usbcore: registered new driver usbfs
[17179574.668000] usbcore: registered new driver hub
[17179574.668000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[17179574.668000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 225
[17179574.668000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[17179574.668000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[17179574.668000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[17179574.668000] ehci_hcd 0000:00:0b.1: debug port 1
[17179574.668000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[17179574.668000] ehci_hcd 0000:00:0b.1: irq 225, io mem 0xfe02e000
[17179574.668000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.668000] usb usb1: configuration #1 chosen from 1 choice
[17179574.668000] hub 1-0:1.0: USB hub found
[17179574.668000] hub 1-0:1.0: 8 ports detected
[17179574.672000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179574.680000] ieee1394: Initialized config rom entry `ip1394'
[17179574.776000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[17179574.776000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 20 (level, low) -> IRQ 233
[17179574.776000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179574.776000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179574.776000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[17179575.444000] ohci_hcd 0000:00:0b.0: irq 233, io mem 0xfe02f000
[17179575.504000] usb usb2: configuration #1 chosen from 1 choice
[17179575.504000] hub 2-0:1.0: USB hub found
[17179575.504000] hub 2-0:1.0: 8 ports detected
[17179575.612000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179575.612000] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 50
[17179575.612000] PCI: Setting latency timer of device 0000:04:08.0 to 64
[17179575.664000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[50]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[17179575.836000] Probing IDE interface ide1...
[17179575.916000] usb 2-4: new full speed USB device using ohci_hcd and address 2
[17179576.148000] usb 2-4: configuration #1 chosen from 1 choice
[17179576.148000] hub 2-4:1.0: USB hub found
[17179576.152000] hub 2-4:1.0: 3 ports detected
[17179576.412000] Attempting manual resume
[17179576.420000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179576.420000] EXT3-fs: write access will be enabled during recovery.
[17179576.564000] usb 2-5: new low speed USB device using ohci_hcd and address 3
[17179576.776000] usb 2-5: configuration #1 chosen from 1 choice
[17179576.952000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000d100815666dc]
[17179577.080000] usb 2-7: new low speed USB device using ohci_hcd and address 4
[17179577.288000] usb 2-7: configuration #1 chosen from 1 choice
[17179577.396000] kjournald starting.  Commit interval 5 seconds
[17179577.396000] EXT3-fs: sda1: orphan cleanup on readonly fs
[17179577.424000] ext3_orphan_cleanup: deleting unreferenced inode 3915778
[17179577.428000] ext3_orphan_cleanup: deleting unreferenced inode 11026613
[17179577.444000] ext3_orphan_cleanup: deleting unreferenced inode 11028064
[17179577.452000] EXT3-fs: sda1: 3 orphan inodes deleted
[17179577.452000] EXT3-fs: recovery complete.
[17179577.524000] usb 2-4.2: new full speed USB device using ohci_hcd and address 5
[17179577.552000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.660000] usb 2-4.2: configuration #1 chosen from 1 choice
[17179577.896000] usb 2-4.3: new full speed USB device using ohci_hcd and address 6
[17179578.032000] usb 2-4.3: configuration #1 chosen from 1 choice
[17179578.036000] usbcore: registered new driver hiddev
[17179578.048000] input: Logitech Optical USB Mouse as /class/input/input1
[17179578.048000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-5
[17179578.056000] input: Dell Dell USB Keyboard as /class/input/input2
[17179578.056000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-7
[17179578.068000] input: Logitech BT Mini-Receiver as /class/input/input3
[17179578.068000] input: USB HID v1.11 Keyboard [Logitech BT Mini-Receiver] on usb-0000:00:0b.0-4.2
[17179578.080000] input: Logitech BT Mini-Receiver as /class/input/input4
[17179578.080000] input,hiddev96: USB HID v1.11 Mouse [Logitech BT Mini-Receiver] on usb-0000:00:0b.0-4.3
[17179578.080000] usbcore: registered new driver usbhid
[17179578.080000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179585.348000] input: PC Speaker as /class/input/input5
[17179585.396000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.396000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.612000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.612000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179585.636000] b44.c:v1.00 (Apr 7, 2006)
[17179585.636000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179585.636000] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 58
[17179585.636000] PCI: Setting latency timer of device 0000:04:07.0 to 64
[17179585.640000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:18:8b:58:aa:eb
[17179585.756000] ts: Compaq touchscreen protocol output
[17179585.788000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[17179585.788000] Uniform CD-ROM driver Revision: 3.20
[17179585.788000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179585.804000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.888000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[17179585.888000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 209
[17179585.888000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[17179586.800000] lp: driver loaded but no devices found
[17179586.808000] NET: Registered protocol family 17
[17179586.832000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179586.832000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179586.860000] Adding 3028212k swap on /dev/disk/by-uuid/04b58ba8-e937-4006-9bbb-c029c34a384e.  Priority:-1 extents:1 across:3028212k
[17179586.944000] EXT3 FS on sda1, internal journal
[17179588.748000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179588.748000] b44: eth0: Flow control is off for TX and off for RX.
[17179592.376000] ACPI: Power Button (FF) [PWRF]
[17179592.376000] ACPI: Power Button (CM) [PWRB]
[17179592.484000] ibm_acpi: ec object not found
[17179592.520000] pcc_acpi: loading...
[17179592.820000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179592.820000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xe (1200 mV)
[17179592.820000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x10 (1150 mV)
[17179592.820000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10 (1150 mV)
[17179592.820000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179592.820000] cpu_init done, current fid 0xe, vid 0xe
[17179595.500000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179595.500000] apm: disabled - APM is not SMP safe.
[17179598.348000] Bluetooth: Core ver 2.8
[17179598.348000] NET: Registered protocol family 31
[17179598.348000] Bluetooth: HCI device and connection manager initialized
[17179598.348000] Bluetooth: HCI socket layer initialized
[17179598.360000] Bluetooth: L2CAP ver 2.8
[17179598.360000] Bluetooth: L2CAP socket layer initialized
[17179598.376000] Bluetooth: RFCOMM socket layer initialized
[17179598.376000] Bluetooth: RFCOMM TTY layer initialized
[17179598.376000] Bluetooth: RFCOMM ver 1.7
[17179598.580000] usb 2-4.1: new full speed USB device using ohci_hcd and address 7
[17179598.716000] usb 2-4.1: configuration #1 chosen from 1 choice
[17179598.776000] Bluetooth: HCI USB driver ver 2.9
[17179598.776000] usbcore: registered new driver hci_usb
[17179607.572000] NET: Registered protocol family 10
[17179607.572000] lo: Disabled Privacy Extensions
[17179607.576000] IPv6 over IPv4 tunneling driver
[17179618.528000] eth0: no IPv6 routers present
[17180917.856000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180918.012000] ISO 9660 Extensions: RRIP_1991A
[17182553.388000] usb 2-5: USB disconnect, address 3
[17182557.388000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17182560.244000] usb 2-3: new low speed USB device using ohci_hcd and address 8
[17182560.456000] usb 2-3: configuration #1 chosen from 1 choice
[17182560.472000] input: Logitech Optical USB Mouse as /class/input/input6
[17182560.472000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17182621.040000] vmmon: module license 'unspecified' taints kernel.
[17182621.040000] /dev/vmmon[4085]: Module vmmon: registered with major=10 minor=165
[17182621.040000] /dev/vmmon[4085]: Module vmmon: initialized
[17182621.156000] /dev/vmnet: open called by PID 4116 (vmnet-bridge)
[17182621.160000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17182621.160000] /dev/vmnet: port on hub 0 successfully opened
[17182621.160000] bridge-eth0: enabling the bridge
[17182621.160000] bridge-eth0: up
[17182621.160000] bridge-eth0: already up
[17182621.160000] bridge-eth0: attached
[17182621.172000] /dev/vmnet: open called by PID 4128 (vmnet-natd)
[17182621.172000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17182621.172000] /dev/vmnet: port on hub 8 successfully opened
[17182631.192000] /dev/vmnet: open called by PID 4422 (vmnet-netifup)
[17182631.192000] /dev/vmnet: port on hub 8 successfully opened
[17182631.196000] /dev/vmnet: open called by PID 4424 (vmnet-netifup)
[17182631.196000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17182631.196000] /dev/vmnet: port on hub 1 successfully opened
[17182631.392000] /dev/vmnet: open called by PID 4450 (vmnet-dhcpd)
[17182631.392000] /dev/vmnet: port on hub 8 successfully opened
[17182631.396000] /dev/vmnet: open called by PID 4451 (vmnet-dhcpd)
[17182631.396000] /dev/vmnet: port on hub 1 successfully opened
[17182641.748000] vmnet1: no IPv6 routers present
[17182641.952000] vmnet8: no IPv6 routers present
[17182867.396000] usb 2-3: USB disconnect, address 8
[17182871.396000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17182910.036000] usb 2-3: new low speed USB device using ohci_hcd and address 9
[17182910.244000] usb 2-3: configuration #1 chosen from 1 choice
[17182910.256000] input: Logitech Optical USB Mouse as /class/input/input7
[17182910.256000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17183085.428000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17183085.460000] ISO 9660 Extensions: RRIP_1991A
[17183280.704000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[17183280.704000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 50
[17183280.704000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17183280.708000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17183298.192000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17183298.236000] ISO 9660 Extensions: RRIP_1991A
[17197236.324000] usb 2-3: USB disconnect, address 9
[17197240.324000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17197241.164000] usb 2-3: new low speed USB device using ohci_hcd and address 10
[17197241.376000] usb 2-3: configuration #1 chosen from 1 choice
[17197241.392000] input: Logitech Optical USB Mouse as /class/input/input8
[17197241.392000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17199724.924000] usb 2-3: USB disconnect, address 10
[17199728.924000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17199731.728000] usb 2-4: USB disconnect, address 2
[17199731.728000] usb 2-4.1: USB disconnect, address 7
[17199735.732000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17199735.980000] usb 2-4.2: USB disconnect, address 5
[17199735.980000] usb 2-4.3: USB disconnect, address 6
[17199736.596000] usb 2-3: new low speed USB device using ohci_hcd and address 11
[17199736.808000] usb 2-3: configuration #1 chosen from 1 choice
[17199736.820000] input: Logitech Optical USB Mouse as /class/input/input9
[17199736.820000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17201865.504000] usb 2-3: USB disconnect, address 11
[17201869.504000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17201870.596000] usb 2-3: new low speed USB device using ohci_hcd and address 12
[17201870.808000] usb 2-3: configuration #1 chosen from 1 choice
[17201870.820000] input: Logitech Optical USB Mouse as /class/input/input10
[17201870.820000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17252048.808000] usb 2-3: USB disconnect, address 12
[17252052.808000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17252053.424000] usb 2-3: new low speed USB device using ohci_hcd and address 13
[17252053.636000] usb 2-3: configuration #1 chosen from 1 choice
[17252053.648000] input: Logitech Optical USB Mouse as /class/input/input11
[17252053.648000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17253701.272000] usb 2-3: USB disconnect, address 13
[17253705.272000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17253705.888000] usb 2-3: new low speed USB device using ohci_hcd and address 14
[17253706.100000] usb 2-3: configuration #1 chosen from 1 choice
[17253706.116000] input: Logitech Optical USB Mouse as /class/input/input12
[17253706.116000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17265588.364000] usb 2-3: USB disconnect, address 14
[17265592.364000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17265592.980000] usb 2-3: new low speed USB device using ohci_hcd and address 15
[17265593.192000] usb 2-3: configuration #1 chosen from 1 choice
[17265593.208000] input: Logitech Optical USB Mouse as /class/input/input13
[17265593.208000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17268139.728000] usb 2-3: USB disconnect, address 15
[17268143.728000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17268144.344000] usb 2-3: new low speed USB device using ohci_hcd and address 16
[17268144.556000] usb 2-3: configuration #1 chosen from 1 choice
[17268144.568000] input: Logitech Optical USB Mouse as /class/input/input14
[17268144.568000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17268967.336000] usb 2-3: USB disconnect, address 16
[17268971.336000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17268971.952000] usb 2-3: new low speed USB device using ohci_hcd and address 17
[17268972.164000] usb 2-3: configuration #1 chosen from 1 choice
[17268972.176000] input: Logitech Optical USB Mouse as /class/input/input15
[17268972.176000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-3
[17269736.248000] usb 2-3: USB disconnect, address 17
[17269755.904000] usb 2-7: USB disconnect, address 4
[17349010.756000] ohci_hcd 0000:00:0b.0: wakeup
[17349011.140000] usb 2-6: new low speed USB device using ohci_hcd and address 18
[17349011.352000] usb 2-6: configuration #1 chosen from 1 choice
[17349011.364000] input: Logitech Optical USB Mouse as /class/input/input16
[17349011.364000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-6
[17349029.536000] usb 2-7: new low speed USB device using ohci_hcd and address 19
[17349029.748000] usb 2-7: configuration #1 chosen from 1 choice
[17349029.764000] input: Dell Dell USB Keyboard as /class/input/input17
[17349029.764000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-7
[17351310.176000] usb 2-6: USB disconnect, address 18
[17351314.176000] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[17351314.792000] usb 2-6: new low speed USB device using ohci_hcd and address 20
[17351315.004000] usb 2-6: configuration #1 chosen from 1 choice
[17351315.016000] input: Logitech Optical USB Mouse as /class/input/input18
[17351315.016000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-6


```

Hopefully someone can make sense of this and can recommend a few things to try.

Thanks

---

