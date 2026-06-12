---
title: "Toshiba a100 kernel / wireless issue"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by elglas on 2006-07-29
hello

I've recenly installed dapper on my new laptop here, however I needed to upgrade the kernel (since the ubuntu-686smp didn't work) to a custom one based on the kernel compilation guide for newbies (for dapper)

my current problem is that although ndiswrapper is installed and using the ini file from my windows partition (yes I dual boot) I have no wireless and recieve the folowing error(s)

```

$ sudo dmesg

[17179569.184000] Linux version 2.6.15.7-ubuntu1-toshiba100 (root@elglas-laptop) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 24 01:09:23 EDT 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fe70000 (usable)
[17179569.184000]  BIOS-e820: 000000003fe70000 - 000000003fe86000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fe86000 - 000000003ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6570
[17179569.184000] On node 0 totalpages: 261744
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32368 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f64c0
[17179569.184000] ACPI: RSDT (v001 TOSINV Capell00 0x06040000  LTP 0x00000000) @ 0x3fe7e15f
[17179569.184000] ACPI: FADT (v001 TOSINV CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe85dee
[17179569.184000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe85e62
[17179569.184000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe85eca
[17179569.184000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe85f02
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3fe85fd8
[17179569.184000] ACPI: MADT (v001 TOSINV   APIC   0x06040000  LTP 0x00000000) @ 0x3fe85f70
[17179569.184000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x3fe7f203
[17179569.184000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x3fe7eb71
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3fe7e1a7
[17179569.184000] ACPI: DSDT (v001 TOSINV CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1 already used, trying 2
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1026668k/1046976k available (2315k kernel code, 19504k reserved, 646k data, 248k init, 129472k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1995.106 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3994.92 BogoMIPS (lpj=7989843)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000040 0000c1a9 00000000 00000000
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.780000] Freeing initrd memory: 6747k freed
[17179569.784000] ACPI: Looking for DSDT ... not found!
[17179569.824000] CPU0: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17179569.824000] SMP alternatives: switching to SMP code
[17179569.824000] Booting processor 1/1 eip 3000
[17179569.836000] Initializing CPU#1
[17179569.916000] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=7980138)
[17179569.916000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.916000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.916000] monitor/mwait feature present.
[17179569.916000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.916000] CPU: L2 cache: 2048K
[17179569.916000] CPU: Hyper-Threading is disabled
[17179569.916000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000040 0000c1a9 00000000 00000000
[17179569.916000] CPU1: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17179569.916000] Total of 2 processors activated (7984.99 BogoMIPS).
[17179569.916000] ENABLING IO-APIC IRQs
[17179569.916000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.064000] checking TSC synchronization across 2 CPUs: passed.
[17179570.068000] Brought up 2 CPUs
[17179570.068000] NET: Registered protocol family 16
[17179570.068000] ACPI: bus type pci registered
[17179570.068000] PCI: PCI BIOS revision 2.10 entry at 0xfd875, last bus=7
[17179570.068000] PCI: Using MMCONFIG
[17179570.068000] ACPI: Subsystem revision 20051216
[17179570.072000] ACPI: Interpreter enabled
[17179570.072000] ACPI: Using IOAPIC for interrupt routing
[17179570.072000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.072000] PCI: Probing PCI hardware (bus 00)
[17179570.164000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179570.164000] Boot video device is 0000:01:00.0
[17179570.164000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[17179570.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.360000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.360000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.360000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.360000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.360000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.360000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.360000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.360000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.360000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179570.424000] ACPI: Power Resource [FN00] (off)
[17179570.424000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.424000] pnp: PnP ACPI init
[17179570.520000] pnp: PnP ACPI: found 11 devices
[17179570.520000] PCI: Using ACPI for IRQ routing
[17179570.520000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.548000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[17179570.548000] PCI: Bridge: 0000:00:01.0
[17179570.548000]   IO window: 2000-2fff
[17179570.548000]   MEM window: dc000000-ddffffff
[17179570.548000]   PREFETCH window: c0000000-cfffffff
[17179570.548000] PCI: Bridge: 0000:00:1c.0
[17179570.548000]   IO window: disabled.
[17179570.548000]   MEM window: disabled.
[17179570.548000]   PREFETCH window: disabled.
[17179570.548000] PCI: Bridge: 0000:00:1c.1
[17179570.548000]   IO window: 3000-3fff
[17179570.548000]   MEM window: d8000000-d9ffffff
[17179570.548000]   PREFETCH window: d2000000-d3ffffff
[17179570.548000] PCI: Bridge: 0000:00:1c.2
[17179570.548000]   IO window: 4000-4fff
[17179570.548000]   MEM window: da000000-dbffffff
[17179570.548000]   PREFETCH window: d4000000-d5ffffff
[17179570.548000] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[17179570.548000]   IO window: 00005400-000054ff
[17179570.548000]   IO window: 00005800-000058ff
[17179570.548000]   PREFETCH window: 50000000-51ffffff
[17179570.548000]   MEM window: 52000000-53ffffff
[17179570.548000] PCI: Bridge: 0000:00:1e.0
[17179570.548000]   IO window: 5000-5fff
[17179570.548000]   MEM window: de000000-de0fffff
[17179570.548000]   PREFETCH window: 50000000-51ffffff
[17179570.548000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.548000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.548000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179570.548000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.548000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
[17179570.548000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.548000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.548000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.548000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.548000] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[17179570.548000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179570.548000] Simple Boot Flag at 0x36 set to 0x1
[17179570.552000] audit: initializing netlink socket (disabled)
[17179570.552000] audit(1154211440.548:1): initialized
[17179570.552000] highmem bounce pool size: 64 pages
[17179570.552000] VFS: Disk quotas dquot_6.5.1
[17179570.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.552000] Initializing Cryptographic API
[17179570.552000] io scheduler noop registered
[17179570.552000] io scheduler anticipatory registered
[17179570.552000] io scheduler deadline registered
[17179570.552000] io scheduler cfq registered
[17179570.552000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.552000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.552000] assign_interrupt_mode Found MSI capability
[17179570.552000] Allocate Port Service[pcie00]
[17179570.552000] Allocate Port Service[pcie03]
[17179570.552000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177

[17179570.676000] mice: PS/2 mouse device common for all mice
[17179570.680000] NET: Registered protocol family 2
[17179570.728000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.728000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[17179570.728000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179570.728000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.728000] TCP reno registered
[17179570.728000] TCP bic registered
[17179570.728000] NET: Registered protocol family 1
[17179570.728000] NET: Registered protocol family 8
[17179570.728000] NET: Registered protocol family 20
[17179570.728000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179570.728000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179570.728000] ieee80211_crypt: registered algorithm 'NULL'
[17179570.728000] ieee80211_crypt: registered algorithm 'WEP'
[17179570.728000] Starting balanced_irq
[17179570.728000] Using IPI No-Shortcut mode
[17179570.728000] ACPI wakeup devices:
[17179570.728000]  LID HDEF PXS1 PXS2 PXS3 LANC
[17179570.728000] ACPI: (supports S0 S3 S4 S5)
[17179570.728000] Freeing unused kernel memory: 248k freed
[17179570.772000] vga16fb: initializing
[17179570.772000] vga16fb: mapped to 0xc00a0000
[17179570.772000] fb0: VGA16 VGA frame buffer device
[17179570.844000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.168000] SCSI subsystem initialized
[17179572.168000] ACPI: bus type scsi registered
[17179572.168000] libata version 1.20 loaded.
[17179572.172000] ata_piix 0000:00:1f.2: version 1.05
[17179572.172000] ata_pci_init_one: pci_dev class+intf: 0x10180
[17179572.172000] ata_pci_init_one: NO_LEGACY == 0
[17179572.172000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 233
[17179572.172000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179572.172000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x18B0 irq 14
[17179572.336000] ata1: dev 0 cfg 00:0040 49:2f00 82:746b 83:7d09 84:6063 85:7469 86:3d09 87:6063 88:203f 93:0000
[17179572.336000] ata1: dev 0 ATA-7, max UDMA/100, 234441648 sectors: LBA48
[17179572.336000] ata_acpi_push_id: skipping for PATA mode
[17179572.336000] ata1: dev 0 configured for UDMA/100
[17179572.336000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179572.336000] pata_get_dev_handle: dev_handle: 0xdffe3aa0, parent_handle: 0xdffeabe0
[17179572.336000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff5ba00, *handle=0xdffe3aa0
[17179572.336000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe2d40
[17179572.336000] scsi0 : ata_piix
[17179572.336000]   Vendor: ATA       Model: TOSHIBA MK1234GS  Rev: AH00
[17179572.336000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179572.336000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179572.336000] pata_get_dev_handle: dev_handle: 0xdffe3aa0, parent_handle: 0xdffeabe0
[17179572.336000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff5ba00, *handle=0xdffe3aa0
[17179572.340000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18B8 irq 15
[17179572.668000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:4000
[17179572.668000] ata2: dev 0 ATAPI, max UDMA/33
[17179572.668000] ata2(0): applying bridge limits
[17179572.668000] ata_acpi_push_id: skipping for PATA mode
[17179572.668000] ata2: dev 0 configured for UDMA/33
[17179572.668000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179572.668000] pata_get_dev_handle: dev_handle: 0xdffe3aa0, parent_handle: 0xdffeabe0
[17179572.668000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff5ba00, *handle=0xdffe3aa0
[17179572.668000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe2c00
[17179572.668000] scsi1 : ata_piix
[17179572.668000]   Vendor: MATSHITA  Model: DVD-RAM UJ-841S   Rev: 1.50
[17179572.672000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179572.672000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179572.672000] pata_get_dev_handle: dev_handle: 0xdffe3aa0, parent_handle: 0xdffeabe0
[17179572.672000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff5ba00, *handle=0xdffe3aa0
[17179572.676000] Driver 'sd' needs updating - please use bus_type methods
[17179572.676000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[17179572.676000] SCSI device sda: drive cache: write back
[17179572.680000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[17179572.680000] SCSI device sda: drive cache: write back
[17179572.680000]  sda: sda1 sda2 sda3 < sda5 > sda4
[17179572.736000] sd 0:0:0:0: Attached scsi disk sda
[17179572.980000] usbcore: registered new driver usbfs
[17179572.980000] usbcore: registered new driver hub
[17179572.980000] USB Universal Host Controller Interface driver v2.3
[17179572.984000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179572.984000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179572.984000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179572.984000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179572.984000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x00001800
[17179572.984000] hub 1-0:1.0: USB hub found
[17179572.984000] hub 1-0:1.0: 2 ports detected
[17179573.028000] ieee1394: Initialized config rom entry `ip1394'
[17179573.088000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 233
[17179573.088000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179573.088000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179573.088000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179573.088000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x00001820
[17179573.092000] hub 2-0:1.0: USB hub found
[17179573.092000] hub 2-0:1.0: 2 ports detected
[17179573.200000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179573.200000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179573.200000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179573.200000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179573.200000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001840
[17179573.200000] hub 3-0:1.0: USB hub found
[17179573.200000] hub 3-0:1.0: 2 ports detected
[17179573.304000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179573.304000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179573.304000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179573.304000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179573.304000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00001860
[17179573.304000] hub 4-0:1.0: USB hub found
[17179573.304000] hub 4-0:1.0: 2 ports detected
[17179573.408000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179573.408000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179573.408000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179573.408000] ehci_hcd 0000:00:1d.7: debug port 1
[17179573.408000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179573.408000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179573.408000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0xde304000
[17179573.412000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179573.412000] hub 5-0:1.0: USB hub found
[17179573.412000] hub 5-0:1.0: 8 ports detected
[17179573.516000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179573.516000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.568000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[de006000-de0067ff]  Max Packet=[2048]
[17179573.580000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179573.580000] ide0: ports already in use, skipping probe
[17179573.580000] ide1: I/O resource 0x170-0x177 not free.
[17179573.580000] ide1: ports already in use, skipping probe
[17179573.600000] Attempting manual resume
[17179573.636000] EXT3-fs: mounted filesystem with ordered data mode.
[17179573.636000] kjournald starting.  Commit interval 5 seconds
[17179574.840000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1421bfc]
[17179580.156000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179580.156000] Uniform CD-ROM driver Revision: 3.20
[17179580.156000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179580.236000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179580.236000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179580.328000] Linux agpgart interface v0.101 (c) Dave Jones
[17179580.388000] agpgart: Detected an Intel 945GM Chipset.
[17179580.404000] agpgart: AGP aperture is 256M @ 0x0
[17179580.424000] hw_random: RNG not detected
[17179580.440000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179580.448000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179580.868000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179580.868000] sdhci: Copyright(c) Pierre Ossman
[17179580.868000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 185
[17179580.920000] sdhci: ============== REGISTER DUMP ==============
[17179580.920000] sdhci: Sys addr: 0x00000000 | Version:  0x00008900
[17179580.920000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179580.920000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179580.920000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179580.920000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179580.920000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179580.920000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179580.920000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179580.920000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179580.920000] sdhci: Caps:     0x01c030b0 | Max curr: 0x00000000
[17179580.920000] sdhci: ===========================================
[17179580.968000] mmc0: SDHCI at 0xde006800 irq 185 DMA
[17179581.060000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179581.060000] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[17179581.060000] Yenta: Enabling burst memory read transactions
[17179581.060000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179581.060000] Yenta: Routing CardBus interrupts to PCI
[17179581.060000] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[17179581.196000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2a0b1, caps: 0xb04713/0x60040d
[17179581.196000] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[17179581.228000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179581.296000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 185
[17179581.296000] Socket status: 30000006
[17179581.296000] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[17179581.296000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[17179581.296000] pcmcia: parent PCI bridge Memory window: 0xde000000 - 0xde0fffff
[17179581.296000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179581.888000] nvidia: module license 'NVIDIA' taints kernel.
[17179581.892000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179581.892000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179581.892000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179582.020000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179582.020000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179582.020000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179582.020000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179582.020000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179582.076000] ipw3945: ipw3945.ucode load failed: Reason -2
[17179582.076000] ipw3945: Could not read microcode: -2
[17179582.076000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[17179582.076000] ipw3945: probe of 0000:05:00.0 failed with error -2
[17179582.100000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179582.100000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179582.100000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179582.144000] e100: eth0: e100_probe: addr 0xde005000, irq 58, MAC addr 00:A0:D1:42:1B:FC
[17179582.160000] ts: Compaq touchscreen protocol output
[17179582.336000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 66
[17179582.336000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179582.680000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179582.700000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179583.460000] lp: driver loaded but no devices found
[17179583.500000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179583.500000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179583.500000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179583.548000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[17179583.588000] EXT3 FS on sda2, internal journal
[17179583.744000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179583.744000] md: bitmap version 4.39
[17179583.764000] NET: Registered protocol family 17
[17179584.072000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179584.632000] cdrom: open failed.
[17179586.848000] NET: Registered protocol family 10
[17179586.848000] lo: Disabled Privacy Extensions
[17179586.848000] IPv6 over IPv4 tunneling driver
[17179588.880000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[17179589.008000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'KeQueryTickCount'
[17179589.008000] ndiswrapper (import:239): unknown symbol: NDIS.SYS:'NdisIMCopySendPerPacketInfo'
[17179589.008000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'w39n51'
[17179589.008000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[17179595.148000] ppdev: user-space parallel port driver
[17179596.968000] eth0: no IPv6 routers present
[17179597.620000] Bluetooth: Core ver 2.8
[17179597.620000] NET: Registered protocol family 31
[17179597.620000] Bluetooth: HCI device and connection manager initialized
[17179597.620000] Bluetooth: HCI socket layer initialized
[17179597.656000] Bluetooth: L2CAP ver 2.8
[17179597.656000] Bluetooth: L2CAP socket layer initialized
[17179597.660000] Bluetooth: RFCOMM socket layer initialized
[17179597.660000] Bluetooth: RFCOMM TTY layer initialized
[17179597.660000] Bluetooth: RFCOMM ver 1.7

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

can anyone help me out with this?

---

