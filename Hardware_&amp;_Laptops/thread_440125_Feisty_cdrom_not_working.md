---
title: "Feisty: cdrom not working"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by exoasol on 2007-05-11
I have searched the web posted this problem before, asked other forums, asked peers in a close by office, and I still am having this problem.

I have a working DVD burner.  I know it is working because up until the upgrade to feisty it was working fine.  I also used this drive to clean install feisty.  I have even tried to boot to live CD since the install and it stopped working and the drive was able to boot to live CD with no problems.  So the drive is good.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e7de6414-bc64-4cb8-a57f-ad6969ed60d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=07432824-4552-4cb4-9bbc-dc971d886dc5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

One of the problems is that my dev folder has no hdc.  When I try to MAKEDEV it says that it wont do that because udev is in control or something along those lines.  I have also used mknod to make hdc and sdc when I do this and then try to mount it tells me that hdc is not a valid block device.

I have the /media/cdrom0 folder.  

I am sure there is something else I have left out that I have tried and it not worked.

I appreciate any help I can get.

Thanks
Aaron

---

### Post by exoasol on 2007-05-15
bump because its still not working

---

### Post by exoasol on 2007-05-15
I replaced the drive and it works now.  The old drive works too, just not with ubuntu 7.04.  I dont know why

---

### Post by kunami on 2007-07-26
I'm having exactly the same problem, only my drive is on hda.

Here's my dmesg output, if someone would be so kind as to look. I've highlighted what I've thought that could be even remotely relevant in "grep"s for ide, ata, sd and hd.

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ce000 size: 0000000000002000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f5d0000 end: 000000003f6d0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f6d0000 size: 0000000000013000 end: 000000003f6e3000 type: 4
[    0.000000] copy_e820_map() start: 000000003f6e3000 size: 000000000091d000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7d50
[    0.000000] Entering add_active_range(0, 0, 259792) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259792
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259792
[    0.000000] On node 0 totalpages: 259792
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30179 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x000f7d20
[    0.000000] ACPI: XSDT (v001 PacBel PBNB0001 0x06040000  LTP 0x00000000) @ 0x3f6d9fd5
[    0.000000] ACPI: FADT (v003 INTEL  CRESTLNE 0x06040000 ALAN 0x00000001) @ 0x3f6e1bd2
[    0.000000] ACPI: MADT (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x3f6e1cc6
[    0.000000] ACPI: HPET (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x3f6e1d2e
[    0.000000] ACPI: MCFG (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x3f6e1d66
[    0.000000] ACPI: TCPA (v001 Intel   CRESTLN 0x06040000  0x00005a52) @ 0x3f6e1da2
[    0.000000] ACPI: TMOR (v001 PTLTD           0x06040000 PTL  0x00000003) @ 0x3f6e1dd4
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x3f6e1dfa
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f6e1e62
[    0.000000] ACPI: SLIC (v001 PacBel PBNB0001 0x06040000  LTP 0x00000000) @ 0x3f6e1e8a
[B][    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x3f6db75a
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x3f6db0c8[/B]
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Tst 0x00003000 INTL 0x20050624) @ 0x3f6da5f5
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu1Tst 0x00003000 INTL 0x20050624) @ 0x3f6da54f
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3f6da069
[    0.000000] ACPI: DSDT (v002 INTEL  CRESTLNE 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1795.702 MHz processor.
[   13.524309] Built 1 zonelists.  Total pages: 257763
[   13.524316] Kernel command line: root=UUID=58a0e225-aca4-49b0-a16b-cd51e0966284 ro quiet splash
[   13.524597] mapped APIC to ffffd000 (fee00000)
[   13.524602] mapped IOAPIC to ffffc000 (fec00000)
[   13.524607] Enabling fast FPU save and restore... done.
[   13.524612] Enabling unmasked SIMD FPU exception support... done.
[   13.524626] Initializing CPU#0
[   13.524722] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   13.527589] Console: colour VGA+ 80x25
[   13.528099] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.528684] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.575751] Memory: 1018984k/1039168k available (1992k kernel code, 19440k reserved, 900k data, 328k init, 121664k highmem)
[   13.575769] virtual kernel memory layout:
[   13.575771]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   13.575773]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.575776]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.575778]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.575780]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   13.575783]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   13.575785]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   13.575791] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.576047] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.576058] hpet0: 3 64-bit timers, 14318180 Hz
[   13.577066] Using HPET for base-timer
[   13.656009] Calibrating delay using timer specific routine.. 3596.26 BogoMIPS (lpj=7192531)
[   13.656078] Security Framework v1.0.0 initialized
[   13.656085] SELinux:  Disabled at boot.
[   13.656111] Mount-cache hash table entries: 512
**[   13.656323] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001**
[   13.656338] monitor/mwait feature present.
[   13.656342] using mwait in idle threads.
[   13.656349] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.656354] CPU: L2 cache: 2048K
[   13.656358] CPU: Physical Processor ID: 0
[   13.656362] CPU: Processor Core ID: 0
[   13.656366] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   13.656382] Compat vDSO mapped to ffffe000.
[   13.656388] Remapping vsyscall page to ffffe000
[   13.656408] Checking 'hlt' instruction... OK.
[   13.672172] SMP alternatives: switching to UP code
[   13.672771] Early unpacking initramfs... done
[   14.337912] ACPI: Core revision 20060707
[   14.338348] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.345159] CPU0: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
[   14.345192] SMP alternatives: switching to SMP code
[   14.345314] Booting processor 1/1 eip 3000
[   14.356031] Initializing CPU#1
[   14.435579] Calibrating delay using timer specific routine.. 3591.14 BogoMIPS (lpj=7182282)
[   14.435591] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   14.435601] monitor/mwait feature present.
[   14.435606] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.435610] CPU: L2 cache: 2048K
[   14.435615] CPU: Physical Processor ID: 0
[   14.435617] CPU: Processor Core ID: 1
[   14.435620] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   14.436478] CPU1: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz stepping 0d
[   14.436517] Total of 2 processors activated (7187.40 BogoMIPS).
[   14.436734] ENABLING IO-APIC IRQs
[   14.436978] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.583502] checking TSC synchronization across 2 CPUs: passed.
[    0.003997] Brought up 2 CPUs
[    0.080830] migration_cost=41
[    0.081292] Booting paravirtualized kernel on bare hardware
[    0.081434] Time: 22:44:39  Date: 06/26/107
[    0.081482] NET: Registered protocol family 16
[    0.081625] EISA bus registered
[    0.081636] ACPI: bus type pci registered
[    0.082118] PCI: PCI BIOS revision 3.00 entry at 0xfde01, last bus=7
[    0.082122] PCI: Using configuration type 1
[    0.082126] Setting up standard PCI resources
[    0.091400] ACPI: Interpreter enabled
[    0.091405] ACPI: Using IOAPIC for interrupt routing
[    0.092770] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.092782] PCI: Probing PCI hardware (bus 00)
[    0.093001] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.096274] Boot video device is 0000:01:00.0
[    0.097869] PCI: Transparent bridge - 0000:00:1e.0
[    0.098015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.120235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.121090] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.121589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.122512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.125347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.126635] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 12 14 15) *11
[    0.127124] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.127614] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 12 14 15)
[    0.128097] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.128576] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 12 14 15) *0, disabled.
[    0.129061] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.129542] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 12 14 15)
[    0.130020] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.132563] ACPI: Power Resource [QFAN] (off)
[    0.132797] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.132814] pnp: PnP ACPI init
[    0.138054] pnp: PnP ACPI: found 11 devices
[    0.138064] PnPBIOS: Disabled by ACPI PNP
[    0.138143] PCI: Using ACPI for IRQ routing
[    0.138148] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.258921] NET: Registered protocol family 8
[    0.258925] NET: Registered protocol family 20
[    0.260174] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[    0.260275] PCI: Bridge: 0000:00:01.0
[    0.260280]   IO window: 2000-2fff
[    0.260288]   MEM window: cc000000-ceffffff
[    0.260295]   PREFETCH window: d0000000-dfffffff
[    0.260303] PCI: Bridge: 0000:00:1c.0
[    0.260305]   IO window: disabled.
[    0.260316]   MEM window: f4100000-f41fffff
[    0.260323]   PREFETCH window: disabled.
[    0.260333] PCI: Bridge: 0000:00:1c.1
[    0.260339]   IO window: 3000-3fff
[    0.260348]   MEM window: f2000000-f3ffffff
[    0.260357]   PREFETCH window: f0000000-f1ffffff
[    0.260367] PCI: Bridge: 0000:00:1c.5
[    0.260372]   IO window: 4000-4fff
[    0.260382]   MEM window: f4000000-f40fffff
[    0.260389]   PREFETCH window: disabled.
[    0.260400] PCI: Bridge: 0000:00:1e.0
[    0.260402]   IO window: disabled.
[    0.260412]   MEM window: f4200000-f42fffff
[    0.260420]   PREFETCH window: disabled.
[    0.260450] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.260460] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.260499] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.260509] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.260546] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.260557] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.260594] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[    0.260605] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.260628] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.260676] NET: Registered protocol family 2
[    0.307905] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.308084] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.308955] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.309394] TCP: Hash tables configured (established 131072 bind 65536)
[    0.309399] TCP reno registered
[    0.324048] checking if image is initramfs... it is
[    1.632696] Freeing initrd memory: 6782k freed
[    1.632986] Simple Boot Flag at 0x36 set to 0x1
[    1.633802] audit: initializing netlink socket (disabled)
[    1.633832] audit(1185489880.724:1): initialized
[    1.634004] highmem bounce pool size: 64 pages
[    1.634149] VFS: Disk quotas dquot_6.5.1
[    1.634182] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.634271] io scheduler noop registered
[    1.634276] io scheduler anticipatory registered
[    1.634280] io scheduler deadline registered
[    1.634301] io scheduler cfq registered (default)
[    1.634773] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.634851] assign_interrupt_mode Found MSI capability
[    1.634857] Allocate Port Service[0000:00:01.0:pcie00]
[    1.634920] Allocate Port Service[0000:00:01.0:pcie02]
[    1.635117] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.635208] assign_interrupt_mode Found MSI capability
[    1.635213] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.635276] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.635478] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.635569] assign_interrupt_mode Found MSI capability
[    1.635574] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.635634] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.635837] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    1.635928] assign_interrupt_mode Found MSI capability
[    1.635933] Allocate Port Service[0000:00:1c.5:pcie00]
[    1.635996] Allocate Port Service[0000:00:1c.5:pcie02]
[    1.636312] isapnp: Scanning for PnP cards...
[    1.992635] isapnp: No Plug & Play device found
[    2.032844] Real Time Clock Driver v1.12ac
[    2.032953] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.034164] mice: PS/2 mouse device common for all mice
[    2.035242] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.035636] input: Macintosh mouse button emulation as /class/input/input0
[B][    2.035700] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.035707] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx[/B]
[    2.036131] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.040186] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.041865] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.041872] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.041877] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.041882] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.041886] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.042100] EISA: Probing bus 0 at eisa.0
[    2.042114] Cannot allocate resource for EISA slot 1
[    2.042121] Cannot allocate resource for EISA slot 2
[    2.042125] Cannot allocate resource for EISA slot 3
[    2.042129] Cannot allocate resource for EISA slot 4
[    2.042158] EISA: Detected 0 cards.
[    2.072299] TCP cubic registered
[    2.072314] NET: Registered protocol family 1
[    2.072350] Starting balanced_irq
[    2.072360] Using IPI No-Shortcut mode
[    2.072542] ACPI: (supports S0 S3 S4 S5)
[    2.072625]   Magic number: 15:977:755
[    2.073039] Freeing unused kernel memory: 328k freed
[    2.074858] Time: tsc clocksource has been installed.
[    2.087280] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.477755] Capability LSM initialized
[    3.563760] ACPI: Transitioning device [FAN] to D3
[    3.563766] ACPI: Transitioning device [FAN] to D3
[    3.563772] ACPI: Fan [FAN] (off)
[    3.571708] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.572188] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.573307] Monitor-Mwait will be used to enter C-1 state
[    3.573312] Monitor-Mwait will be used to enter C-2 state
[    3.573317] Monitor-Mwait will be used to enter C-3 state
[    3.573328] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.573339] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.574348] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.574743] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.575874] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.575885] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.578521] ACPI: Thermal Zone [THRM] (43 C)
[    4.496000] Time: hpet clocksource has been installed.
[    5.084000] usbcore: registered new interface driver usbfs
[    5.084000] usbcore: registered new interface driver hub
[    5.084000] usbcore: registered new device driver usb
[    5.164000] USB Universal Host Controller Interface driver v3.0
[    5.164000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.164000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    5.164000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.164000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.164000] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    5.164000] usb usb1: configuration #1 chosen from 1 choice
[    5.164000] hub 1-0:1.0: USB hub found
[    5.164000] hub 1-0:1.0: 2 ports detected
[    5.268000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    5.268000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    5.268000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.268000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.268000] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001820
[    5.268000] usb usb2: configuration #1 chosen from 1 choice
[    5.268000] hub 2-0:1.0: USB hub found
[    5.268000] hub 2-0:1.0: 2 ports detected
[    5.268000] ieee1394: Initialized config rom entry `ip1394'
[    5.296000] SCSI subsystem initialized
**[    5.304000] libata version 2.20 loaded.**
[    5.372000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[    5.372000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    5.372000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.372000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    5.372000] ehci_hcd 0000:00:1a.7: debug port 1
[    5.372000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    5.372000] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4504000
[    5.376000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.376000] usb usb3: configuration #1 chosen from 1 choice
[    5.376000] hub 3-0:1.0: USB hub found
[    5.376000] hub 3-0:1.0: 4 ports detected
[    5.480000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    5.480000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.480000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.480000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    5.480000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.480000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.480000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf4504400
[    5.484000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.484000] usb usb4: configuration #1 chosen from 1 choice
[    5.484000] hub 4-0:1.0: USB hub found
[    5.484000] hub 4-0:1.0: 6 ports detected
[    5.588000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    5.588000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.588000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.588000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.588000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001840
[    5.588000] usb usb5: configuration #1 chosen from 1 choice
[    5.588000] hub 5-0:1.0: USB hub found
[    5.588000] hub 5-0:1.0: 2 ports detected
[    5.692000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[    5.692000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.692000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.692000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.692000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001860
[    5.692000] usb usb6: configuration #1 chosen from 1 choice
[    5.692000] hub 6-0:1.0: USB hub found
[    5.692000] hub 6-0:1.0: 2 ports detected
[    5.720000] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    5.796000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    5.796000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.796000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.796000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.796000] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001880
[    5.796000] usb usb7: configuration #1 chosen from 1 choice
[    5.796000] hub 7-0:1.0: USB hub found
[    5.796000] hub 7-0:1.0: 2 ports detected
[    5.864000] usb 3-1: configuration #1 chosen from 1 choice
[    5.900000] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.952000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4200000-f42007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[B][    5.956000] ata_piix 0000:00:1f.2: version 2.10ac1
[    5.956000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    6.112000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    6.112000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    6.112000] ata1: SATA max UDMA/133 cmd 0x000118f8 ctl 0x000118ce bmdma 0x000118e0 irq 21
[    6.112000] ata2: SATA max UDMA/133 cmd 0x000118f0 ctl 0x000118ca bmdma 0x000118e8 irq 21
[    6.112000] scsi0 : ata_piix
[    6.276000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    6.276000] ata1.00: ATA-7: ST9160821AS, 3.ALB, max UDMA/133
[    6.276000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.284000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    6.284000] ata1.00: configured for UDMA/133
[    6.284000] scsi1 : ata_piix[/B]
[    6.436000] usb 5-1: new full speed USB device using uhci_hcd and address 2
[B][    6.440000] ATA: abnormal status 0x7F on port 0x000118f7
[    6.444000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    6.460000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    6.460000] sda: Write Protect is off
[    6.460000] sda: Mode Sense: 00 3a 00 00
[    6.460000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.460000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    6.460000] sda: Write Protect is off
[    6.460000] sda: Mode Sense: 00 3a 00 00
[    6.460000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.460000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    6.520000] sd 0:0:0:0: Attached scsi disk sda
[    6.528000] sd 0:0:0:0: Attached scsi generic sg0 type 0[/B]
[    6.636000] usb 5-1: configuration #1 chosen from 1 choice
[    6.836000] Attempting manual resume
[    6.836000] swsusp: Resume From Partition 8:5
[    6.836000] PM: Checking swsusp image.
[    6.864000] PM: Resume from disk failed.
[    6.912000] kjournald starting.  Commit interval 5 seconds
[    6.912000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.228000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004ce056241b00]
[   21.084000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.104000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.108000] agpgart: Detected an Intel 965GM Chipset.
[   21.128000] agpgart: AGP aperture is 256M @ 0x0
[   21.488000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.504000] sdhci: Secure Digital Host Controller Interface driver
[   21.504000] sdhci: Copyright(c) Pierre Ossman
[   21.504000] sdhci: SDHCI controller found at 0000:07:01.1 [1180:0822] (rev 19)
[   21.504000] ACPI: PCI Interrupt 0000:07:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.504000] mmc0: SDHCI at 0xf4200800 irq 17 DMA
[   21.848000] ieee80211_crypt: registered algorithm 'NULL'
[   21.972000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.972000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.224000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.224000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   22.224000] sky2 0000:06:00.0: v1.13 addr 0xf4000000 irq 17 Yukon-FE (0xb7) rev 3
[   22.224000] sky2 eth0: addr 00:1b:24:1a:85:73
[   22.244000] Linux video capture interface: v2.00
[   22.304000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   22.304000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   22.304000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.304000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   22.304000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.392000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b024)
[   22.420000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000
[   22.468000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.740000] nvidia: module license 'NVIDIA' taints kernel.
[   22.860000] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[   23.000000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.000000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   23.000000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.09  Sat May 26 00:47:07 PDT 2007
[   23.184000] usbcore: registered new interface driver speedtch
[   23.184000] usbcore: registered new interface driver uvcvideo
[   23.184000] USB Video Class driver (v0.1.0)
[   23.312000] speedtch 5-1:1.0: found stage 1 firmware speedtch-1.bin
[   23.348000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   23.348000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   23.416000] speedtch 5-1:1.0: found stage 2 firmware speedtch-2.bin
[   23.880000] lp: driver loaded but no devices found
[   24.020000] Adding 947792k swap on /dev/disk/by-uuid/20e9ea1b-111b-45a0-8f32-c1c177704cb7.  Priority:-1 extents:1 across:947792k
[   24.180000] EXT3 FS on sda3, internal journal
[   24.548000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.552000] ipw3945: Radio Frequency Kill Switch is On:
[   24.552000] Kill switch must be turned off for wireless networking to work.
[   24.640000] NTFS volume version 3.1.
[   25.504000] Using specific hotkey driver
[   25.560000] ibm_acpi: ec object not found
[   25.656000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.680000] input: Power Button (FF) as /class/input/input3
[   25.680000] ACPI: Power Button (FF) [PWRF]
[   25.680000] input: Lid Switch as /class/input/input4
[   25.680000] ACPI: Lid Switch [LID]
[   25.704000] ACPI: Battery Slot [BAT1] (battery absent)
[   25.724000] No dock devices found.
[   25.756000] ACPI: AC Adapter [ACAD] (off-line)
[   25.808000] pcc_acpi: loading...
[   27.364000] sky2 eth0: enabling interface
[   27.368000] sky2 eth0: ram buffer 4K
[   28.496000] ATM dev 0: ADSL line is synchronising
[   30.164000] apm: BIOS not found.
[   31.272000] Bluetooth: Core ver 2.11
[   31.272000] NET: Registered protocol family 31
[   31.272000] Bluetooth: HCI device and connection manager initialized
[   31.272000] Bluetooth: HCI socket layer initialized
[   31.416000] Bluetooth: L2CAP ver 2.8
[   31.416000] Bluetooth: L2CAP socket layer initialized
[   31.484000] Bluetooth: RFCOMM socket layer initialized
[   31.484000] Bluetooth: RFCOMM TTY layer initialized
[   31.484000] Bluetooth: RFCOMM ver 1.8
[   32.068000] PPP generic driver version 2.4.2
[   50.048000] NET: Registered protocol family 10
[   50.048000] lo: Disabled Privacy Extensions
[   50.048000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.496000] ATM dev 0: ADSL line is up (4096 kb/s down | 256 kb/s up)
[   87.608000] nas0: no IPv6 routers present
[   87.636000] NET: Registered protocol family 17
[   87.880000] NET: Registered protocol family 24
[  322.564000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[  322.800000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  338.632000] ipw3945: Radio Frequency Kill Switch is On:
[  338.632000] Kill switch must be turned off for wireless networking to work.
```

This is happening on a Packard Bell Easynote MB65-P-002 laptop running Feisty desktop i386. Any idea on how to solve it?

---

### Post by Yuri77 on 2007-07-31
I had the same problem, here is described how we solved it:

[http://ubuntuforums.org/showthread.php?t=509176](http://ubuntuforums.org/showthread.php?t=509176)

If it will work for you, please tell us.

---

### Post by wpshooter on 2007-07-31
> **exoasol said:**
> I replaced the drive and it works now.  The old drive works too, just not with ubuntu 7.04.  I dont know why

Have you tried updating the **firmware** to the latest and greatest version on your old CD-rom drive ?

---

