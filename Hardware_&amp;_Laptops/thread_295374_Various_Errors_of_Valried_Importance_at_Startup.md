---
title: "Various Errors of Valried Importance at Startup"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by jrattner on 2006-11-08
When I start my laptop, I receive several errors during the boot process which are apparent in DMESG.  For example: 
[17179573.172000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179573.172000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179573.172000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0

This is an interesting one and my main concern.

Below is the rest of my dmesg output:

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000007fef0000 - 000000007fef9000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007fef9000 - 000000007ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 1150MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7a70
[17179569.184000] On node 0 totalpages: 524016
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294640 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f79c0
[17179569.184000] ACPI: RSDT (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x7fef1a59
[17179569.184000] ACPI: FADT (v001 HP     3082     0x06040000 PTL  0x00000003) @ 0x7fef8ec0
[17179569.184000] ACPI: MCFG (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x7fef8f34
[17179569.184000] ACPI: MADT (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x7fef8f70
[17179569.184000] ACPI: BOOT (v001     HP 3082     0x06040000  LTP 0x00000001) @ 0x7fef8fd8
[17179569.184000] ACPI: DSDT (v001 HP     3082     0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 3192.788 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.096000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.096000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.164000] Memory: 2068476k/2096064k available (1910k kernel code, 26232k reserved, 1070k data, 308k init, 1178560k highmem)
[17179572.164000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.244000] Calibrating delay using timer specific routine.. 6392.20 BogoMIPS (lpj=12784400)
[17179572.244000] Security Framework v1.0.0 initialized
[17179572.244000] SELinux:  Disabled at boot.
[17179572.244000] Mount-cache hash table entries: 512
[17179572.244000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.244000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.244000] monitor/mwait feature present.
[17179572.244000] using mwait in idle threads.
[17179572.244000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.244000] CPU: L2 cache: 2048K
[17179572.244000] CPU: Hyper-Threading is disabled
[17179572.244000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179572.244000] Checking 'hlt' instruction... OK.
[17179572.260000] SMP alternatives: switching to UP code
[17179572.260000] checking if image is initramfs... it is
[17179572.648000] Freeing initrd memory: 5212k freed
[17179572.648000] ACPI: Core revision 20060707
[17179572.680000] ACPI: Looking for DSDT ... not found!
[17179572.696000] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[17179572.696000] SMP alternatives: switching to SMP code
[17179572.696000] Booting processor 1/1 eip 3000
[17179572.708000] Initializing CPU#1
[17179572.788000] Calibrating delay using timer specific routine.. 6384.68 BogoMIPS (lpj=12769365)
[17179572.788000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.788000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.788000] monitor/mwait feature present.
[17179572.788000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.788000] CPU: L2 cache: 2048K
[17179572.788000] CPU: Hyper-Threading is disabled
[17179572.788000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179572.788000] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[17179572.788000] Total of 2 processors activated (12776.88 BogoMIPS).
[17179572.788000] ENABLING IO-APIC IRQs
[17179572.788000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.932000] checking TSC synchronization across 2 CPUs: passed.
[17179572.936000] Brought up 2 CPUs
[17179573.088000] migration_cost=4000
[17179573.088000] NET: Registered protocol family 16
[17179573.088000] EISA bus registered
[17179573.088000] ACPI: bus type pci registered
[17179573.088000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179573.088000] PCI: Not using MMCONFIG.
[17179573.124000] PCI: PCI BIOS revision 2.10 entry at 0xfd95e, last bus=11
[17179573.124000] PCI: Using configuration type 1
[17179573.124000] Setting up standard PCI resources
[17179573.152000] ACPI: Interpreter enabled
[17179573.152000] ACPI: Using IOAPIC for interrupt routing
[17179573.152000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.152000] PCI: Probing PCI hardware (bus 00)
[17179573.156000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179573.156000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179573.156000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.156000] Boot video device is 0000:01:00.0
[17179573.156000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.156000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[17179573.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[17179573.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.164000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5
[17179573.164000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7
[17179573.164000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7
[17179573.164000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[17179573.164000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7
[17179573.168000] ACPI: Embedded Controller [EC0] (gpe 29) interrupt mode.
[17179573.172000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.172000] pnp: PnP ACPI init
[17179573.172000] pnp: PnP ACPI: found 9 devices
[17179573.172000] PnPBIOS: Disabled by ACPI PNP
[17179573.172000] PCI: Using ACPI for IRQ routing
[17179573.172000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.172000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179573.172000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179573.172000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179573.192000] PCI: Bridge: 0000:00:01.0
[17179573.192000]   IO window: 4000-4fff
[17179573.192000]   MEM window: b0100000-b01fffff
[17179573.192000]   PREFETCH window: c0000000-cfffffff
[17179573.192000] PCI: Bridge: 0000:00:1c.0
[17179573.192000]   IO window: disabled.
[17179573.192000]   MEM window: disabled.
[17179573.192000]   PREFETCH window: disabled.
[17179573.192000] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[17179573.192000]   IO window: 00005400-000054ff
[17179573.192000]   IO window: 00005800-000058ff
[17179573.192000]   PREFETCH window: 88000000-89ffffff
[17179573.192000]   MEM window: 8a000000-8bffffff
[17179573.192000] PCI: Bridge: 0000:00:1e.0
[17179573.192000]   IO window: 5000-5fff
[17179573.192000]   MEM window: b0200000-b02fffff
[17179573.192000]   PREFETCH window: 88000000-89ffffff
[17179573.192000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.192000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.192000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179573.192000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.192000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.192000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.192000] NET: Registered protocol family 2
[17179573.236000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.236000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179573.236000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.236000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.236000] TCP reno registered
[17179573.236000] Simple Boot Flag at 0x36 set to 0x1
[17179573.236000] audit: initializing netlink socket (disabled)
[17179573.236000] audit(1162942851.236:1): initialized
[17179573.236000] highmem bounce pool size: 64 pages
[17179573.236000] VFS: Disk quotas dquot_6.5.1
[17179573.236000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.236000] Initializing Cryptographic API
[17179573.236000] io scheduler noop registered
[17179573.236000] io scheduler anticipatory registered
[17179573.236000] io scheduler deadline registered
[17179573.236000] io scheduler cfq registered (default)
[17179573.236000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.236000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:01.0:pcie00]
[17179573.236000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179573.236000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.236000] assign_interrupt_mode Found MSI capability
[17179573.236000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179573.236000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179573.236000] isapnp: Scanning for PnP cards...
[17179573.588000] isapnp: No Plug & Play device found
[17179573.612000] Real Time Clock Driver v1.12ac
[17179573.612000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.612000] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 209
[17179573.612000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.612000] mice: PS/2 mouse device common for all mice
[17179573.612000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.612000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.612000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.616000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179573.616000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.616000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.616000] EISA: Probing bus 0 at eisa.0
[17179573.616000] Cannot allocate resource for EISA slot 1
[17179573.616000] Cannot allocate resource for EISA slot 3
[17179573.616000] Cannot allocate resource for EISA slot 4
[17179573.616000] Cannot allocate resource for EISA slot 5
[17179573.616000] EISA: Detected 0 cards.
[17179573.616000] TCP bic registered
[17179573.616000] NET: Registered protocol family 1
[17179573.616000] NET: Registered protocol family 8
[17179573.616000] NET: Registered protocol family 20
[17179573.616000] Starting balanced_irq
[17179573.616000] Using IPI No-Shortcut mode
[17179573.616000] ACPI: (supports S0 S3 S4 S5)
[17179573.616000] Freeing unused kernel memory: 308k freed
[17179573.652000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.680000] Capability LSM initialized
[17179574.712000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.712000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.716000] ACPI: Thermal Zone [THRM] (65 C)
[17179575.068000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.068000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 217
[17179575.068000] ICH6: chipset revision 3
[17179575.068000] ICH6: not 100% native mode: will probe irqs later
[17179575.068000]     ide0: BM-DMA at 0x3c40-0x3c47, BIOS settings: hda:DMA, hdb:DMA
[17179575.068000] Probing IDE interface ide0...
[17179575.356000] hda: ST9808211A, ATA DISK drive
[17179576.140000] hdb: HL-DT-ST DVD-RW GCA-4080N, ATAPI CD/DVD-ROM drive
[17179576.196000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.204000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[17179576.204000] Uniform CD-ROM driver Revision: 3.20
[17179576.212000] hda: max request size: 512KiB
[17179576.212000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.212000] hda: cache flushes supported
[17179576.212000]  hda: hda1 hda2 hda3 < hda5 > hda4
[17179576.652000] Probing IDE interface ide1...
[17179576.696000] usbcore: registered new driver usbfs
[17179576.696000] usbcore: registered new driver hub
[17179576.696000] USB Universal Host Controller Interface driver v3.0
[17179576.696000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 225
[17179576.696000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.696000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.696000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.696000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00001800
[17179576.696000] usb usb1: configuration #1 chosen from 1 choice
[17179576.696000] hub 1-0:1.0: USB hub found
[17179576.696000] hub 1-0:1.0: 2 ports detected
[17179576.732000] ieee1394: Initialized config rom entry `ip1394'
[17179576.800000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 233
[17179576.800000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.800000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.800000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.800000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x000038c0
[17179576.800000] usb usb2: configuration #1 chosen from 1 choice
[17179576.800000] hub 2-0:1.0: USB hub found
[17179576.800000] hub 2-0:1.0: 2 ports detected
[17179576.904000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179576.904000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.904000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.904000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.904000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x000038e0
[17179576.904000] usb usb3: configuration #1 chosen from 1 choice
[17179576.904000] hub 3-0:1.0: USB hub found
[17179576.904000] hub 3-0:1.0: 2 ports detected
[17179577.008000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.008000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.008000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.008000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.008000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00003c00
[17179577.008000] usb usb4: configuration #1 chosen from 1 choice
[17179577.008000] hub 4-0:1.0: USB hub found
[17179577.008000] hub 4-0:1.0: 2 ports detected
[17179577.112000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 225
[17179577.112000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.112000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.112000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.112000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.112000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.112000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xb0000000
[17179577.116000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.116000] usb usb5: configuration #1 chosen from 1 choice
[17179577.116000] hub 5-0:1.0: USB hub found
[17179577.116000] hub 5-0:1.0: 8 ports detected
[17179577.144000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179577.220000] ACPI: PCI Interrupt 0000:0b:00.2[C] -> GSI 22 (level, low) -> IRQ 209
[17179577.268000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179577.328000] Attempting manual resume
[17179577.360000] kjournald starting.  Commit interval 5 seconds
[17179577.360000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.944000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17179578.144000] usb 2-1: configuration #1 chosen from 1 choice
[17179578.388000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179578.540000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800285600097f8a]
[17179578.564000] usb 4-1: configuration #1 chosen from 1 choice
[17179588.756000] hw_random: RNG not detected
[17179588.772000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.772000] agpgart: Detected an Intel 915G Chipset.
[17179588.792000] agpgart: AGP aperture is 256M @ 0x0
[17179588.872000] input: PC Speaker as /class/input/input1
[17179588.896000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.900000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.404000] usbcore: registered new driver hiddev
[17179589.420000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179589.420000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-1
[17179589.420000] usbcore: registered new driver usbhid
[17179589.420000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.436000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.436000] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[17179589.436000] Yenta: Enabling burst memory read transactions
[17179589.436000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.436000] Yenta: Routing CardBus interrupts to PCI
[17179589.436000] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[17179589.476000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179589.476000] sdhci: Copyright(c) Pierre Ossman
[17179589.524000] 8139too Fast Ethernet driver 0.9.27
[17179589.540000] ieee80211_crypt: registered algorithm 'NULL'
[17179589.568000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3D11
[17179589.568000] usbcore: registered new driver usblp
[17179589.568000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179589.584000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[17179589.612000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179589.612000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179589.620000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179589.672000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[17179589.672000] Socket status: 30000006
[17179589.672000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[17179589.672000] cs: IO port probe 0x5000-0x5fff: clean.
[17179589.672000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[17179589.672000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x89ffffff
[17179589.672000] sdhci: SDHCI controller found at 0000:0b:00.4 [104c:8034] (rev 0)
[17179589.672000] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[17179589.672000] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.672000] mmc0: SDHCI at 0xb0209000 irq 169 DMA
[17179589.672000] mmc1: SDHCI at 0xb0208c00 irq 169 DMA
[17179589.672000] mmc2: SDHCI at 0xb0208800 irq 169 DMA
[17179589.672000] PCI: Enabling device 0000:0b:00.3 (0000 -> 0002)
[17179589.672000] ACPI: PCI Interrupt 0000:0b:00.3[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.672000] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 20 (level, low) -> IRQ 50
[17179589.672000] eth0: RealTek RTL8139 at 0xf8ac0400, 00:c0:9f:a9:1b:7f, IRQ 50
[17179589.672000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179589.676000] ts: Compaq touchscreen protocol output
[17179589.760000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179589.784000] bcm43xx driver
[17179589.784000] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[17179589.784000] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179589.976000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179590.044000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179590.084000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179590.116000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 209
[17179590.116000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179590.220000] cs: IO port probe 0x100-0x3af: clean.
[17179590.220000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179590.220000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.220000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.220000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.432000] intel8x0_measure_ac97_clock: measured 58131 usecs
[17179590.432000] intel8x0: clocking to 48000
[17179590.608000] lp: driver loaded but no devices found
[17179590.660000] SCSI subsystem initialized
[17179590.668000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.668000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.692000] Adding 1871532k swap on /dev/disk/by-uuid/4b9f3ec7-85f6-4f1c-8374-dd8f3bb48acb.  Priority:-1 extents:1 across:1871532k
[17179590.824000] EXT3 FS on hda2, internal journal
[17179591.048000] NET: Registered protocol family 17
[17179591.076000] kjournald starting.  Commit interval 5 seconds
[17179591.084000] EXT3 FS on hda4, internal journal
[17179591.084000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.136000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179591.188000] NTFS volume version 3.1.
[17179591.420000] NET: Registered protocol family 10
[17179591.420000] lo: Disabled Privacy Extensions
[17179591.420000] IPv6 over IPv4 tunneling driver
[17179593.736000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179593.760000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179593.760000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179593.796000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179593.800000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179593.800000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179593.824000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179593.824000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179593.824000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179593.864000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179593.864000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179593.864000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179596.088000] ACPI: AC Adapter [ACAD] (on-line)
[17179596.376000] ACPI: Battery Slot [BAT1] (battery absent)
[17179596.396000] ACPI: Power Button (FF) [PWRF]
[17179596.396000] ACPI: Lid Switch [LID0]
[17179596.396000] ACPI: Power Button (CM) [PWRB]
[17179596.396000] ACPI: Sleep Button (CM) [SLPB]
[17179596.520000] ibm_acpi: ec object not found
[17179596.564000] pcc_acpi: loading...
[17179596.616000] wmi_add device=dff5c400
[17179596.616000] calling WQBA
[17179596.676000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.424000] [drm] Initialized drm 1.0.1 20051102
[17179599.436000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179599.436000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179600.124000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179600.124000] apm: disabled - APM is not SMP safe.
[17179600.732000] [drm] Setting GART location based on new memory map
[17179600.732000] [drm] Loading R300 Microcode
[17179600.732000] [drm] writeback test succeeded in 1 usecs
[17179601.492000] eth0: no IPv6 routers present
[17179604.848000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179605.744000] /dev/vmmon[4678]: Module vmmon: registered with major=10 minor=165
[17179605.744000] /dev/vmmon[4678]: Module vmmon: initialized
[17179605.852000] /dev/vmnet: open called by PID 4704 (vmnet-bridge)
[17179605.852000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179605.856000] /dev/vmnet: port on hub 0 successfully opened
[17179605.856000] bridge-eth0: enabling the bridge
[17179605.856000] bridge-eth0: up
[17179605.856000] bridge-eth0: already up
[17179605.856000] bridge-eth0: attached
[17179605.904000] /dev/vmnet: open called by PID 4710 (vmnet-netifup)
[17179605.904000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179605.904000] /dev/vmnet: port on hub 1 successfully opened
[17179605.904000] /dev/vmnet: open called by PID 4718 (vmnet-netifup)
[17179605.904000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179605.904000] /dev/vmnet: port on hub 8 successfully opened
[17179605.932000] /dev/vmnet: open called by PID 4720 (vmnet-natd)
[17179605.932000] /dev/vmnet: port on hub 8 successfully opened
[17179607.228000] Bluetooth: Core ver 2.8
[17179607.228000] NET: Registered protocol family 31
[17179607.228000] Bluetooth: HCI device and connection manager initialized
[17179607.228000] Bluetooth: HCI socket layer initialized
[17179607.228000] /dev/vmnet: open called by PID 4742 (vmnet-dhcpd)
[17179607.228000] /dev/vmnet: port on hub 1 successfully opened
[17179607.228000] /dev/vmnet: open called by PID 4746 (vmnet-dhcpd)
[17179607.228000] /dev/vmnet: port on hub 8 successfully opened
[17179607.352000] Bluetooth: L2CAP ver 2.8
[17179607.352000] Bluetooth: L2CAP socket layer initialized
[17179607.388000] Bluetooth: RFCOMM socket layer initialized
[17179607.388000] Bluetooth: RFCOMM TTY layer initialized
[17179607.388000] Bluetooth: RFCOMM ver 1.7
[17179608.476000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179615.964000] vmnet1: no IPv6 routers present
[17179616.820000] vmnet8: no IPv6 routers present
[17179625.400000] eth0: no IPv6 routers present
[17179635.480000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179659.116000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179683.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179707.160000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179731.984000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179855.200000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179978.416000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180102.584000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180225.800000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180350.380000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180473.596000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180596.856000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180720.076000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180843.288000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by j3cakes on 2006-12-05
I keep getting the same error, did you ever find a solution to this?

---

