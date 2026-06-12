---
title: "W83627hf Watchdog"
date: 2008-08-26
forum: Hardware
---

### Post by SteelWo1f on 2008-08-26
Hi

I have a SuperMicro 5015M-MT server and I'm trying to get the Winbond W83627HF watchdog working. It seems to be compiled in as a module but the module is not loading on startup. There is however an iTCO_wdt module being loaded and I think that is whats creating the /dev/watchdog file. I also think thats whats causing this error:

root@FlashUbuntu:~# modprobe -a w83627hf_wdt
WARNING: Error inserting w83627hf_wdt (/lib/modules/2.6.24-16-server/kernel/drivers/watchdog/w83627hf_wdt.ko): Device or resource busy

On a related note, when I `apt-get install watchdog`, it says 

(Reading database ... 36699 files and directories currently installed.)
Unpacking watchdog (from .../watchdog_5.4-2_i386.deb) ...
Setting up watchdog (5.4-2) ...
udev active, devices will be created in /dev/.static/dev/
udev active, devices will be created in /dev/.static/dev/

What exactly is /dev/.static/dev/? My real question is how do I get the Winbond watchdog to work?

One final note: w83627hf_wdt is blacklisted in /etc/modprobe.d/blacklist-watchdog. Why is that? Even if I unblacklist it and blacklist the iTCO_wdt, it still doesn't work.

Thanks 





Dmesg:

 Initializing cgroup subsys cpuset
 Initializing cgroup subsys cpu
 Linux version 2.6.24-16-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:58:00 UTC 2008 (Ubuntu 2.6.24-16.30-server)
 BIOS-provided physical RAM map:
  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
  BIOS-e820: 000000007fee0000 - 000000007fee9000 (ACPI data)
  BIOS-e820: 000000007fee9000 - 000000007ff00000 (ACPI NVS)
  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
 1150MB HIGHMEM available.
 896MB LOWMEM available.
 found SMP MP-table at 000f5ed0
 NX (Execute Disable) protection: active
 Entering add_active_range(0, 0, 524000) 0 entries of 256 used
 Zone PFN ranges:
   DMA             0 ->     4096
   Normal       4096 ->   229376
   HighMem    229376 ->   524000
 Movable zone start PFN for each node
 active PFN ranges
     0:        0 ->   524000
 On node 0 totalpages: 524000
   DMA zone: 32 pages used for memmap
   DMA zone: 0 pages reserved
   DMA zone: 4064 pages, LIFO batch:0
   Normal zone: 1760 pages used for memmap
   Normal zone: 223520 pages, LIFO batch:31
   HighMem zone: 2301 pages used for memmap
   HighMem zone: 292323 pages, LIFO batch:31
   Movable zone: 0 pages used for memmap
 DMI present.
 ACPI: RSDP signature @ 0xC00F5E50 checksum 0
 ACPI: RSDP 000F5E50, 0014 (r0 PTLTD )
 ACPI: RSDT 7FEE25B4, 003C (r1 PTLTD    RSDT    6040000  LTP        0)
 ACPI: FACP 7FEE8E51, 0074 (r1 INTEL            6040000 PTL         3)
 ACPI: DSDT 7FEE39DC, 5475 (r1  INTEL GLENWOOD  6040000 MSFT  100000E)
 ACPI: FACS 7FEE9FC0, 0040
 ACPI: MCFG 7FEE8EC5, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
 ACPI: APIC 7FEE8F01, 0074 (r1 PTLTD  	 APIC    6040000  LTP        0)
 ACPI: BOOT 7FEE8F75, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
 ACPI: ASF! 7FEE8F9D, 0063 (r32   CETP     CETP  6040000 PTL         1)
 ACPI: SSDT 7FEE25F0, 13EC (r1  PmRef    CpuPm     3000 INTL 20050228)
 ACPI: PM-Timer IO Port: 0x1008
 ACPI: Local APIC address 0xfee00000
 enabled)
 Processor #0 6:15 APIC version 20
 enabled)
 Processor #1 6:15 APIC version 20
)
)
)
: apic_id 2, version 32, address 0xfec00000, GSI 0-23
)
: apic_id 3, version 32, address 0xfec10000, GSI 24-47
 ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
 ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
 ACPI: IRQ0 used by override.
 ACPI: IRQ2 used by override.
 ACPI: IRQ9 used by override.
 Enabling APIC mode:  Flat.  Using 2 I/O APICs
 Using ACPI (MADT) for SMP configuration information
 Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
 swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
 swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
 swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
 Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
 Kernel command line: root=UUID=8ff352dc-38e4-401a-83b1-5948cf3d1d42 ro quiet splash
 mapped APIC to ffffb000 (fee00000)
 mapped IOAPIC to ffffa000 (fec00000)
 mapped IOAPIC to ffff9000 (fec10000)
 Enabling fast FPU save and restore... done.
 Enabling unmasked SIMD FPU exception support... done.
 Initializing CPU#0
 PID hash table entries: 4096 (order: 12, 16384 bytes)
 Detected 2128.131 MHz processor.
 Console: colour VGA+ 80x25
 enabled
 Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
 Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
 Memory: 2066048k/2096000k available (2255k kernel code, 28672k reserved, 1032k data, 384k init, 1178496k highmem)
 virtual kernel memory layout:
     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
       .init : 0xc043c000 - 0xc049c000   ( 384 kB)
       .data : 0xc0333e95 - 0xc0435fe4   (1032 kB)
       .text : 0xc0100000 - 0xc0333e95   (2255 kB)
 Checking if this processor honours the WP bit even in supervisor mode... Ok.
 SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
 Calibrating delay using timer specific routine.. 4258.67 BogoMIPS (lpj=21293388)
 Security Framework initialized
 SELinux:  Disabled at boot.
 AppArmor: AppArmor initialized
 Failure registering capabilities with primary security module.
 Mount-cache hash table entries: 512
 Initializing cgroup subsys ns
 Initializing cgroup subsys cpuacct
 CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
 monitor/mwait feature present.
 using mwait in idle threads.
 CPU: L1 I cache: 32K, L1 D cache: 32K
 CPU: L2 cache: 2048K
 CPU: Physical Processor ID: 0
 CPU: Processor Core ID: 0
 CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
 Compat vDSO mapped to ffffe000.
 Checking 'hlt' instruction... OK.
 SMP alternatives: switching to UP code
 Early unpacking initramfs... done
 ACPI: Core revision 20070126
 ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
 CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
 SMP alternatives: switching to SMP code
 Booting processor 1/1 eip 3000
 Initializing CPU#1
 Calibrating delay using timer specific routine.. 4256.12 BogoMIPS (lpj=21280609)
 CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
 monitor/mwait feature present.
 CPU: L1 I cache: 32K, L1 D cache: 32K
 CPU: L2 cache: 2048K
 CPU: Physical Processor ID: 0
 CPU: Processor Core ID: 1
 CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
 CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
 Total of 2 processors activated (8514.79 BogoMIPS).
 ENABLING IO-APIC IRQs
 ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
: passed.
 Brought up 2 CPUs
 CPU0 attaching sched-domain:
  domain 0: span 03
   groups: 01 02
 CPU1 attaching sched-domain:
  domain 0: span 03
   groups: 02 01
 net_namespace: 64 bytes
 Booting paravirtualized kernel on bare hardware
 Time: 14:44:26  Date: 08/26/08
 NET: Registered protocol family 16
 EISA bus registered
 ACPI: bus type pci registered
 PCI: PCI BIOS revision 2.10 entry at 0xfd70e, last bus=15
 PCI: Using configuration type 1
 Setting up standard PCI resources
 ACPI: EC: Look up EC in DSDT
 ACPI: Interpreter enabled
 ACPI: (supports S0 S1 S4 S5)
 ACPI: Using IOAPIC for interrupt routing
 (0000:00)
 Force enabled HPET at base address 0xfed00000
 PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
 PCI quirk: region 1180-11bf claimed by ICH6 GPIO
 PCI: PXH quirk detected, disabling MSI for SHPC device
 PCI: Transparent bridge - 0000:00:1e.0







 (IRQs 3 10 *11 14 15)
 (IRQs 3 10 *11 14 15)
 (IRQs 3 10 11 14 15) *5
 (IRQs 3 10 *11 14 15)
 (IRQs 3 10 11 14 15) *0, disabled.
 (IRQs 3 10 11 14 15) *0, disabled.
 (IRQs 3 10 11 14 15) *0, disabled.
 (IRQs 3 *10 11 14 15)
 Linux Plug and Play Support v0.97 (c) Adam Belay
 pnp: PnP ACPI init
 ACPI: bus type pnp registered
 pnp: PnP ACPI: found 13 devices
 ACPI: ACPI bus type pnp unregistered
 PnPBIOS: Disabled by ACPI PNP
 PCI: Using ACPI for IRQ routing
 PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
 NET: Registered protocol family 8
 NET: Registered protocol family 20
 NetLabel: Initializing
 NetLabel:  domain hash size = 128
 NetLabel:  protocols = UNLABELED CIPSOv4
 NetLabel:  unlabeled traffic allowed by default
 hpet clockevent registered
 hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
 hpet0: 3 64-bit timers, 14318180 Hz
 AppArmor: AppArmor Filesystem Enabled
 Time: tsc clocksource has been installed.
 system 00:01: ioport range 0x295-0x296 has been reserved
 system 00:01: ioport range 0x800-0x83f has been reserved
 system 00:01: ioport range 0x900-0x90f has been reserved
 system 00:01: ioport range 0x1000-0x107f has been reserved
 system 00:01: ioport range 0x1180-0x11bf has been reserved
 system 00:01: ioport range 0x4d0-0x4d1 has been reserved
 system 00:01: ioport range 0xfe00-0xfe00 has been reserved
 system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
 system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
 system 00:01: iomem range 0xfed18000-0xfed1bfff has been reserved
 system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
 system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
 system 00:01: iomem range 0xfef00000-0xfeffffff has been reserved
 PCI: Bridge: 0000:00:01.0
   IO window: disabled.
   MEM window: disabled.
   PREFETCH window: disabled.
 PCI: Bridge: 0000:09:00.0
   IO window: 4000-4fff
   MEM window: e0200000-e02fffff
   PREFETCH window: 88000000-880fffff
 PCI: Bridge: 0000:00:1c.0
   IO window: 4000-4fff
   MEM window: e0100000-e02fffff
   PREFETCH window: 88000000-880fffff
 PCI: Bridge: 0000:00:1c.4
   IO window: 5000-5fff
   MEM window: e0300000-e03fffff
   PREFETCH window: disabled.
 PCI: Bridge: 0000:00:1c.5
   IO window: 6000-6fff
   MEM window: e0400000-e04fffff
   PREFETCH window: disabled.
 PCI: Bridge: 0000:00:1e.0
   IO window: 7000-7fff
   MEM window: e0500000-e05fffff
   PREFETCH window: e8000000-efffffff
 -> GSI 16 (level, low) -> IRQ 16
 PCI: Setting latency timer of device 0000:00:01.0 to 64
 -> GSI 17 (level, low) -> IRQ 17
 PCI: Setting latency timer of device 0000:00:1c.0 to 64
 PCI: Setting latency timer of device 0000:09:00.0 to 64
 -> GSI 17 (level, low) -> IRQ 17
 PCI: Setting latency timer of device 0000:00:1c.4 to 64
 -> GSI 16 (level, low) -> IRQ 16
 PCI: Setting latency timer of device 0000:00:1c.5 to 64
 PCI: Setting latency timer of device 0000:00:1e.0 to 64
 NET: Registered protocol family 2
 IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
 TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
 TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
 TCP: Hash tables configured (established 131072 bind 65536)
 TCP reno registered
 checking if image is initramfs... it is
 Switched to high resolution mode on CPU 1
 Switched to high resolution mode on CPU 0
 Freeing initrd memory: 7134k freed
 Simple Boot Flag at 0x38 set to 0x1
 audit: initializing netlink socket (disabled)
 audit(1219761866.530:1): initialized
 highmem bounce pool size: 64 pages
 Total HugeTLB memory allocated, 0
 VFS: Disk quotas dquot_6.5.1
 Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 io scheduler noop registered
 io scheduler anticipatory registered
 io scheduler deadline registered (default)
 io scheduler cfq registered
 Boot video device is 0000:0f:00.0
 PCI: Setting latency timer of device 0000:00:01.0 to 64
 assign_interrupt_mode Found MSI capability

 PCI: Setting latency timer of device 0000:00:1c.0 to 64
 assign_interrupt_mode Found MSI capability


 PCI: Setting latency timer of device 0000:00:1c.4 to 64
 assign_interrupt_mode Found MSI capability


 PCI: Setting latency timer of device 0000:00:1c.5 to 64
 assign_interrupt_mode Found MSI capability


 isapnp: Scanning for PnP cards...
 isapnp: No Plug & Play device found
 Real Time Clock Driver v1.12ac
 Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
 serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
 input: Macintosh mouse button emulation as /devices/virtual/input/input0
 at 0x60,0x64 irq 1,12
 serio: i8042 KBD port at 0x60,0x64 irq 1
 serio: i8042 AUX port at 0x60,0x64 irq 12
 mice: PS/2 mouse device common for all mice
 EISA: Probing bus 0 at eisa.0
 Cannot allocate resource for EISA slot 1
 Cannot allocate resource for EISA slot 3
 Cannot allocate resource for EISA slot 4
 Cannot allocate resource for EISA slot 5
 Cannot allocate resource for EISA slot 6
 Cannot allocate resource for EISA slot 7
 EISA: Detected 0 cards.
 cpuidle: using governor ladder
 cpuidle: using governor menu
 NET: Registered protocol family 1
 Using IPI No-Shortcut mode
 registered taskstats version 1
   Magic number: 4:136:739
 BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
 Freeing unused kernel memory: 384k freed
 input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
 fuse init (API version 7.9)






 Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
 Copyright (c) 1999-2006 Intel Corporation.
 -> GSI 24 (level, low) -> IRQ 18
 usbcore: registered new interface driver usbfs
 usbcore: registered new interface driver hub
 usbcore: registered new device driver usb
 USB Universal Host Controller Interface driver v3.0
 -> GSI 23 (level, low) -> IRQ 19
 PCI: Setting latency timer of device 0000:00:1d.0 to 64
 uhci_hcd 0000:00:1d.0: UHCI Host Controller
 uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
 uhci_hcd 0000:00:1d.0: irq 19, io base 0x00003000
 usb usb1: configuration #1 chosen from 1 choice
 hub 1-0:1.0: USB hub found
 hub 1-0:1.0: 2 ports detected
 e1000: 0000:0a:01.0: e1000_probe: (PCI:66MHz:32-bit) 00:0e:0c:b6:83:5e
 -> GSI 19 (level, low) -> IRQ 20
 PCI: Setting latency timer of device 0000:00:1d.1 to 64
 uhci_hcd 0000:00:1d.1: UHCI Host Controller
 uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
 uhci_hcd 0000:00:1d.1: irq 20, io base 0x00003020
 usb usb2: configuration #1 chosen from 1 choice
 hub 2-0:1.0: USB hub found
 hub 2-0:1.0: 2 ports detected
 SCSI subsystem initialized
 libata version 3.00 loaded.
 Floppy drive(s): fd0 is 1.44M
 FDC 0 is a post-1991 82077
 -> GSI 18 (level, low) -> IRQ 21
 PCI: Setting latency timer of device 0000:00:1d.2 to 64
 uhci_hcd 0000:00:1d.2: UHCI Host Controller
 uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
 uhci_hcd 0000:00:1d.2: irq 21, io base 0x00003040
 usb usb3: configuration #1 chosen from 1 choice
 hub 3-0:1.0: USB hub found
 hub 3-0:1.0: 2 ports detected
 -> GSI 16 (level, low) -> IRQ 16
 PCI: Setting latency timer of device 0000:00:1d.3 to 64
 uhci_hcd 0000:00:1d.3: UHCI Host Controller
 uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
 uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003060
 usb usb4: configuration #1 chosen from 1 choice
 hub 4-0:1.0: USB hub found
 hub 4-0:1.0: 2 ports detected
 e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
 -> GSI 16 (level, low) -> IRQ 16
 PCI: Setting latency timer of device 0000:0d:00.0 to 64
 e1000: 0000:0d:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:30:48:8a:ca:e2
 e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
 -> GSI 17 (level, low) -> IRQ 17
 PCI: Setting latency timer of device 0000:0e:00.0 to 64
 e1000: 0000:0e:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:30:48:8a:ca:e3
 e1000: eth2: e1000_probe: Intel(R) PRO/1000 Network Connection
 -> GSI 23 (level, low) -> IRQ 19
 PCI: Setting latency timer of device 0000:00:1d.7 to 64
 ehci_hcd 0000:00:1d.7: EHCI Host Controller
 ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
 ehci_hcd 0000:00:1d.7: debug port 1
 PCI: cache line size of 32 is not supported by device 0000:00:1d.7
 ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe0000000
 ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
 usb usb5: configuration #1 chosen from 1 choice
 hub 5-0:1.0: USB hub found
 hub 5-0:1.0: 8 ports detected
 ata_piix 0000:00:1f.2: version 2.12

 -> GSI 19 (level, low) -> IRQ 20
 PCI: Setting latency timer of device 0000:00:1f.2 to 64
 scsi0 : ata_piix
 scsi1 : ata_piix
 ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
 ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
 ata1.00: ATA-6: WDC WD2500JD-00HBC0, 08.02D08, max UDMA/133
 ata1.00: 488397168 sectors, multi 16: LBA48 
 ata1.00: configured for UDMA/133
 ata2.00: ATAPI: CD-224E-N, 1.AA, max UDMA/33
 ata2.01: ATA-5: TRANSCEND, 2.0, max UDMA/66
 ata2.01: 2000880 sectors, multi 1: LBA 
 ata2.01: limited to UDMA/33 due to 40-wire cable
 ata2.00: configured for UDMA/33
 ata2.01: configured for UDMA/33
 scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
 scsi 1:0:0:0: CD-ROM            TEAC     CD-224E-N        1.AA PQ: 0 ANSI: 5
 scsi 1:0:1:0: Direct-Access     ATA      TRANSCEND        2.0  PQ: 0 ANSI: 5
 Driver 'sd' needs updating - please use bus_type methods
 488397168 512-byte hardware sectors (250059 MB)
 Write Protect is off
 Mode Sense: 00 3a 00 00
 Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 488397168 512-byte hardware sectors (250059 MB)
 Write Protect is off
 Mode Sense: 00 3a 00 00
 Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  sda:<4>Driver 'sr' needs updating - please use bus_type methods
  sda1 sda2 < sda5 sda6 >
 Attached SCSI disk
 2000880 512-byte hardware sectors (1024 MB)
 Write Protect is off
 Mode Sense: 00 3a 00 00
 Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
 2000880 512-byte hardware sectors (1024 MB)
 Write Protect is off
 Mode Sense: 00 3a 00 00
 Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
  sdb: sdb4
 Attached SCSI disk
 sd 0:0:0:0: Attached scsi generic sg0 type 0
 sr 1:0:0:0: Attached scsi generic sg1 type 5
 sd 1:0:1:0: Attached scsi generic sg2 type 0
 sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
 Uniform CD-ROM driver Revision: 3.20
 sr 1:0:0:0: Attached scsi CD-ROM sr0
 Attempting manual resume
 swsusp: Resume From Partition 8:6
 PM: Checking swsusp image.
 PM: Resume from disk failed.
 EXT3-fs: INFO: recovery required on readonly filesystem.
 EXT3-fs: write access will be enabled during recovery.
 kjournald starting.  Commit interval 5 seconds
 EXT3-fs: recovery complete.
 EXT3-fs: mounted filesystem with ordered data mode.
 input: PC Speaker as /devices/platform/pcspkr/input/input2
 intel_rng: FWH not detected
 EDAC MC: Ver: 2.1.0 Apr 10 2008
 pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
 EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
 input: Power Button (FF) as /devices/virtual/input/input3

 input: Power Button (CM) as /devices/virtual/input/input4

 input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
 parport_pc 00:0c: reported by Plug and Play ACPI

 e1000: eth1: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
 e1000: eth1: e1000_watchdog: 10/100 speed: disabling TSO
 NET: Registered protocol family 10
 lo: Disabled Privacy Extensions
 loop: module loaded
 lp0: using parport0 (interrupt-driven).
 Adding 5992204k swap on /dev/sda6.  Priority:-1 extents:1 across:5992204k
 EXT3 FS on sdb4, internal journal
 ip_tables: (C) 2000-2006 Netfilter Core Team
 eth1: no IPv6 routers present

---

