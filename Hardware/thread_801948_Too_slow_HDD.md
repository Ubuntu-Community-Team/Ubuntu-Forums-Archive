---
title: "Too slow HDD"
date: 2008-05-21
forum: Hardware
---

### Post by jspking on 2008-05-21
I've Installed Hardy server version.

my server spec is..

CPU Intel Xeon 2.4 (Pentium 4 HT)

M/B : Interl SHG2 


root@ubuntu-server:~# lspci
00:00.0 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset) (rev 13)
00:00.1 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset)
00:00.2 Host bridge: Broadcom CMIC-LE
00:02.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:0f.0 ISA bridge: Broadcom CSB5 South Bridge (rev 93)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 93)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 Host bridge: Broadcom CSB5 LPC bridge
00:11.0 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:11.2 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
01:04.0 Ethernet controller: Intel Corporation 82544GC Gigabit Ethernet Controller (LOM) (rev 02)
02:09.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
02:09.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)




My problem is.... see below

root@ubuntu-server:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   836 MB in  2.00 seconds = 417.52 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.58 MB/sec
root@ubuntu-server:~# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   428 MB in  2.00 seconds = 213.82 MB/sec
 Timing buffered disk reads:    8 MB in  3.67 seconds =   2.18 MB/sec


sdc is too much slower than sda

so I've tried figured this out with [http://ubuntuforums.org/showthread.php?t=678153](http://ubuntuforums.org/showthread.php?t=678153)


However that thread was not for my case.


Actually, my hdd is IDE...  see below ..

DMA of the hdd attached in ATA2 is disabled..

root@ubuntu-server:~# dmesg | grep ata
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[   54.614455] Memory: 507808k/524288k available (2157k kernel code, 15920k reserved, 998k data, 364k init, 0k highmem)
[   54.614472]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   55.414142] ACPI: EC: GPE = 0x35, I/O: command/status = 0xca7, data = 0xca6
[   59.160649] libata version 3.00 loaded.
[   59.544750] scsi1 : pata_serverworks
[   59.552655] scsi2 : pata_serverworks
[   59.552919] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2440 irq 14
[   59.552926] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2448 irq 15
[   59.891286] ata1.00: ATA-6: ST340014A, 8.01, max UDMA/100
[   59.891295] ata1.00: 78165360 sectors, multi 16: LBA48 
[   59.891650] ata1.01: ATA-6: ST3160023A, 8.01, max UDMA/100
[   59.891656] ata1.01: 312581808 sectors, multi 16: LBA48 
[   59.907222] ata1.00: configured for UDMA/100
[   59.923092] ata1.01: configured for UDMA/100
[   60.140884] ata2.00: ATA-7: ST3320620A, 3.AAC, max UDMA/100
[   60.140896] ata2.00: 625142448 sectors, multi 16: LBA48 
[   60.333088] ata2.01: HPA unlocked: 625140335 -> 625142448, native 625142448
[   60.333097] ata2.01: ATA-7: ST3320620A, 3.AAC, max UDMA/100
[   60.333102] ata2.01: 625142448 sectors, multi 16: LBA48 
[   60.333122] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   60.333127] ata2.01: simplex DMA is claimed by other device, disabling DMA
[   60.382039] ata2.00: configured for PIO4
[   60.426849] ata2.01: configured for PIO4
[   95.782000] EXT3-fs: mounted filesystem with ordered data mode.
[  177.466553] ReiserFS: sdb1: using ordered data mode
[  177.617196] ReiserFS: sdc1: using ordered data mode
[  177.650176] ReiserFS: sdd1: using ordered data mode




help me.... please..

---

### Post by Yellow Pasque on 2008-05-21
How do you have the HD's attached, on the same PATA cable?
Make sure your BIOS is up to date as well: [http://support.intel.com/support/motherboards/server/shg2/sb/cs-006505.htm](http://support.intel.com/support/motherboards/server/shg2/sb/cs-006505.htm)

---

### Post by sdennie on 2008-05-21
> **jspking said:**
> 
[   60.333122] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   60.333127] ata2.01: simplex DMA is claimed by other device, disabling DMA


That looks really odd to me and sounds like a motherboard problem.  I'm assuming that your CD drive is showing up as /dev/sdb.  What happens if you put the two hard drives as master/slave on the same IDE controller?

---

### Post by jspking on 2008-05-21
to Temüjin
  After reading your reply, I updated BIOS... etc.. Howerver situation is same.


to vor

All Devices On IDE0 Master/Slave are HDD. Also, All Devices on IDE1 Master/Slave are HDD, too.

All HDDs are connected with 80-wire version PATA Cable.


Thank you..

For more detail dmesg


root@ubuntu-server:~# dmesg 
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f67d0
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F67A0 checksum 0
[    0.000000] ACPI: RSDP 000F67A0, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 1FEF86CA, 0030 (r1 INTEL    RSDT    6040000 MSFT        0)
[    0.000000] ACPI: FACP 1FEFEEFA, 0074 (r1 INTEL  029D      6040000 MSFT  1000000)
[    0.000000] ACPI: DSDT 1FEF86FA, 6800 (r1 INTEL  029D      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEFFFC0, 0040
[    0.000000] ACPI: APIC 1FEFEF6E, 006A (r1 INTEL       APIC    6040000 MSFT        0)
[    0.000000] ACPI: BOOT 1FEFEFD8, 0028 (r1 INTEL  $SBFTBL$  6040000 MSFT        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 3, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000001fef0000 - 000000001feff000
[    0.000000] swsusp: Registered nosave memory region: 000000001feff000 - 000000001ff00000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=UUID=21f5397e-17c9-478d-b24b-c42cf5e8b6d4 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fec01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2399.854 MHz processor.
[   39.901482] Console: colour VGA+ 80x25
[   39.901487] console [tty0] enabled
[   39.901885] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   39.902227] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   39.914985] Memory: 507808k/524288k available (2157k kernel code, 15920k reserved, 998k data, 364k init, 0k highmem)
[   39.914995] virtual kernel memory layout:
[   39.914997]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   39.914998]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   39.914999]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   39.915000]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[   39.915002]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   39.915003]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   39.915004]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   39.915008] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   39.915053] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   39.994946] Calibrating delay using timer specific routine.. 4804.04 BogoMIPS (lpj=9608089)
[   39.994975] Security Framework initialized
[   39.994984] SELinux:  Disabled at boot.
[   39.995001] AppArmor: AppArmor initialized
[   39.995006] Failure registering capabilities with primary security module.
[   39.995016] Mount-cache hash table entries: 512
[   39.995177] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   39.995192] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   39.995195] CPU: L2 cache: 512K
[   39.995198] CPU: Physical Processor ID: 0
[   39.995201] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   39.995214] Compat vDSO mapped to ffffe000.
[   39.995230] Checking 'hlt' instruction... OK.
[   40.011361] SMP alternatives: switching to UP code
[   40.013336] Early unpacking initramfs... done
[   40.366263] ACPI: Core revision 20070126
[   40.366358] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.369037] CPU0: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[   40.369064] SMP alternatives: switching to SMP code
[   40.369890] Booting processor 1/1 eip 3000
[   40.380147] Initializing CPU#1
[   40.458178] Calibrating delay using timer specific routine.. 4799.67 BogoMIPS (lpj=9599349)
[   40.458189] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   40.458202] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   40.458205] CPU: L2 cache: 512K
[   40.458208] CPU: Physical Processor ID: 0
[   40.458211] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   40.458491] CPU1: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[   40.458543] Total of 2 processors activated (9603.71 BogoMIPS).
[   40.458862] ENABLING IO-APIC IRQs
[   40.459061] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   40.498727] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   40.498790] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   40.498795] ...trying to set up timer as Virtual Wire IRQ... works.
[   40.646060] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   40.666052] Brought up 2 CPUs
[   40.666095] CPU0 attaching sched-domain:
[   40.666098]  domain 0: span 03
[   40.666101]   groups: 01 02
[   40.666106]   domain 1: span 03
[   40.666109]    groups: 03
[   40.666112] CPU1 attaching sched-domain:
[   40.666114]  domain 0: span 03
[   40.666117]   groups: 02 01
[   40.666121]   domain 1: span 03
[   40.666123]    groups: 03
[   40.666512] net_namespace: 64 bytes
[   40.666522] Booting paravirtualized kernel on bare hardware
[   40.667216] Time:  9:00:57  Date: 05/21/08
[   40.667261] NET: Registered protocol family 16
[   40.667607] EISA bus registered
[   40.667614] ACPI: bus type pci registered
[   40.669459] PCI: PCI BIOS revision 2.10 entry at 0xfdace, last bus=2
[   40.669462] PCI: Using configuration type 1
[   40.669464] Setting up standard PCI resources
[   40.674432] ACPI: EC: Look up EC in DSDT
[   40.678632] ACPI: Interpreter enabled
[   40.678636] ACPI: (supports S0 S1 S4 S5)
[   40.678655] ACPI: Using IOAPIC for interrupt routing
[   40.679237] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   40.700652] ACPI: EC: GPE = 0x35, I/O: command/status = 0xca7, data = 0xca6
[   40.700657] ACPI: EC: driver started in interrupt mode
[   40.700796] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.701492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.706213] ACPI: PCI Root Bridge [PCI1] (0000:01)
[   40.706391] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   40.706718] ACPI: PCI Root Bridge [PCI2] (0000:02)
[   40.706824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI2._PRT]
[   40.707247] ACPI Exception (pci_link-0282): AE_AML_BAD_RESOURCE_LENGTH, Evaluating _CRS [20070126]
[   40.707253] ACPI: PCI Interrupt Link [LN1] (IRQs 10) *0
[   40.707451] ACPI: PCI Interrupt Link [LN10] (IRQs *16)
[   40.707649] ACPI: PCI Interrupt Link [LN11] (IRQs *17)
[   40.707848] ACPI: PCI Interrupt Link [LN12] (IRQs *18)
[   40.708047] ACPI: PCI Interrupt Link [LN13] (IRQs *19)
[   40.708247] ACPI: PCI Interrupt Link [LN14] (IRQs *20)
[   40.708446] ACPI: PCI Interrupt Link [LN15] (IRQs *21)
[   40.708645] ACPI: PCI Interrupt Link [LN16] (IRQs *22)
[   40.708846] ACPI: PCI Interrupt Link [LN17] (IRQs *23)
[   40.709045] ACPI: PCI Interrupt Link [LN18] (IRQs *24)
[   40.709245] ACPI: PCI Interrupt Link [LN19] (IRQs *25)
[   40.709444] ACPI: PCI Interrupt Link [LN1A] (IRQs *26)
[   40.709643] ACPI: PCI Interrupt Link [LN1B] (IRQs *27)
[   40.709852] ACPI: PCI Interrupt Link [LN1C] (IRQs *28)
[   40.710111] ACPI: PCI Interrupt Link [LN1D] (IRQs *29)
[   40.710310] ACPI: PCI Interrupt Link [LN1E] (IRQs *30)
[   40.710558] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.710622] pnp: PnP ACPI init
[   40.710637] ACPI: bus type pnp registered
[   40.713393] pnp: IRQ 8 override to edge, high
[   40.717620] pnp: PnP ACPI: found 15 devices
[   40.717623] ACPI: ACPI bus type pnp unregistered
[   40.717630] PnPBIOS: Disabled by ACPI PNP
[   40.718074] PCI: Using ACPI for IRQ routing
[   40.718080] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   40.745734] NET: Registered protocol family 8
[   40.745738] NET: Registered protocol family 20
[   40.745848] AppArmor: AppArmor Filesystem Enabled
[   40.749711] Time: tsc clocksource has been installed.
[   40.765755] system 00:07: ioport range 0x540-0x55f has been reserved
[   40.765759] system 00:07: ioport range 0x560-0x563 has been reserved
[   40.765762] system 00:07: ioport range 0x564-0x567 has been reserved
[   40.765765] system 00:07: ioport range 0x568-0x56f has been reserved
[   40.765768] system 00:07: ioport range 0x600-0x61f has been reserved
[   40.765777] system 00:08: ioport range 0x580-0x58d has been reserved
[   40.765780] system 00:08: ioport range 0xb04-0xb04 has been reserved
[   40.765783] system 00:08: ioport range 0x419-0x41b has been reserved
[   40.765786] system 00:08: ioport range 0x41d-0x41f has been reserved
[   40.765789] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   40.765792] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   40.765796] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   40.765799] system 00:08: ioport range 0xc06-0xc08 has been reserved
[   40.765802] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   40.765805] system 00:08: ioport range 0xc49-0xc4a has been reserved
[   40.765808] system 00:08: ioport range 0xc50-0xc51 has been reserved
[   40.765811] system 00:08: ioport range 0xc52-0xc52 has been reserved
[   40.765814] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   40.765817] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   40.765820] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   40.765823] system 00:08: ioport range 0xf50-0xf58 has been reserved
[   40.765826] system 00:08: ioport range 0x374-0x375 has been reserved
[   40.765829] system 00:08: ioport range 0xfe00-0xfe20 has been reserved
[   40.765832] system 00:08: ioport range 0x220-0x220 has been reserved
[   40.765835] system 00:08: ioport range 0x225-0x225 has been reserved
[   40.765838] system 00:08: ioport range 0x228-0x228 has been reserved
[   40.765841] system 00:08: ioport range 0x22a-0x22e has been reserved
[   40.765844] system 00:08: ioport range 0x102-0x105 has been reserved
[   40.765847] system 00:08: ioport range 0x107-0x107 has been reserved
[   40.765851] system 00:08: ioport range 0x40b-0x40b has been reserved
[   40.765854] system 00:08: ioport range 0x500-0x51f has been reserved
[   40.765859] system 00:08: ioport range 0x58e-0x593 has been reserved
[   40.765862] system 00:08: ioport range 0xca2-0xca5 has been reserved
[   40.796536] NET: Registered protocol family 2
[   40.837674] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   40.838058] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[   40.838463] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   40.839215] TCP: Hash tables configured (established 65536 bind 65536)
[   40.839222] TCP reno registered
[   40.849820] checking if image is initramfs... it is
[   41.293003] Switched to high resolution mode on CPU 1
[   41.296796] Switched to high resolution mode on CPU 0
[   41.546975] Freeing initrd memory: 7279k freed
[   41.547254] Simple Boot Flag at 0x7d set to 0x1
[   41.547978] audit: initializing netlink socket (disabled)
[   41.547998] audit(1211360457.476:1): initialized
[   41.551377] VFS: Disk quotas dquot_6.5.1
[   41.551506] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   41.551704] io scheduler noop registered
[   41.551707] io scheduler anticipatory registered
[   41.551709] io scheduler deadline registered
[   41.551730] io scheduler cfq registered (default)
[   41.551750] Boot video device is 0000:00:02.0
[   41.551757] PCI: Firmware left 0000:00:03.0 e100 interrupts enabled, disabling
[   41.552220] isapnp: Scanning for PnP cards...
[   41.906186] isapnp: No Plug & Play device found
[   41.953247] Real Time Clock Driver v1.12ac
[   41.953420] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   41.953585] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.953793] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   41.954757] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.955232] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   41.956624] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.956740] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   41.956930] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSC0] at 0x60,0x64 irq 1,12
[   41.959299] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.959307] serio: i8042 AUX port at 0x60,0x64 irq 12
[   41.976006] mice: PS/2 mouse device common for all mice
[   41.976215] EISA: Probing bus 0 at eisa.0
[   41.976232] Cannot allocate resource for EISA slot 2
[   41.976265] EISA: Detected 0 cards.
[   41.976270] cpuidle: using governor ladder
[   41.976272] cpuidle: using governor menu
[   41.976405] NET: Registered protocol family 1
[   41.976447] Using IPI No-Shortcut mode
[   41.976494] registered taskstats version 1
[   41.976623]   Magic number: 8:485:20
[   41.976800] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   41.976803] EDD information not available.
[   41.977266] Freeing unused kernel memory: 364k freed
[   42.003268] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   43.295120] fuse init (API version 7.9)
[   43.325607] ACPI: Invalid PBLK length [0]
[   43.325653] ACPI: Invalid PBLK length [0]
[   43.325677] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   43.325693] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   43.562162] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   43.562172] e100: Copyright(c) 1999-2006 Intel Corporation
[   43.562297] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 18 (level, low) -> IRQ 16
[   43.656827] SCSI subsystem initialized
[   43.752700] libata version 3.00 loaded.
[   43.761987] usbcore: registered new interface driver usbfs
[   43.762030] usbcore: registered new interface driver hub
[   43.812737] usbcore: registered new device driver usb
[   43.817900] e100: eth0: e100_probe: addr 0xfc021000, irq 16, MAC addr 00:02:b3:52:73:a3
[   43.818012] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   43.832998] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   43.833526] ACPI Exception (pci_link-0282): AE_AML_BAD_RESOURCE_LENGTH, Evaluating _CRS [20070126]
[   43.833536] ACPI: Unable to set IRQ for PCI Interrupt Link [LN1]. Try pci=noacpi or acpi=off
[   43.833543] ACPI: Invalid IRQ link routing entry
[   43.833547] ACPI: Unable to derive IRQ for device 0000:00:0f.2
[   43.833551] ACPI: PCI Interrupt 0000:00:0f.2[A]: no GSI - using IRQ 10
[   43.833580] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   43.834020] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[   43.834054] ohci_hcd 0000:00:0f.2: irq 10, io mem 0xfc022000
[   43.890718] usb usb1: configuration #1 chosen from 1 choice
[   43.890767] hub 1-0:1.0: USB hub found
[   43.890782] hub 1-0:1.0: 4 ports detected
[   44.004527] scsi0 : pata_serverworks
[   44.006744] scsi1 : pata_serverworks
[   44.006993] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2440 irq 14
[   44.006999] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2448 irq 15
[   44.215969] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   44.215976] Copyright (c) 1999-2006 Intel Corporation.
[   44.344216] ata1.00: ATA-6: ST340014A, 8.01, max UDMA/100
[   44.344224] ata1.00: 78165360 sectors, multi 16: LBA48 
[   44.344506] ata1.01: ATA-6: ST3160023A, 8.01, max UDMA/100
[   44.344512] ata1.01: 312581808 sectors, multi 16: LBA48 
[   44.360188] ata1.00: configured for UDMA/100
[   44.376213] ata1.01: configured for UDMA/100
[   44.411226] Floppy drive(s): fd0 is 1.44M
[   44.426892] FDC 0 is a National Semiconductor PC87306
[   44.593347] ata2.00: ATA-7: ST3320620A, 3.AAC, max UDMA/100
[   44.593353] ata2.00: 625142448 sectors, multi 16: LBA48 
[   44.791331] ata2.01: HPA unlocked: 625140335 -> 625142448, native 625142448
[   44.791343] ata2.01: ATA-7: ST3320620A, 3.AAC, max UDMA/100
[   44.791349] ata2.01: 625142448 sectors, multi 16: LBA48 
[B][COLOR="Red"][   44.791378] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   44.791386] ata2.01: simplex DMA is claimed by other device, disabling DMA[/COLOR][/B]
[   44.834537] ata2.00: configured for PIO4
[   44.877493] ata2.01: configured for PIO4
[   44.877737] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        8.01 PQ: 0 ANSI: 5
[   44.878029] scsi 0:0:1:0: Direct-Access     ATA      ST3160023A       8.01 PQ: 0 ANSI: 5
[   44.878356] scsi 1:0:0:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
[   44.879201] scsi 1:0:1:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
[   44.879645] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 19 (level, low) -> IRQ 17
[   45.128865] e1000: 0000:01:04.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:02:b3:52:73:a4
[   45.156273] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   45.212047] Driver 'sd' needs updating - please use bus_type methods
[   45.212204] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   45.212232] sd 0:0:0:0: [sda] Write Protect is off
[   45.212238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   45.212279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.212377] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   45.212402] sd 0:0:0:0: [sda] Write Protect is off
[   45.212407] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   45.212445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.212454]  sda: sda1 sda2 < sda5 >
[   45.254254] sd 0:0:0:0: [sda] Attached SCSI disk
[   45.254394] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   45.254421] sd 0:0:1:0: [sdb] Write Protect is off
[   45.254426] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   45.254473] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.254580] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   45.254604] sd 0:0:1:0: [sdb] Write Protect is off
[   45.254609] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   45.254664] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.254672]  sdb: sdb1
[   45.263044] sd 0:0:1:0: [sdb] Attached SCSI disk
[   45.263159] sd 1:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   45.263183] sd 1:0:0:0: [sdc] Write Protect is off
[   45.263188] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   45.263229] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.263326] sd 1:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   45.263351] sd 1:0:0:0: [sdc] Write Protect is off
[   45.263355] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   45.263408] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.263415]  sdc: sdc1
[   45.283578] sd 1:0:0:0: [sdc] Attached SCSI disk
[   45.283771] sd 1:0:1:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   45.283834] sd 1:0:1:0: [sdd] Write Protect is off
[   45.283843] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   45.283915] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.284073] sd 1:0:1:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   45.284101] sd 1:0:1:0: [sdd] Write Protect is off
[   45.284105] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   45.284149] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.284155]  sdd: sdd1
[   45.309001] sd 1:0:1:0: [sdd] Attached SCSI disk
[   45.319594] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   45.319637] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   45.319675] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   45.319713] sd 1:0:1:0: Attached scsi generic sg3 type 0
[   51.270484] kjournald starting.  Commit interval 5 seconds
[   51.270501] EXT3-fs: mounted filesystem with ordered data mode.
[   59.622098] Linux agpgart interface v0.102
[   59.945600] scb2_flash: warning - can't reserve rom window, continuing
[   60.062274] CFI: Found no SCB2 BIOS Flash device at location zero
[   60.062282] scb2_flash: flash probe failed!
[   60.294203] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   60.689246] input: Power Button (FF) as /devices/virtual/input/input2
[   60.708564] ACPI: Power Button (FF) [PWRF]
[   60.708756] input: Sleep Button (CM) as /devices/virtual/input/input3
[   60.740096] ACPI: Sleep Button (CM) [SLPB]
[   60.740304] input: Power Button (CM) as /devices/virtual/input/input4
[   60.764056] ACPI: Power Button (CM) [PWRB]
[   62.014290] e1000: eth1: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   62.833070] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   63.399839] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   63.474820] parport_pc 00:0b: reported by Plug and Play ACPI
[   63.474961] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   63.730892] NET: Registered protocol family 10
[   63.731596] lo: Disabled Privacy Extensions
[   66.409355] loop: module loaded
[   66.445823] lp0: using parport0 (interrupt-driven).
[   66.615834] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   66.926679] EXT3 FS on sda1, internal journal
[   74.147886] eth1: no IPv6 routers present
[  132.507476] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[  132.507498] ReiserFS: sdb1: using ordered data mode
[  132.513390] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  132.514453] ReiserFS: sdb1: checking transaction log (sdb1)
[  132.575029] ReiserFS: sdb1: Using r5 hash to sort names
[  132.611302] ReiserFS: sdc1: found reiserfs format "3.6" with standard journal
[  132.611327] ReiserFS: sdc1: using ordered data mode
[  132.615120] ReiserFS: sdc1: journal params: device sdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  132.616268] ReiserFS: sdc1: checking transaction log (sdc1)
[  132.630439] ReiserFS: sdc1: Using r5 hash to sort names
[  132.644540] ReiserFS: sdd1: found reiserfs format "3.6" with standard journal
[  132.644567] ReiserFS: sdd1: using ordered data mode
[  132.650906] ReiserFS: sdd1: journal params: device sdd1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  132.652225] ReiserFS: sdd1: checking transaction log (sdd1)
[  132.666551] ReiserFS: sdd1: Using r5 hash to sort names
[  133.392104] ip_tables: (C) 2000-2006 Netfilter Core Team
[  135.229135] No dock devices found.
[  140.944374] apm: BIOS not found.
[  143.365432] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by jspking on 2008-05-22
Does anybody have any idea????

Please Helpppppppppppppppp.

---

### Post by Yellow Pasque on 2008-05-22
It looks like your hardware is either incapable of DMA on IDE1 or not configured for it in the BIOS.

---

### Post by jspking on 2008-05-23
Sooo, I tested my server with windows XP on Same Hdd connection just before.

the result from hdtune was really nice.  (76MB/s)

there was no problem with the hdd which was really slow on Ubuntu.


I don't think Mother board causes this situation.




Any Idea???? 

thanks.

---

