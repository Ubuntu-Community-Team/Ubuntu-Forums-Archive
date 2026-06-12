---
title: "SATA woes (sil3114 card problem?)"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by syoung on 2007-01-04
I've been having some terrible trouble with Ubuntu Edgy Server and a sil3114 SATA controller. I'm at a loss as to what the problem is. I had the same results in both a Gentoo box and an Edgy box.

The card is [Syba SD-SATA-4P](http://www.newegg.com/Product/Product.asp?Item=N82E16815124020). It has fakeraid 0/1/5/10. I also purchased 2x [Seagate Barracuda 7200.10 320 GB ST3320620AS](http://www.okla.seagate.com/ww/v/index.jsp?locale=en-US&name=Barracuda_7200.10_SATA_320.3_GB&vgnextoid=2d1099f4fa74c010VgnVCM100000dd04090aRCRD&vgnextchannel=a32a2f290c5fb010VgnVCM100000dd04090aRCRD&reqPage=Model) ([alt](http://www.newegg.com/product/product.asp?item=N82E16822148140)) drives. The idea was to setup a simple software RAID1 array for my live music library.

Fast forward a bit... I start playing with mdadm and the behavior I see is upsetting. The array is created without issues. Set partition type to 0xFD, mdadm --create, mkfs.ext3 on both drives. It would take a while to sync, and seemed to be running well. During heavy use, one drive would get booted from the array. Adding it back caused a re-sync. **Also after a reboot**, the system would find problems with the file systems on these drives. I tried ext3 and reiser. Both would experience fsck errors during boot even if I had not performed any writes since running mkfs. The RAID1 array would not come back fully active as one drive would have an invalid superblock checksum and a re-sync would start after each reboot. I am not posting logs for this (yet) because I think the problem is deeper than my RAID setup routine.

Ok so RAID didn't seem to be going too well. I need a backup solution asap. So I decide to just use rsync in a cron job for my hacky music backup. So I just want to format both drives with mkfs.ext3 and start copying my data over. During the copy (or heavy use in general), both cp -r and rsync -av would end up with one of these:

```
[42950850.170000] EXT3-fs error (device sda1): ext3_new_block: Allocating block in system zone - blocks from 32636932, length 1
[42950850.190000] Aborting journal on device sda1.
[42950850.220000] ext3_abort called.
[42950850.250000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[42950850.280000] Remounting filesystem read-only
[42950850.310000] EXT3-fs error (device sda1): ext3_free_blocks: Freeing blocks in system zones - Block = 32636932, count = 1
[42950850.340000] EXT3-fs error (device sda1) in ext3_free_blocks_sb: Journal has aborted
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data

```

After reading a number [bits](http://blogs.sun.com/PlasticPixel/entry/build_your_own_multi_terabyte) and [pieces](http://www.newegg.com/Product/CustratingReview.asp?item=N82E16815124020) about the Sil3114 card I have, I decided to flash the card's BIOS to the non-raid version. I popped it out of my Linux box and into my Windows box. I loaded the latest driver from SI and flashed the BIOS to the latest version with no raid support. Great, maybe the fakeraid was the problem.

*****While I'm doing this, I decide to test out the drives while they are still in the Windows box. I formatted both to NTFS and did a heavy-duty copy of 6-7 GB of music to both drives and they work fine. I also go to Seagate's website and run their diagnostic software on the drives. Extended tests on each came out just fine.

So now I'm hoping I'm on to something. I put the card back in my Edgy box and try the drives with normal ext3. cp -r -f -v /oldIDEdata /newSATAmount.

```
[42950850.170000] EXT3-fs error (device sda1): ext3_new_block: Allocating block in system zone - blocks from 32636932, length 1
[42950850.190000] Aborting journal on device sda1.
[42950850.220000] ext3_abort called.
[42950850.250000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[42950850.280000] Remounting filesystem read-only
[42950850.310000] EXT3-fs error (device sda1): ext3_free_blocks: Freeing blocks in system zones - Block = 32636932, count = 1
[42950850.340000] EXT3-fs error (device sda1) in ext3_free_blocks_sb: Journal has aborted
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data

```

This happens with both drives. It *seems* to last longer this time. Similarly after re-mounting rw and trying again, rm -rf /newSATAmount gives the following:

```
[42950482.420000] EXT3-fs error (device sda1): ext3_free_inode: bit already cleared for inode 16302086
[42950482.430000] Aborting journal on device sda1.
[42950482.440000] EXT3-fs error (device sda1) in ext3_delete_inode: IO failure
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] ext3_abort called.
[42950482.470000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[42950482.490000] Remounting filesystem read-only
```

Again, both drives. Strangely enough a ReisferFS format will allow the copy to succeed. But when I reboot, I'll have loads of fsck errors. The block bitmaps will have corruptions and I eventually end up with a dead file system.

So I'm at a loss here. The whole setup works fine in my windows box. It does not work fine in Linux. Seagate diagnostics pass the drives with flying colors. Also I highly doubt I got **two** bad drives. I thought the problem was the card until I tried it in my windows box.

It looks like there is either an issue in sata_sil/libata with this card or with this card and my hardware. Of course I could be making a stupid mistake, too. You can read all the output from relevant commands below. All of this is running on a [MSI KT3 Ultra](http://www.msicomputer.com/product/detail_spec/product_detail.asp?model=KT3_Ultra) with an Athlon 1700+.

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:05.0 Mass storage controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```

dmesg (including some errors during heavy usage):
```
[42949372.960000] Linux version 2.6.17-10-server (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:29:32 UTC 2006 (Ubuntu 2.6.17-10.34-server)
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[42949372.960000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[42949372.960000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[42949372.960000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 511MB LOWMEM available.
[42949372.960000] found SMP MP-table at 000fb940
[42949372.960000] On node 0 totalpages: 131056
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   Normal zone: 126960 pages, LIFO batch:31
[42949372.960000] DMI 2.3 present.
[42949372.960000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa900
[42949372.960000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1fff0000
[42949372.960000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1fff0030
[42949372.960000] ACPI: MADT (v001 AMIINT VIA_K7   0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[42949372.960000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x808
[42949372.960000] ACPI: Local APIC address 0xfee00000
[42949372.960000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[42949372.960000] Processor #0 6:8 APIC version 16
[42949372.960000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[42949372.960000] IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[42949372.960000] ACPI: IRQ0 used by override.
[42949372.960000] ACPI: IRQ2 used by override.
[42949372.960000] ACPI: IRQ9 used by override.
[42949372.960000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[42949372.960000] Using ACPI (MADT) for SMP configuration information
[42949372.960000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hda3 ro quiet splash vga=0x318
[42949372.960000] mapped APIC to ffffd000 (fee00000)
[42949372.960000] mapped IOAPIC to ffffc000 (fec00000)
[42949372.960000] Enabling fast FPU save and restore... done.
[42949372.960000] Enabling unmasked SIMD FPU exception support... done.
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[42949372.960000] Detected 1466.749 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour dummy device 80x25
[42949376.670000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949376.670000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[42949376.690000] Memory: 510176k/524224k available (1903k kernel code, 13464k reserved, 1073k data, 312k init, 0k highmem)
[42949376.690000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949376.840000] Calibrating delay using timer specific routine.. 2936.22 BogoMIPS (lpj=14681105)
[42949376.840000] Security Framework v1.0.0 initialized
[42949376.840000] SELinux:  Disabled at boot.
[42949376.840000] Mount-cache hash table entries: 512
[42949376.840000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949376.840000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949376.840000] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[42949376.840000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[42949376.840000] CPU: L2 Cache: 256K (64 bytes/line)
[42949376.840000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[42949376.840000] Checking 'hlt' instruction... OK.
[42949376.880000] SMP alternatives: switching to UP code
[42949376.880000] Freeing SMP alternatives: 16k freed
[42949376.880000] checking if image is initramfs... it is
[42949377.440000] Freeing initrd memory: 5181k freed
[42949377.440000] ACPI: Core revision 20060707
[42949377.440000] ACPI: Looking for DSDT ... not found!
[42949377.440000] CPU0: AMD Athlon(tm) XP 1700+ stepping 01
[42949377.440000] Total of 1 processors activated (2936.22 BogoMIPS).
[42949377.440000] ENABLING IO-APIC IRQs
[42949377.440000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[42949377.650000] Brought up 1 CPUs
[42949377.650000] migration_cost=0
[42949377.650000] NET: Registered protocol family 16
[42949377.650000] EISA bus registered
[42949377.650000] ACPI: bus type pci registered
[42949377.650000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[42949377.650000] PCI: Using configuration type 1
[42949377.650000] Setting up standard PCI resources
[42949377.660000] ACPI: Interpreter enabled
[42949377.660000] ACPI: Using IOAPIC for interrupt routing
[42949377.660000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949377.660000] PCI: Probing PCI hardware (bus 00)
[42949377.660000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[42949377.660000] Boot video device is 0000:01:00.0
[42949377.660000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949377.680000] ACPI: Power Resource [URP1] (off)
[42949377.680000] ACPI: Power Resource [URP2] (off)
[42949377.680000] ACPI: Power Resource [FDDP] (off)
[42949377.680000] ACPI: Power Resource [LPTP] (off)
[42949377.680000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[42949377.680000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[42949377.680000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[42949377.680000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[42949377.680000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949377.680000] pnp: PnP ACPI init
[42949377.690000] pnp: PnP ACPI: found 12 devices
[42949377.690000] PnPBIOS: Disabled by ACPI PNP
[42949377.690000] PCI: Using ACPI for IRQ routing
[42949377.690000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949377.690000] PCI: Bridge: 0000:00:01.0
[42949377.690000]   IO window: disabled.
[42949377.690000]   MEM window: ddd00000-dfdfffff
[42949377.690000]   PREFETCH window: cdb00000-ddbfffff
[42949377.690000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[42949377.690000] NET: Registered protocol family 2
[42949377.790000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[42949377.790000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[42949377.790000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[42949377.790000] TCP: Hash tables configured (established 16384 bind 8192)
[42949377.790000] TCP reno registered
[42949377.790000] audit: initializing netlink socket (disabled)
[42949377.790000] audit(1167899516.790:1): initialized
[42949377.790000] VFS: Disk quotas dquot_6.5.1
[42949377.790000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949377.790000] Initializing Cryptographic API
[42949377.790000] io scheduler noop registered
[42949377.790000] io scheduler anticipatory registered
[42949377.790000] io scheduler deadline registered (default)
[42949377.790000] io scheduler cfq registered
[42949377.790000] isapnp: Scanning for PnP cards...
[42949378.140000] isapnp: No Plug & Play device found
[42949378.170000] Real Time Clock Driver v1.12ac
[42949378.170000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[42949378.170000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949378.170000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949378.170000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949378.180000] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949378.180000] mice: PS/2 mouse device common for all mice
[42949378.180000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949378.180000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949378.180000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949378.180000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[42949378.180000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949378.180000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949378.180000] EISA: Probing bus 0 at eisa.0
[42949378.180000] EISA: Detected 0 cards.
[42949378.180000] TCP bic registered
[42949378.180000] NET: Registered protocol family 1
[42949378.180000] NET: Registered protocol family 8
[42949378.180000] NET: Registered protocol family 20
[42949378.180000] Using IPI No-Shortcut mode
[42949378.180000] ACPI: (supports S0 S1 S4 S5)
[42949378.180000] Freeing unused kernel memory: 312k freed
[42949378.210000] input: AT Translated Set 2 keyboard as /class/input/input0
[42949378.240000] vesafb: framebuffer at 0xd0000000, mapped to 0xe0880000, using 6144k, total 65536k
[42949378.240000] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[42949378.240000] vesafb: protected mode interface info at c000:c2c0
[42949378.240000] vesafb: scrolling: redraw
[42949378.240000] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[42949378.430000] Console: switching to colour frame buffer device 128x48
[42949378.430000] fb0: VESA VGA frame buffer device
[42949378.440000] Capability LSM initialized
[42949378.480000] ACPI: Processor [CPU1] (supports 16 throttling states)
[42949379.120000] SCSI subsystem initialized
[42949379.120000] libata version 1.20 loaded.
[42949379.130000] sata_sil 0000:00:05.0: version 0.9
[42949379.130000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 169
[42949379.130000] sata_sil 0000:00:05.0: Applying R_ERR on DMA activate FIS errata fix
[42949379.130000] ata1: SATA max UDMA/100 cmd 0xE083EC80 ctl 0xE083EC8A bmdma 0xE083EC00 irq 169
[42949379.130000] ata2: SATA max UDMA/100 cmd 0xE083ECC0 ctl 0xE083ECCA bmdma 0xE083EC08 irq 169
[42949379.130000] ata3: SATA max UDMA/100 cmd 0xE083EE80 ctl 0xE083EE8A bmdma 0xE083EE00 irq 169
[42949379.130000] ata4: SATA max UDMA/100 cmd 0xE083EEC0 ctl 0xE083EECA bmdma 0xE083EE08 irq 169
[42949379.340000] ata1: SATA link down (SStatus 0)
[42949379.350000] scsi0 : sata_sil
[42949379.560000] ata2: SATA link down (SStatus 0)
[42949379.570000] scsi1 : sata_sil
[42949379.940000] ata3: SATA link up 1.5 Gbps (SStatus 113)
[42949379.960000] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
[42949379.960000] ata3: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[42949379.980000] ata3: dev 0 configured for UDMA/100
[42949379.980000] scsi2 : sata_sil
[42949380.350000] ata4: SATA link up 1.5 Gbps (SStatus 113)
[42949380.370000] ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
[42949380.370000] ata4: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[42949380.390000] ata4: dev 0 configured for UDMA/100
[42949380.390000] scsi3 : sata_sil
[42949380.390000]   Vendor: ATA       Model: ST3320620AS       Rev: 3.AA
[42949380.390000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[42949380.390000]   Vendor: ATA       Model: ST3320620AS       Rev: 3.AA
[42949380.390000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[42949380.400000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[42949380.400000] sda: Write Protect is off
[42949380.400000] sda: Mode Sense: 00 3a 00 00
[42949380.400000] SCSI device sda: drive cache: write back
[42949380.400000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[42949380.400000] sda: Write Protect is off
[42949380.400000] sda: Mode Sense: 00 3a 00 00
[42949380.400000] SCSI device sda: drive cache: write back
[42949380.400000]  sda: sda1
[42949380.410000] sd 2:0:0:0: Attached scsi disk sda
[42949380.420000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[42949380.420000] sdb: Write Protect is off
[42949380.420000] sdb: Mode Sense: 00 3a 00 00
[42949380.430000] SCSI device sdb: drive cache: write back
[42949380.430000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[42949380.430000] sdb: Write Protect is off
[42949380.430000] sdb: Mode Sense: 00 3a 00 00
[42949380.430000] SCSI device sdb: drive cache: write back
[42949380.430000]  sdb: sdb1
[42949380.440000] sd 3:0:0:0: Attached scsi disk sdb
[42949380.600000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[42949380.600000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[42949380.600000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[42949380.600000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[42949380.600000] VP_IDE: chipset revision 6
[42949380.600000] VP_IDE: not 100% native mode: will probe irqs later
[42949380.600000] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[42949380.600000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[42949380.600000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[42949380.600000] Probing IDE interface ide0...
[42949381.050000] hda: WDC WD800JB-00JJC0, ATA DISK drive
[42949381.350000] hdb: WDC WD800JB-00JJC0, ATA DISK drive
[42949381.410000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949381.420000] Probing IDE interface ide1...
[42949381.870000] hdc: ST340014A, ATA DISK drive
[42949382.710000] hdd: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[42949382.770000] ide1 at 0x170-0x177,0x376 on irq 15
[42949382.800000] hda: max request size: 128KiB
[42949382.800000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[42949382.800000] hda: cache flushes supported
[42949382.800000]  hda: hda1 hda2 hda3
[42949382.810000] hdb: max request size: 128KiB
[42949382.810000] hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[42949382.810000] hdb: cache flushes supported
[42949382.810000]  hdb: hdb1 hdb2
[42949382.820000] hdc: max request size: 512KiB
[42949382.820000] hdc: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[42949382.820000] hdc: cache flushes supported
[42949382.820000]  hdc: hdc1
[42949382.870000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[42949382.870000] Uniform CD-ROM driver Revision: 3.20
[42949383.350000] usbcore: registered new driver usbfs
[42949383.350000] usbcore: registered new driver hub
[42949383.350000] USB Universal Host Controller Interface driver v3.0
[42949383.350000] ACPI: PCI Interrupt 0000:00:11.2[D] -> GSI 21 (level, low) -> IRQ 177
[42949383.350000] PCI: Via IRQ fixup for 0000:00:11.2, from 10 to 1
[42949383.350000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[42949383.350000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[42949383.350000] uhci_hcd 0000:00:11.2: irq 177, io base 0x0000c800
[42949383.350000] usb usb1: configuration #1 chosen from 1 choice
[42949383.350000] hub 1-0:1.0: USB hub found
[42949383.350000] hub 1-0:1.0: 2 ports detected
[42949383.460000] ACPI: PCI Interrupt 0000:00:11.3[D] -> GSI 21 (level, low) -> IRQ 177
[42949383.460000] PCI: Via IRQ fixup for 0000:00:11.3, from 10 to 1
[42949383.460000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[42949383.460000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[42949383.460000] uhci_hcd 0000:00:11.3: irq 177, io base 0x0000cc00
[42949383.460000] usb usb2: configuration #1 chosen from 1 choice
[42949383.460000] hub 2-0:1.0: USB hub found
[42949383.460000] hub 2-0:1.0: 2 ports detected
[42949383.660000] Attempting manual resume
[42949383.670000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[42949387.570000] ReiserFS: hda3: using ordered data mode
[42949387.590000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[42949387.590000] ReiserFS: hda3: checking transaction log (hda3)
[42949387.620000] ReiserFS: hda3: Using r5 hash to sort names
[42949392.210000] r8169 Gigabit Ethernet driver 2.2LK loaded
[42949392.210000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 185
[42949392.210000] eth0: Identified chip type is 'RTL8169s/8110s'.
[42949392.210000] eth0: RTL8169 at 0xe0eb6b00, 00:14:6c:cb:d5:11, IRQ 185
[42949392.400000] FDC 0 is a post-1991 82077
[42949392.670000] input: PC Speaker as /class/input/input1
[42949392.740000] parport: PnPBIOS parport detected.
[42949392.740000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[42949392.770000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949392.910000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949392.970000] Linux agpgart interface v0.101 (c) Dave Jones
[42949392.980000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[42949392.990000] agpgart: AGP aperture is 128M @ 0xe0000000
[42949393.060000] r8169: eth0: link down
[42949393.300000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[42949393.310000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[42949393.310000] 8139cp: pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[42949393.310000] 8139cp: Try the "8139too" driver instead.
[42949393.330000] 8139too Fast Ethernet driver 0.9.27
[42949393.330000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 193
[42949393.330000] eth1: RealTek RTL8139 at 0xe0f48a00, 00:c0:26:75:f6:a8, IRQ 193
[42949393.330000] eth1:  Identified 8139 chip type 'RTL-8139C'
[42949393.370000] irda_init()
[42949393.370000] NET: Registered protocol family 23
[42949393.530000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[42949393.530000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[42949393.700000] ts: Compaq touchscreen protocol output
[42949393.760000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 201
[42949393.760000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[42949393.760000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[42949394.650000] lp0: using parport0 (interrupt-driven).
[42949394.800000] Adding 979956k swap on /dev/disk/by-uuid/6736388a-afac-4eb9-b8bc-c4eebd7dc224.  Priority:-1 extents:1 across:979956k
[42949395.210000] r8169: eth0: link up
[42949396.030000] NET: Registered protocol family 10
[42949396.030000] lo: Disabled Privacy Extensions
[42949396.030000] IPv6 over IPv4 tunneling driver
[42949406.360000] eth0: no IPv6 routers present
[42949409.980000] kjournald starting.  Commit interval 5 seconds
[42949409.980000] EXT3 FS on hda1, internal journal
[42949409.980000] EXT3-fs: mounted filesystem with ordered data mode.
[42949409.980000] kjournald starting.  Commit interval 5 seconds
[42949409.980000] EXT3 FS on hdb1, internal journal
[42949409.980000] EXT3-fs: mounted filesystem with ordered data mode.
[42949409.990000] kjournald starting.  Commit interval 5 seconds
[42949409.990000] EXT3 FS on hdb2, internal journal
[42949409.990000] EXT3-fs: mounted filesystem with ordered data mode.
[42949410.020000] ReiserFS: hdc1: found reiserfs format "3.6" with standard journal
[42949412.160000] ReiserFS: hdc1: using ordered data mode
[42949412.180000] ReiserFS: hdc1: journal params: device hdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[42949412.180000] ReiserFS: hdc1: checking transaction log (hdc1)
[42949412.200000] ReiserFS: hdc1: Using r5 hash to sort names
[42949412.240000] kjournald starting.  Commit interval 5 seconds
[42949412.240000] EXT3 FS on sda1, internal journal
[42949412.240000] EXT3-fs: mounted filesystem with ordered data mode.
[42949412.250000] kjournald starting.  Commit interval 5 seconds
[42949412.250000] EXT3 FS on sdb1, internal journal
[42949412.250000] EXT3-fs: mounted filesystem with ordered data mode.
[42950482.420000] EXT3-fs error (device sda1): ext3_free_inode: bit already cleared for inode 16302086
[42950482.430000] Aborting journal on device sda1.
[42950482.440000] EXT3-fs error (device sda1) in ext3_delete_inode: IO failure
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] __journal_remove_journal_head: freeing b_committed_data
[42950482.460000] ext3_abort called.
[42950482.470000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[42950482.490000] Remounting filesystem read-only
[42950684.270000] EXT3-fs error (device sdb1): ext3_new_block: Allocating block in system zone - blocks from 7307269, length 1
[42950684.280000] Aborting journal on device sdb1.
[42950684.290000] ext3_abort called.
[42950684.300000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[42950684.310000] Remounting filesystem read-only
[42950684.320000] EXT3-fs error (device sdb1): ext3_free_blocks: Freeing blocks in system zones - Block = 7307269, count = 1
[42950684.330000] EXT3-fs error (device sdb1) in ext3_free_blocks_sb: Journal has aborted
[42950685.090000] __journal_remove_journal_head: freeing b_committed_data
[42950771.750000] __journal_remove_journal_head: freeing b_committed_data
[42950771.750000] __journal_remove_journal_head: freeing b_committed_data
[42950771.750000] __journal_remove_journal_head: freeing b_committed_data
[42950771.750000] __journal_remove_journal_head: freeing b_committed_data
[42950771.750000] __journal_remove_journal_head: freeing b_committed_data
[42950787.160000] kjournald starting.  Commit interval 5 seconds
[42950787.160000] EXT3-fs warning (device sda1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[42950787.160000] EXT3-fs warning (device sda1): ext3_clear_journal_err: Marking fs in need of filesystem check.
[42950787.160000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[42950787.160000] EXT3 FS on sda1, internal journal
[42950787.160000] EXT3-fs: recovery complete.
[42950787.160000] EXT3-fs: mounted filesystem with ordered data mode.
[42950850.170000] EXT3-fs error (device sda1): ext3_new_block: Allocating block in system zone - blocks from 32636932, length 1
[42950850.190000] Aborting journal on device sda1.
[42950850.220000] ext3_abort called.
[42950850.250000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[42950850.280000] Remounting filesystem read-only
[42950850.310000] EXT3-fs error (device sda1): ext3_free_blocks: Freeing blocks in system zones - Block = 32636932, count = 1
[42950850.340000] EXT3-fs error (device sda1) in ext3_free_blocks_sb: Journal has aborted
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data
[42950850.420000] __journal_remove_journal_head: freeing b_committed_data
[42950961.610000] __journal_remove_journal_head: freeing b_committed_data
[42951056.760000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[42951071.690000] ReiserFS: sda1: using ordered data mode
[42951071.710000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[42951071.720000] ReiserFS: sda1: checking transaction log (sda1)
[42951072.190000] ReiserFS: sda1: Using r5 hash to sort names
[42951072.190000] ReiserFS: sda1: warning: Created .reiserfs_priv on sda1 - reserved for xattr storage.
```

---

### Post by syoung on 2007-01-05
Bump. As of now I'm just assuming that sil3114 is trash. I ordered a Promise card to give that one a whirl. But if anyone has ideas, let me know. Thanks.

---

### Post by jemenake on 2007-03-09
For what it's worth, I'm having almost exactly the same problem with two different SYBA SD-SATA-4P cards I bought. I have three 250GB drives arranged in a RAID5 using the Linux md driver, and a fourth card all by itself. When I start to load the drives with work (with a script that constantly creates and copies big files), the files start getting errors and, eventually the filesystems get set to read-only and end up with a bunch of fsck errors.

These SYBA's are going into the trash (or into a Windows machine... same difference :P ). 

How did that Promise card ever work out?

- Joe

---

### Post by NeoMatrixJR on 2007-08-16
NOOOOO....I don't know about newer cards but I've had nothing but trouble with Promise's older PATA RAID and NON-RAID cards.  They don't play nice with linux!  I'm still looking for something else.

---

### Post by midorigin on 2007-09-06
I found this thread after considering ordering the [Syba SD-SATA-4P]("http://www.newegg.com/product/product.asp?item=N82E16815124020") from Newegg.com. One reviewer there reports no issues using this under Feisty, but what you're saying about failing under heavy use worries me. I had hoped to use this in a software RAID.

I'm curious to hear if you got any of that resolved, and how the Promise card turned out.

---

### Post by pdurph on 2007-10-25
I'm having the same problem with an Asus A7V8X and 2 x Seagate 500 GB drives.

Are there *any* reliable PCI SATA controllers for Linux? Could this be a kernel issue? I'm running Ubuntu Feisty Fawn (Linux debra 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux).

---

### Post by copilot on 2007-11-17
This thread makes me sad. I'll post my outcome when the install is done, I'm using the same syba card in a gutsy system. I'll let everyone know how it works.

---

### Post by lbarbisan on 2008-02-24
I have same problem when copy big files with :
Sil3114 controller
4 Western DIgital 500gb (with jumper set to work in 150 Mb/s)

When i launched fsck it found a lot of errors...

I tried :
Raid 5, RAID 1 (using 2 and 4 drives)...same errors
So I  Reinstalled ubuntu twice (RAID 5, and RAID1 ) using RAID wizard...same errors...

Does any one found a solution ?

---

### Post by mntbighker on 2008-03-03
I don't have much in the way of helpful insight but I do have some observations. In using a sata_sil fake RAID0 for a couple of years I have observed some changes in how this works. Up until prior to Gutsy I was using the mdadm tools and I had a mdadm.conf that defined the RAID setup despite doing the initial setup in my BIOS. When I upgraded to Gutsy my RAID was fully broken as far as the kernel was concerned. The mdadm tools also were reporting that my RAID0 members were RAID1. I have since installed Mandriva and in the process reformatted my mirror. Now with no mdadm tools installed at all my RAID is recognized at boot time as a "/dev/devicemapper/somethingorother" and can be included in fstab as such. The message here is there appears to have been a recent fundamental shift in how this device is handled by the kernel. I don't know if there may have been a smooth transition process available to me? I can say that the installer scripts of recent distros appear not to recognize the old RAID setups. Mandriva did not see the XFS file system on my old RAID, but once reformatted XFS things appeared to fall in place. I'm going back to Gutsy tonight so I'll see if it picks up the new mirror set now.

edit: The installer didn't do a thing to detect or map my RAID0. I'm not sure what to do next. Searching the forums here so far has been little use.

---

### Post by lrosa on 2008-05-05
I'm having exactly the same annoying problem starting with with 8.04 (with Ubuntu 7 I had no problem at all :evil:).
I fresh installed 8.04, no upgrade.

My hardware is ADAPTEC 3405 Universal Serial (NOT a fake raid) with two SAMSUNG SATA HD321KJ configured as RAID1

---

### Post by 655 on 2008-05-13
Are there any reliable cards at this stage?  
All I want is a port multiplier, doesn't need to have RAID functionality...

---

