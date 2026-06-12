---
title: "Dell XPS locking up"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by init6 on 2006-06-06
I had the same trouble with 5.04 and 5.10.  I was hoping I'd actually get to use 6.06.  I can boot to the gnome desktop about 50-75% of the time without locking up.  Once I'm there I can usually get a shell open for like 3 minutes before crash.  If I try to start anything else up like web browser, package manager, etc, it's automatic crash.  I started another thread a couple days ago but the guy helping me just vanished into the sunset.  This time I was able to retrieve more info.  Please see the following and thanks in advance:

Dell XPS
3.4 GHz Processor.  1 GB RAM.  ATI 9800 video.

LSPCI:

0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M18 JN [Radeon Mobility 9800]
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

DMESG:

[4294667.296000] Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003ffaa800 (usable)
[4294667.296000]  BIOS-e820: 000000003ffaa800 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[4294667.296000]  BIOS-e820: 00000000feda0000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 262058
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32682 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde90
[4294667.296000] ACPI: RSDT (v001 DELL    CPi R   0x27d40b01 ASL  0x00000061) @ 0x3ffefbcd
[4294667.296000] ACPI: FADT (v001 DELL    CPi R   0x27d40b01 ASL  0x00000061) @ 0x3fff0400
[4294667.296000] ACPI: MADT (v001 DELL    CPi R   0x27d40b01 ASL  0x00000047) @ 0x3fff0c00
[4294667.296000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x3ffefbfd
[4294667.296000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:3 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 15:3 APIC version 20
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda6 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 3392.399 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.147000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.148000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.170000] Memory: 1026940k/1048232k available (2101k kernel code, 20588k reserved, 592k data, 332k init, 130728k highmem)
[4294670.170000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.230000] Calibrating delay using timer specific routine.. 6787.16 BogoMIPS (lpj=3393583)
[4294670.230000] Security Framework v1.0.0 initialized
[4294670.230000] SELinux:  Disabled at boot.
[4294670.230000] Mount-cache hash table entries: 512
[4294670.230000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294670.230000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294670.230000] monitor/mwait feature present.
[4294670.230000] using mwait in idle threads.
[4294670.230000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294670.230000] CPU: L2 cache: 1024K
[4294670.230000] CPU: Hyper-Threading is disabled
[4294670.230000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[4294670.230000] mtrr: v2.0 (20020519)
[4294670.230000] Enabling fast FPU save and restore... done.
[4294670.230000] Enabling unmasked SIMD FPU exception support... done.
[4294670.230000] Checking 'hlt' instruction... OK.
[4294670.234000] SMP alternatives: switching to UP code
[4294670.234000] checking if image is initramfs... it is
[4294670.669000] Freeing initrd memory: 6798k freed
[4294670.680000] ACPI: Looking for DSDT ... not found!
[4294670.682000] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[4294670.682000] SMP alternatives: switching to SMP code
[4294670.683000] Booting processor 1/1 eip 3000
[4294670.693000] Initializing CPU#1
[4294670.754000] Calibrating delay using timer specific routine.. 6782.06 BogoMIPS (lpj=3391032)
[4294670.754000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294670.754000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294670.754000] monitor/mwait feature present.
[4294670.754000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294670.754000] CPU: L2 cache: 1024K
[4294670.754000] CPU: Hyper-Threading is disabled
[4294670.754000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[4294670.754000] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[4294670.754000] Total of 2 processors activated (13569.23 BogoMIPS).
[4294670.754000] ENABLING IO-APIC IRQs
[4294670.754000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.865000] checking TSC synchronization across 2 CPUs: 
[4294670.865000] CPU#0 had 0 usecs TSC skew, fixed it up.
[4294670.865000] CPU#1 had 0 usecs TSC skew, fixed it up.
[4294670.866000] Brought up 2 CPUs
[4294670.866000] NET: Registered protocol family 16
[4294670.866000] EISA bus registered
[4294670.866000] ACPI: bus type pci registered
[4294670.882000] PCI: PCI BIOS revision 2.10 entry at 0xfcc7e, last bus=2
[4294670.882000] PCI: Using configuration type 1
[4294670.883000] ACPI: Subsystem revision 20051216
[4294670.893000] ACPI: Interpreter enabled
[4294670.893000] ACPI: Using IOAPIC for interrupt routing
[4294670.894000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.894000] PCI: Probing PCI hardware (bus 00)
[4294670.894000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.902000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294670.902000] PCI quirk: region 1080-10bf claimed by ICH4 GPIO
[4294670.902000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.902000] Boot video device is 0000:01:00.0
[4294670.902000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.902000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.911000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[4294670.911000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[4294670.911000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[4294670.911000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[4294670.912000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.912000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.913000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294670.914000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[4294670.914000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.914000] pnp: PnP ACPI init
[4294670.923000] pnp: PnP ACPI: found 10 devices
[4294670.923000] PnPBIOS: Disabled by ACPI PNP
[4294670.923000] PCI: Using ACPI for IRQ routing
[4294670.923000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.936000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294670.936000] pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
[4294670.936000] pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
[4294670.936000] pnp: 00:01: ioport range 0x800-0x80f has been reserved
[4294670.936000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[4294670.936000] pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
[4294670.936000] pnp: 00:02: ioport range 0x1010-0x105f could not be reserved
[4294670.936000] pnp: 00:02: ioport range 0x1060-0x107f has been reserved
[4294670.936000] pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
[4294670.936000] pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
[4294670.936000] pnp: 00:07: ioport range 0x900-0x97f has been reserved
[4294670.937000] PCI: Bridge: 0000:00:01.0
[4294670.937000]   IO window: c000-cfff
[4294670.937000]   MEM window: fc000000-fdffffff
[4294670.937000]   PREFETCH window: e0000000-efffffff
[4294670.937000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[4294670.937000]   IO window: 0000e000-0000e0ff
[4294670.937000]   IO window: 0000e400-0000e4ff
[4294670.937000]   PREFETCH window: 50000000-51ffffff
[4294670.937000]   MEM window: 54000000-55ffffff
[4294670.937000] PCI: Bridge: 0000:00:1e.0
[4294670.937000]   IO window: e000-efff
[4294670.937000]   MEM window: fa000000-fbffffff
[4294670.937000]   PREFETCH window: 50000000-52ffffff
[4294670.937000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.937000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[4294670.937000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 169
[4294670.937000] audit: initializing netlink socket (disabled)
[4294670.937000] audit(1149624998.935:1): initialized
[4294670.937000] highmem bounce pool size: 64 pages
[4294670.938000] VFS: Disk quotas dquot_6.5.1
[4294670.938000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.938000] Initializing Cryptographic API
[4294670.938000] io scheduler noop registered
[4294670.938000] io scheduler anticipatory registered
[4294670.938000] io scheduler deadline registered
[4294670.938000] io scheduler cfq registered
[4294670.938000] isapnp: Scanning for PnP cards...
[4294671.292000] isapnp: No Plug & Play device found
[4294671.311000] Real Time Clock Driver v1.12
[4294671.311000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.314000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.315000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.315000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.317000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 177
[4294671.317000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294671.317000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.318000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.318000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.318000] mice: PS/2 mouse device common for all mice
[4294671.318000] EISA: Probing bus 0 at eisa.0
[4294671.318000] Cannot allocate resource for EISA slot 1
[4294671.318000] EISA: Detected 0 cards.
[4294671.318000] NET: Registered protocol family 2
[4294671.327000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.329000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.329000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[4294671.331000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[4294671.331000] TCP: Hash tables configured (established 262144 bind 65536)
[4294671.331000] TCP reno registered
[4294671.331000] TCP bic registered
[4294671.331000] NET: Registered protocol family 1
[4294671.331000] NET: Registered protocol family 8
[4294671.331000] NET: Registered protocol family 20
[4294671.331000] Starting balanced_irq
[4294671.331000] Using IPI No-Shortcut mode
[4294671.331000] ACPI wakeup devices: 
[4294671.331000]  LID PBTN PCI0 USB1 USB2 USB4 USB3 MODM PCIE 
[4294671.331000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.331000] Freeing unused kernel memory: 332k freed
[4294671.376000] vga16fb: initializing
[4294671.376000] vga16fb: mapped to 0xc00a0000
[4294671.482000] Console: switching to colour frame buffer device 80x25
[4294671.482000] fb0: VGA16 VGA frame buffer device
[4294672.507000] Capability LSM initialized
[4294672.585000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294672.585000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294672.590000] ACPI: Thermal Zone [THM] (72 C)
[4294673.127000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294673.127000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294673.127000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 185
[4294673.127000] ICH5: chipset revision 2
[4294673.127000] ICH5: not 100% native mode: will probe irqs later
[4294673.127000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[4294673.127000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294673.127000] Probing IDE interface ide0...
[4294673.392000] hda: FUJITSU MHU2100AT, ATA DISK drive
[4294674.116000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.153000] Probing IDE interface ide1...
[4294674.825000] hdc: _NEC DVD+/-RW ND-6500A, ATAPI CD/DVD-ROM drive
[4294675.437000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.446000] hda: max request size: 128KiB
[4294675.447000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.449000] hda: cache flushes supported
[4294675.449000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 hda8 hda9 hda10 >
[4294675.623000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.623000] Uniform CD-ROM driver Revision: 3.20
[4294682.952000] hdc: irq timeout: status=0xd0 { Busy }
[4294682.952000] ide: failed opcode was: unknown
[4294682.952000] hdc: DMA disabled
[4294683.102000] hdc: ATAPI reset complete
[4294700.650000] usbcore: registered new driver usbfs
[4294700.651000] usbcore: registered new driver hub
[4294700.652000] USB Universal Host Controller Interface driver v2.3
[4294700.652000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294700.652000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294700.652000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294700.652000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294700.652000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000bf80
[4294700.652000] hub 1-0:1.0: USB hub found
[4294700.652000] hub 1-0:1.0: 2 ports detected
[4294700.690000] ieee1394: Initialized config rom entry `ip1394'
[4294700.753000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 169
[4294700.753000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294700.753000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294700.753000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294700.753000] uhci_hcd 0000:00:1d.1: irq 169, io base 0x0000bf60
[4294700.753000] hub 2-0:1.0: USB hub found
[4294700.753000] hub 2-0:1.0: 2 ports detected
[4294700.854000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
[4294700.854000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294700.854000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294700.854000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294700.854000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000bf40
[4294700.854000] hub 3-0:1.0: USB hub found
[4294700.854000] hub 3-0:1.0: 2 ports detected
[4294700.955000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 185
[4294700.955000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294700.955000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294700.955000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294700.955000] uhci_hcd 0000:00:1d.3: irq 185, io base 0x0000bf20
[4294700.955000] hub 4-0:1.0: USB hub found
[4294700.955000] hub 4-0:1.0: 2 ports detected
[4294701.056000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[4294701.056000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294701.056000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294701.056000] ehci_hcd 0000:00:1d.7: debug port 1
[4294701.056000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294701.056000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294701.056000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xf8fffc00
[4294701.060000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294701.060000] hub 5-0:1.0: USB hub found
[4294701.060000] hub 5-0:1.0: 8 ports detected
[4294701.162000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294701.162000] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 19 (level, low) -> IRQ 169
[4294701.212000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[169]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]
[4294701.652000] Attempting manual resume
[4294701.661000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294701.661000] EXT3-fs: write access will be enabled during recovery.
[4294701.699000] EXT3-fs: recovery complete.
[4294701.699000] kjournald starting.  Commit interval 5 seconds
[4294701.699000] EXT3-fs: mounted filesystem with ordered data mode.
[4294702.468000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc000149e0cc1]
[4294707.640000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294707.645000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294707.915000] hw_random: cannot enable RNG, aborting
[4294707.930000] Linux agpgart interface v0.101 (c) Dave Jones
[4294707.938000] agpgart: Detected an Intel 865 Chipset.
[4294707.945000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294708.002000] input: PC Speaker as /class/input/input1
[4294708.158000] tg3.c:v3.47 (Dec 28, 2005)
[4294708.158000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 193
[4294708.454000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 177
[4294708.454000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294708.455000] ieee80211_crypt: registered algorithm 'NULL'
[4294708.458000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294708.458000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294708.500000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0f:1f:23:ba:6a
[4294708.500000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[4294708.500000] eth0: dma_rwctrl[763f0000]
[4294708.548000] bcm43xx driver
[4294708.579000] input: PS/2 Mouse as /class/input/input2
[4294708.604000] ts: Compaq touchscreen protocol output
[4294708.605000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[4294709.592000] intel8x0_measure_ac97_clock: measured 51444 usecs
[4294709.592000] intel8x0: clocking to 48000
[4294709.594000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 169
[4294709.594000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:017c]
[4294709.594000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294709.594000] Yenta: Routing CardBus interrupts to PCI
[4294709.594000] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64
[4294709.818000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[4294709.818000] Socket status: 30000086
[4294709.818000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[4294709.818000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[4294709.818000] cs: IO port probe 0xe000-0xefff: clean.
[4294709.818000] pcmcia: parent PCI bridge Memory window: 0xfa000000 - 0xfbffffff
[4294709.818000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x52ffffff
[4294709.818000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294710.057000] NET: Registered protocol family 17
[4294710.137000] cs: IO port probe 0x100-0x3af: clean.
[4294710.138000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294710.138000] cs: IO port probe 0x820-0x8ff: clean.
[4294710.139000] cs: IO port probe 0xc00-0xcf7: clean.
[4294710.139000] cs: IO port probe 0xa00-0xaff: clean.
[4294710.282000] lp: driver loaded but no devices found
[4294710.352000] SCSI subsystem initialized
[4294710.362000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294710.362000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294710.362000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294710.452000] Adding 1959920k swap on /dev/hda3.  Priority:-1 extents:1 across:1959920k
[4294710.491000] EXT3 FS on hda6, internal journal
[4294710.698000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294710.698000] md: bitmap version 4.39
[4294711.031000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4294711.031000] tg3: eth0: Flow control is on for TX and on for RX.
[4294711.237000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294714.782000] kjournald starting.  Commit interval 5 seconds
[4294714.783000] EXT3 FS on hda10, internal journal
[4294714.783000] EXT3-fs: mounted filesystem with ordered data mode.
[4294714.807000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294714.876000] NTFS volume version 3.1.
[4294714.928000] NTFS volume version 3.1.
[4294714.956000] kjournald starting.  Commit interval 5 seconds
[4294714.957000] EXT3 FS on hda9, internal journal
[4294714.957000] EXT3-fs: mounted filesystem with ordered data mode.
[4294714.987000] kjournald starting.  Commit interval 5 seconds
[4294714.987000] EXT3 FS on hda7, internal journal
[4294714.987000] EXT3-fs: mounted filesystem with ordered data mode.
[4294715.077000] kjournald starting.  Commit interval 5 seconds
[4294715.078000] EXT3 FS on hda8, internal journal
[4294715.078000] EXT3-fs: mounted filesystem with ordered data mode.
[4294719.455000] ACPI: AC Adapter [AC] (on-line)
[4294719.726000] ACPI: Battery Slot [BAT0] (battery present)
[4294719.786000] ACPI: Lid Switch [LID]
[4294719.786000] ACPI: Power Button (CM) [PBTN]
[4294719.786000] ACPI: Sleep Button (CM) [SBTN]
[4294719.865000] ibm_acpi: ec object not found
[4294719.881000] pcc_acpi: loading...
[4294719.968000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294723.311000] [drm] Initialized drm 1.0.1 20051102
[4294723.323000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294723.324000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294723.727000] ppdev: user-space parallel port driver
[4294724.019000] apm: BIOS not found.
[4294724.577000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294724.577000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294724.577000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294724.855000] [drm] Setting GART location based on new memory map
[4294724.856000] [drm] Loading R300 Microcode
[4294724.856000] [drm] writeback test succeeded in 1 usecs
[4294730.792000] NET: Registered protocol family 10
[4294730.792000] lo: Disabled Privacy Extensions
[4294730.792000] IPv6 over IPv4 tunneling driver
[4294730.992000] Bluetooth: Core ver 2.8
[4294730.992000] NET: Registered protocol family 31
[4294730.992000] Bluetooth: HCI device and connection manager initialized
[4294730.992000] Bluetooth: HCI socket layer initialized
[4294731.010000] Bluetooth: L2CAP ver 2.8
[4294731.010000] Bluetooth: L2CAP socket layer initialized
[4294731.018000] Bluetooth: RFCOMM socket layer initialized
[4294731.018000] Bluetooth: RFCOMM TTY layer initialized
[4294731.018000] Bluetooth: RFCOMM ver 1.7
[4294739.199000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294739.419000] ISO 9660 Extensions: RRIP_1991A
[4294741.222000] eth0: no IPv6 routers present

---

### Post by John.Michael.Kane on 2006-06-07
Have you tried installing with noacpi or acpi=off? sometimes this can lead to lockups , and freezing.

---

### Post by init6 on 2006-06-07
I booted the alternate install cd.  I escaped out of the gui to the boot prompt.

**boot:** install acpi=off

Install completed successfully.  After rebooting the machine froze up before I could get a terminal open in gnome.

---

### Post by init6 on 2006-06-07
Managed to get the system to stay up long enough to apt-get install linux-686-smp.

I rebooted keeping acpi=off as part of the parameters.  Still no luck.

---

### Post by bilange on 2006-06-07
Might be or might not be related, but I would test your system for functional memory, with like Memtest86 or others. 

If that program says he has troubles reading/writing to some memory addresses, in this case i would try to use your memory at a slower speed (333Mhz instead of 400Mhz, etc)

When you're talking about "crash" what are you talking about? The system just freezes? Graphical interface disappearing? The system just reboot itself without warnings?

---

### Post by John.Michael.Kane on 2006-06-07
bilange might be on to something with the memory.

init6 have you tired another distro say fedora core5 or suse MEPIS. to see if you get the same issues.

---

### Post by init6 on 2006-06-07
screen freezes and no further processing.  No black screens no rebooting.  Fan stays running, but everything else just stops working.

---

### Post by init6 on 2006-06-07
I'll try the memory test right now.

---

### Post by The Darkness on 2006-06-07
Do you have the latest BIOS update installed?
I had Linux install issues on my XPS notebook originally, until I updated to the latest BIOS rev. from Dell.

---

### Post by init6 on 2006-06-07
Mem test passed with flying colors.  

I'll go look for a bios flash.  However, this has happened with 5.04, 5.10, and now 6.06 on this laptop AND on my desktop.  Same trouble.  There has to be something I'm missing.

---

### Post by init6 on 2006-06-07
BIOS update complete.  Didn't fix the problem. :(

---

### Post by init6 on 2006-06-08
Figured it out.  Was an issue with ATI driver.

Thanks for everyone's assistance in this matter.

---

