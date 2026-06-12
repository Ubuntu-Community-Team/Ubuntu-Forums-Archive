---
title: "Silicon sil3112 - soft resetting port"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by antibios on 2007-08-16
I just purchased a SIL3112 with two 500G Maxtor drives.  The card is recognised correctly and I can see both the drives perfectly.  However when try to copy large amounts of data (seems like anything > 1G), I get the following errors:

[  866.871478] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  866.871490] ata3.00: cmd 35/00:00:e7:ea:20/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[  866.871492]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  867.183184] ata3: soft resetting port
[  867.339042] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  867.348295] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[  867.356298] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[  867.356305] ata3.00: configured for UDMA/100
[  867.356320] ata3: EH complete
[  867.365054] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[  867.369354] sdc: Write Protect is off
[  867.369360] sdc: Mode Sense: 00 3a 00 00
[  867.399195] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Now at first I thought that it might have been a problem with the drives, so I downloaded the Maxtor ISO and tested both the drives, and they both reported OK.  So next step, I tried formatting one drive with ext3 and the other with xfs, and they both report the same error.  Has anyone seen errors like this when using a SIL3112?  Or what does it mean when it says "Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen"?

System Info:
antibios@dwarfstar ~ $ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
02:03.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)


antibios@dwarfstar ~ $ sudo hdparm -i /dev/sdc
Password:

/dev/sdc:

 Model=Maxtor 3H500F0                          , FwRev=HA431DD0, SerialNo=H818BK1H
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


antibios@dwarfstar ~/tmp $ cat dmesg.20070815
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4ce0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f68b0
[    0.000000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff6980
[    0.000000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 2430.184 MHz processor.
[   31.346557] Built 1 zonelists.  Total pages: 130033
[   31.346562] Kernel command line: root=UUID=be3cb345-7507-4475-9acc-90cdd8a42e5f ro quiet splash
[   31.346736] mapped APIC to ffffd000 (fee00000)
[   31.346739] mapped IOAPIC to ffffc000 (fec00000)
[   31.346742] Enabling fast FPU save and restore... done.
[   31.346746] Enabling unmasked SIMD FPU exception support... done.
[   31.346762] Initializing CPU#0
[   31.346856] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   31.348221] Console: colour VGA+ 80x25
[   31.348651] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.349016] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.361116] Memory: 507456k/524224k available (1992k kernel code, 16224k reserved, 893k data, 328k init, 0k highmem)
[   31.361127] virtual kernel memory layout:
[   31.361128]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   31.361129]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.361131]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   31.361132]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   31.361133]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   31.361134]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   31.361135]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   31.361139] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.438779] Calibrating delay using timer specific routine.. 4864.10 BogoMIPS (lpj=9728215)
[   31.438825] Security Framework v1.0.0 initialized
[   31.438832] SELinux:  Disabled at boot.
[   31.438851] Mount-cache hash table entries: 512
[   31.439009] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   31.439022] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   31.439026] CPU: L2 cache: 512K
[   31.439028] CPU: Hyper-Threading is disabled
[   31.439030] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
[   31.439043] Compat vDSO mapped to ffffe000.
[   31.439047] Remapping vsyscall page to ffffe000
[   31.439060] Checking 'hlt' instruction... OK.
[   31.454867] SMP alternatives: switching to UP code
[   31.455065] Freeing SMP alternatives: 11k freed
[   31.455292] Early unpacking initramfs... done
[   31.813996] ACPI: Core revision 20060707
[   31.819500] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.824276] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   31.824321] Total of 1 processors activated (4864.10 BogoMIPS).
[   31.824450] ENABLING IO-APIC IRQs
[   31.824641] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   31.970351] Brought up 1 CPUs
[   31.970623] Booting paravirtualized kernel on bare hardware
[   31.970707] Time: 10:35:38  Date: 07/15/107
[   31.970740] NET: Registered protocol family 16
[   31.970846] EISA bus registered
[   31.970852] ACPI: bus type pci registered
[   31.995060] PCI: PCI BIOS revision 2.10 entry at 0xfa460, last bus=2
[   31.995063] PCI: Using configuration type 1
[   31.995065] Setting up standard PCI resources
[   32.014086] ACPI: Interpreter enabled
[   32.014091] ACPI: Using IOAPIC for interrupt routing
[   32.014787] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.014792] PCI: Probing PCI hardware (bus 00)
[   32.015402] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   32.015404] * this clock source is slow. If you are sure your timer does not have
[   32.015405] * this bug, please use "acpi_pm_good" to disable the workaround
[   32.015450] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[   32.015454] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[   32.015689] Boot video device is 0000:01:00.0
[   32.015893] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   32.015962] PCI: Transparent bridge - 0000:00:1e.0
[   32.015991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.038606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   32.039769] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   32.040034] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   32.040295] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   32.040556] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   32.040814] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   32.041074] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   32.041333] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   32.041592] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   32.044148] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.044166] pnp: PnP ACPI init
[   32.047473] pnp: PnP ACPI: found 10 devices
[   32.047479] PnPBIOS: Disabled by ACPI PNP
[   32.047537] PCI: Using ACPI for IRQ routing
[   32.047541] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.120356] NET: Registered protocol family 8
[   32.120358] NET: Registered protocol family 20
[   32.120802] PCI: Bridge: 0000:00:01.0
[   32.120805]   IO window: disabled.
[   32.120810]   MEM window: e8000000-e9ffffff
[   32.120815]   PREFETCH window: d8000000-e7ffffff
[   32.120821] PCI: Bridge: 0000:00:1e.0
[   32.120824]   IO window: 9000-afff
[   32.120829]   MEM window: ea000000-ebffffff
[   32.120834]   PREFETCH window: 30000000-300fffff
[   32.120853] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   32.120884] NET: Registered protocol family 2
[   32.158230] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   32.158325] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   32.158423] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   32.158475] TCP: Hash tables configured (established 16384 bind 8192)
[   32.158478] TCP reno registered
[   32.170261] checking if image is initramfs... it is
[   32.876954] Freeing initrd memory: 8036k freed
[   32.877449] audit: initializing netlink socket (disabled)
[   32.877465] audit(1187174138.608:1): initialized
[   32.877641] VFS: Disk quotas dquot_6.5.1
[   32.877665] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.877719] io scheduler noop registered
[   32.877722] io scheduler anticipatory registered
[   32.877725] io scheduler deadline registered
[   32.877734] io scheduler cfq registered (default)
[   32.878050] isapnp: Scanning for PnP cards...
[   33.231696] isapnp: No Plug & Play device found
[   33.260148] Real Time Clock Driver v1.12ac
[   33.260205] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.260321] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.260516] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.261241] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.261567] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.261854] mice: PS/2 mouse device common for all mice
[   33.262510] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.262784] input: Macintosh mouse button emulation as /class/input/input0
[   33.262825] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.262830] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.263075] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   33.263078] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   33.266834] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.266842] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.267031] EISA: Probing bus 0 at eisa.0
[   33.267052] Cannot allocate resource for EISA slot 4
[   33.267054] Cannot allocate resource for EISA slot 5
[   33.267066] EISA: Detected 0 cards.
[   33.297158] TCP cubic registered
[   33.297165] NET: Registered protocol family 1
[   33.297191] Using IPI No-Shortcut mode
[   33.297264] ACPI: (supports S0 S1 S4 S5)
[   33.297315]   Magic number: 3:228:578
[   33.297499]   hash matches device pcspkr
[   33.297885] Freeing unused kernel memory: 328k freed
[   33.301121] Time: tsc clocksource has been installed.
[   33.313272] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.428385] Capability LSM initialized
[   34.446522] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   34.479982] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   34.587482] md: linear personality registered for level -1
[   34.591465] md: multipath personality registered for level -4
[   34.595317] md: raid0 personality registered for level 0
[   34.599792] md: raid1 personality registered for level 1
[   34.603585] raid5: automatically using best checksumming function: pIII_sse
[   34.619945]    pIII_sse  :  3067.000 MB/sec
[   34.619947] raid5: using function: pIII_sse (3067.000 MB/sec)
[   34.691888] raid6: int32x1    663 MB/s
[   34.759844] raid6: int32x2    710 MB/s
[   34.827797] raid6: int32x4    681 MB/s
[   34.895716] raid6: int32x8    461 MB/s
[   34.963658] raid6: mmxx1     1855 MB/s
[   35.031596] raid6: mmxx2     2478 MB/s
[   35.099567] raid6: sse1x1    1156 MB/s
[   35.167479] raid6: sse1x2    2171 MB/s
[   35.235402] raid6: sse2x1    1797 MB/s
[   35.303357] raid6: sse2x2    2740 MB/s
[   35.303359] raid6: using algorithm sse2x2 (2740 MB/s)
[   35.303363] md: raid6 personality registered for level 6
[   35.303365] md: raid5 personality registered for level 5
[   35.303367] md: raid4 personality registered for level 4
[   35.344214] md: raid10 personality registered for level 10
[   35.798763] usbcore: registered new interface driver usbfs
[   35.798791] usbcore: registered new interface driver hub
[   35.798827] usbcore: registered new device driver usb
[   35.799896] USB Universal Host Controller Interface driver v3.0
[   35.799954] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.799967] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   35.799971] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   35.800127] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   35.800154] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000b800
[   35.800273] usb usb1: configuration #1 chosen from 1 choice
[   35.800306] hub 1-0:1.0: USB hub found
[   35.800314] hub 1-0:1.0: 2 ports detected
[   35.886063] SCSI subsystem initialized
[   35.892056] libata version 2.20 loaded.
[   35.903754] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   35.903758] e100: Copyright(c) 1999-2006 Intel Corporation
[   35.906900] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   35.906914] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   35.906918] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   35.906942] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   35.906970] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000b000
[   35.907075] usb usb2: configuration #1 chosen from 1 choice
[   35.907102] hub 2-0:1.0: USB hub found
[   35.907112] hub 2-0:1.0: 2 ports detected
[   36.014793] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   36.014807] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.014811] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.014836] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   36.014865] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[   36.014969] usb usb3: configuration #1 chosen from 1 choice
[   36.014999] hub 3-0:1.0: USB hub found
[   36.015008] hub 3-0:1.0: 2 ports detected
[   36.122776] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   36.122795] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   36.122799] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   36.122828] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   36.122868] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   36.122878] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xec000000
[   36.126751] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.126836] usb usb4: configuration #1 chosen from 1 choice
[   36.126866] hub 4-0:1.0: USB hub found
[   36.126876] hub 4-0:1.0: 6 ports detected
[   36.239544] ata_piix 0000:00:1f.1: version 2.10ac1
[   36.239563] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   36.239583] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   36.239642] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   36.239680] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   36.239699] scsi0 : ata_piix
[   36.650476] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   36.650482] ata1.00: ATA-6: ST380024A, 3.33, max UDMA/100
[   36.650485] ata1.00: 156301488 sectors, multi 16: LBA
[   36.651801] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   36.651805] ata1.01: ATA-6: WDC WD2500JB-00GVA0, 08.02D08, max UDMA/100
[   36.651807] ata1.01: 488397168 sectors, multi 16: LBA48
[   36.662402] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   36.662406] ata1.00: configured for UDMA/100
[   36.675514] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   36.675518] ata1.01: configured for UDMA/100
[   36.675530] scsi1 : ata_piix
[   36.834031] scsi 0:0:0:0: Direct-Access     ATA      ST380024A        3.33 PQ: 0 ANSI: 5
[   36.834422] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2500JB-00G 08.0 PQ: 0 ANSI: 5
[   36.835100] sata_sil 0000:02:03.0: version 2.2
[   36.835122] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.835194] ata3: SATA max UDMA/100 cmd 0xe08d8080 ctl 0xe08d808a bmdma 0xe08d8000 irq 16
[   36.835224] ata4: SATA max UDMA/100 cmd 0xe08d80c0 ctl 0xe08d80ca bmdma 0xe08d8008 irq 16
[   36.835234] scsi2 : sata_sil
[   36.847724] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   36.847749] sda: Write Protect is off
[   36.847752] sda: Mode Sense: 00 3a 00 00
[   36.847772] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.847836] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   36.847848] sda: Write Protect is off
[   36.847850] sda: Mode Sense: 00 3a 00 00
[   36.847869] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.847872]  sda: sda1 sda2 sda3 sda4
[   36.874541] sd 0:0:0:0: Attached scsi disk sda
[   36.874709] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   36.874723] sdb: Write Protect is off
[   36.874726] sdb: Mode Sense: 00 3a 00 00
[   36.874745] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.874791] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   36.874803] sdb: Write Protect is off
[   36.874805] sdb: Mode Sense: 00 3a 00 00
[   36.874824] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.874827]  sdb: sdb1 sdb2 sdb3
[   36.901811] sd 0:0:1:0: Attached scsi disk sdb
[   36.906800] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.906928] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   37.307721] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.318699] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.318708] ata3.00: ATA-7: Maxtor 3H500F0, HA431DD0, max UDMA/133
[   37.318711] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.321367] kjournald starting.  Commit interval 5 seconds
[   37.321379] EXT3-fs: mounted filesystem with ordered data mode.
[   37.330691] ata3.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.330701] ata3.00: configured for UDMA/100
[   37.330719] scsi3 : sata_sil
[   37.800991] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.814257] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.814264] ata4.00: ATA-7: Maxtor 3H500F0, HA431DD0, max UDMA/133
[   37.814267] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.826447] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   37.826455] ata4.00: configured for UDMA/100
[   37.826579] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 3H500F0   HA43 PQ: 0 ANSI: 5
[   37.826657] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   37.826671] sdc: Write Protect is off
[   37.826674] sdc: Mode Sense: 00 3a 00 00
[   37.826693] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.826747] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   37.826758] sdc: Write Protect is off
[   37.826761] sdc: Mode Sense: 00 3a 00 00
[   37.826779] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.826783]  sdc: sdc1
[   37.857085] sd 2:0:0:0: Attached scsi disk sdc
[   37.857130] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   37.857356] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 3H500F0   HA43 PQ: 0 ANSI: 5
[   37.857519] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   37.857533] sdd: Write Protect is off
[   37.857536] sdd: Mode Sense: 00 3a 00 00
[   37.857555] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.857605] SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
[   37.857682] sdd: Write Protect is off
[   37.857685] sdd: Mode Sense: 00 3a 00 00
[   37.857704] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.857707]  sdd: unknown partition table
[   37.891072] sd 3:0:0:0: Attached scsi disk sdd
[   37.891119] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   37.891379] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   37.913932] e100: eth0: e100_probe: addr 0xeb002000, irq 20, MAC addr 00:20:ED:6D:36:A3
[   52.755340] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   54.258395] NET: Registered protocol family 17
[   54.506056] Linux agpgart interface v0.102 (c) Dave Jones
[   54.559373] agpgart: Detected an Intel 845G Chipset.
[   54.565135] agpgart: AGP aperture is 128M @ 0xd0000000
[   54.592075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.597089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.817935] iTCO_vendor_support: vendor-support=0
[   54.838008] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   54.838105] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x4060)
[   54.838150] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   54.943983] input: PC Speaker as /class/input/input2
[   54.978896] intel_rng: FWH not detected
[   55.328961] parport: PnPBIOS parport detected.
[   55.329001] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   55.352811] Linux video capture interface: v2.00
[   55.592054] nvidia: module license 'NVIDIA' taints kernel.
[   55.866351] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   55.866671] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   55.878417] saa7130/34: v4l2 driver version 0.2.14 loaded
[   55.878497] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 21
[   55.878507] saa7133[0]: found at 0000:02:02.0, rev: 208, irq: 21, latency: 32, mmio: 0xeb001000
[   55.878514] saa7133[0]: subsystem: 17de:7201, board: Tevion/KWorld DVB-T 220RF [card=88,autodetected]
[   55.878524] saa7133[0]: board init: gpio is 100
[   56.020235] saa7133[0]: i2c eeprom 00: de 17 01 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020248] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020259] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020270] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020281] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020291] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020302] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.020313] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.156103] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   56.208053] tuner 0-004b: setting tuner address to 61
[   56.248106] tuner 0-004b: type set to tda8290+75a
[   56.367906] tuner 0-004b: setting tuner address to 61
[   56.407869] tuner 0-004b: type set to tda8290+75a
[   56.478671] saa7133[0]: registered device video0 [v4l2]
[   56.478705] saa7133[0]: registered device vbi0
[   56.478738] saa7133[0]: registered device radio0
[   56.478918] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   56.478957] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   56.509234] saa7134 ALSA driver for DMA sound loaded
[   56.509265] saa7133[0]/alsa: saa7133[0] at 0xeb001000 irq 21 registered as card -2
[   56.799511] intel8x0_measure_ac97_clock: measured 56756 usecs
[   56.799516] intel8x0: clocking to 48000
[   56.959084] Intel ISA PCIC probe: not found.
[   57.041108] lp0: using parport0 (interrupt-driven).
[   57.142617] fuse init (API version 7.8)
[   57.315038] DVB: registering new adapter (saa7133[0]).
[   57.315044] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   57.554939] Adding 522104k swap on /dev/disk/by-uuid/c118ed2e-75ac-40a6-a054-cfb4e61b165a.  Priority:-1 extents:1 across:522104k
[   57.662123] EXT3 FS on sda4, internal journal
[   58.372997] NET: Registered protocol family 10
[   58.373109] lo: Disabled Privacy Extensions
[   68.592678] eth0: no IPv6 routers present
[   73.875920] kjournald starting.  Commit interval 5 seconds
[   73.876168] EXT3 FS on dm-1, internal journal
[   73.876174] EXT3-fs: mounted filesystem with ordered data mode.
[   73.996422] ReiserFS: dm-6: found reiserfs format "3.6" with standard journal
[   73.996449] ReiserFS: dm-6: using ordered data mode
[   73.999893] ReiserFS: dm-6: journal params: device dm-6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   74.001160] ReiserFS: dm-6: checking transaction log (dm-6)
[   74.022922] ReiserFS: dm-6: Using r5 hash to sort names
[   74.192869] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   74.193035] SGI XFS Quota Management subsystem
[   74.210536] Filesystem "dm-0": Disabling barriers, not supported by the underlying device
[   74.227057] XFS mounting filesystem dm-0
[   74.286068] Ending clean XFS mount for filesystem: dm-0
[   74.340115] kjournald starting.  Commit interval 5 seconds
[   74.341418] EXT3 FS on sdc1, internal journal
[   74.341424] EXT3-fs: mounted filesystem with ordered data mode.
[   74.357646] Adding 522104k swap on /dev/disk/by-uuid/c118ed2e-75ac-40a6-a054-cfb4e61b165a.  Priority:-2 extents:1 across:522104k
[   76.984000] input: Power Button (FF) as /class/input/input3
[   76.988911] ACPI: Power Button (FF) [PWRF]
[   77.028862] input: Power Button (CM) as /class/input/input4
[   77.033740] ACPI: Power Button (CM) [PWRB]
[   77.073117] input: Sleep Button (CM) as /class/input/input5
[   77.078001] ACPI: Sleep Button (CM) [SLPB]
[   77.097800] Using specific hotkey driver
[   77.136055] No dock devices found.
[   77.181471] ibm_acpi: ec object not found
[   77.330727] pcc_acpi: loading...
[   91.119790] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   91.119796] apm: overridden by ACPI.
[  104.963273] tda1004x: setting up plls for 48MHz sampling clock
[  106.957443] tda1004x: found firmware revision 23 -- ok
[  149.457471] NVRM: not using NVAGP, an AGPGART backend is loaded!
[  149.718083] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[  149.720952] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[  149.721715] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!



antibios@dwarfstar ~/tmp $ uname -a
Linux dwarfstar 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


antibios@dwarfstar ~/tmp $ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 7
cpu MHz         : 2430.160
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
bogomips        : 4864.12
clflush size    : 64

antibios@dwarfstar ~/tmp $ cat /proc/meminfo
MemTotal:       515992 kB
MemFree:          4884 kB
Buffers:          7816 kB
Cached:         257332 kB
SwapCached:          0 kB
Active:         253108 kB
Inactive:       208024 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515992 kB
LowFree:          4884 kB
SwapTotal:     1044208 kB
SwapFree:      1010140 kB
Dirty:           79080 kB
Writeback:       46196 kB
AnonPages:      196156 kB
Mapped:          56236 kB
Slab:            27572 kB
SReclaimable:     6324 kB
SUnreclaim:      21248 kB
PageTables:       3036 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1302204 kB
Committed_AS:   844080 kB
VmallocTotal:   507896 kB
VmallocUsed:     29668 kB
VmallocChunk:   470672 kB

---

### Post by ddrichardson on 2007-08-17
Check this [link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603") and let us know.

---

