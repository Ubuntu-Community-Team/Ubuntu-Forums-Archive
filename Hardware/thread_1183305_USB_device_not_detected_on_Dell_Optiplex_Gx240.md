---
title: "USB device not detected on Dell Optiplex Gx240"
date: 2009-06-09
forum: Hardware
---

### Post by lufte on 2009-06-09
Hi everyone, this is my first thread and, honestly, the reason I joined the forum. I've searched other forums in my language (spanish) for a solution with no success, so I'll now  give it a try in english forums :p

Okay, let's get it started. The problem is actually very simple: I can't get my Xubuntu to detect my cellphone, which should be detected as a generic USB storage device, it does not need any special drivers. But this is the real mistery: I can mount the cellphone in my PC when using Windows (XP, 2000, whatever) and my cellphone gets detected automatically on any other PC using Linux (I've tried it on Kubuntu, Ubuntu, Fedora, etc). I'm really confused, the cellphone seems to work on Linux but not when using Linux on my computer, and it also works on Windows with no problem in my computer. I've also tried other distributions on my computer to make sure with the same results.

You'll be wandering exactly why can't I mount the cellphone, and this is why: the cellphone just won't be detected. I plug it in and nothing happens. The lsusb command shows absolutely nothing. The only way I could make it work was pluggin it before booting Linux (in the GRUB menu for example) but this only works sometimes. 

I've tried to compile all the possible information to make it esay to you people to understand what's going on, here it goes:

OS: Xubuntu 8.04 (I've tried other versions so this makes no difference)
Computer: [COLOR=Blue][Dell Optiplex GX240]("http://support.dell.com/support/edocs/systems/opgx240/en/sm/index.htm")[/COLOR] 
This is the lshw output:
```

javier-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.2
          size: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 78
                serial: 00:08:74:0a:39:26
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=10.0.0.12 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

```Cellphone: [COLOR=Blue][Alcatel 801]("http://www.gsmarena.com/alcatel_ot_e801-1462.php")[/COLOR]

This is the device information given by GParted:
```

Model: VIMICRO U-disk Bridge
Size: 949.15 MiB
Path: /dev/sdc
DiskLabelType:  loop
Heads:        255
Sectors/Track:    63
Cylinders:    121
Total Sectors:    1943865

```This is the device information given by Hardinfo:
```

Device Information
Model: VIMICRO U-disk Bridge
Vendor: VIMICRO U-disk Bridge (null)
Type:    Disk
Revision: 1.00
SCSI Controller
Controller    scsi2
Channel        0
ID        0
LUN        0

```This is the lsusb output:
```

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 064: ID 0ac8:9680 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000 

```This is the dmesg (which I don't really know what it does :S) output after booting Xubuntu with the cellphone previously plugged in:
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff77000 (usable)
[    0.000000]  BIOS-e820: 000000001ff77000 - 000000001ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff79000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130935) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130935
[    0.000000]   HighMem    130935 ->   130935
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130935
[    0.000000] On node 0 totalpages: 130935
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125849 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FD560 checksum 0
[    0.000000] ACPI: RSDP 000FD560, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD574, 0034 (r1 DELL    GX240          8 ASL        61)
[    0.000000] ACPI: FACP 000FD5A8, 0074 (r1 DELL    GX240          8 ASL        61)
[    0.000000] ACPI: DSDT FFFE3C22, 2393 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF77000, 0040
[    0.000000] ACPI: SSDT FFFE5FB5, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD61C, 005C (r1 DELL    GX240          8 ASL        61)
[    0.000000] ACPI: BOOT 000FD678, 0028 (r1 DELL    GX240          8 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129913
[    0.000000] Kernel command line: root=UUID=d788dad7-18b6-4b00-a547-e70458d4f7d1 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1695.112 MHz processor.
[   51.674038] Console: colour VGA+ 80x25
[   51.674046] console [tty0] enabled
[   51.674684] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   51.675357] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   51.697193] Memory: 506916k/523740k available (2157k kernel code, 16316k reserved, 998k data, 364k init, 0k highmem)
[   51.697207] virtual kernel memory layout:
[   51.697209]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   51.697210]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   51.697212]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   51.697214]     lowmem  : 0xc0000000 - 0xdff77000   ( 511 MB)
[   51.697216]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   51.697217]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   51.697219]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   51.697224] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   51.697291] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   51.777310] Calibrating delay using timer specific routine.. 3394.07 BogoMIPS (lpj=6788142)
[   51.777355] Security Framework initialized
[   51.777367] SELinux:  Disabled at boot.
[   51.777392] AppArmor: AppArmor initialized
[   51.777399] Failure registering capabilities with primary security module.
[   51.777414] Mount-cache hash table entries: 512
[   51.777661] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   51.777684] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   51.777688] CPU: L2 cache: 256K
[   51.777693] CPU: Hyper-Threading is disabled
[   51.777697] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[   51.777718] Compat vDSO mapped to ffffe000.
[   51.777743] Checking 'hlt' instruction... OK.
[   51.793951] SMP alternatives: switching to UP code
[   51.796685] Freeing SMP alternatives: 11k freed
[   51.796940] Early unpacking initramfs... done
[   52.363231] ACPI: Core revision 20070126
[   52.375418] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   52.399386] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   52.399448] Total of 1 processors activated (3394.07 BogoMIPS).
[   52.399604] ENABLING IO-APIC IRQs
[   52.399811] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   52.545295] Brought up 1 CPUs
[   52.545339] CPU0 attaching sched-domain:
[   52.545344]  domain 0: span 01
[   52.545348]   groups: 01
[   52.545740] net_namespace: 64 bytes
[   52.545762] Booting paravirtualized kernel on bare hardware
[   52.546810] Time: 15:57:28  Date: 06/05/09
[   52.546874] NET: Registered protocol family 16
[   52.547322] EISA bus registered
[   52.547369] ACPI: bus type pci registered
[   52.573254] PCI: PCI BIOS revision 2.10 entry at 0xfbe2e, last bus=2
[   52.573260] PCI: Using configuration type 1
[   52.573262] Setting up standard PCI resources
[   52.576441] ACPI: EC: Look up EC in DSDT
[   52.600850] ACPI: Interpreter enabled
[   52.600858] ACPI: (supports S0 S1 S3 S4 S5)
[   52.600889] ACPI: Using IOAPIC for interrupt routing
[   52.630589] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   52.630928] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   52.630934] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   52.631633] PCI: Transparent bridge - 0000:00:1e.0
[   52.631673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   52.632217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   52.652466] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   52.652830] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   52.653231] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   52.653591] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   52.653947] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   52.654300] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   52.654655] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   52.655015] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   52.655391] Linux Plug and Play Support v0.97 (c) Adam Belay
[   52.655460] pnp: PnP ACPI init
[   52.655481] ACPI: bus type pnp registered
[   52.683036] pnp: PnP ACPI: found 13 devices
[   52.683045] ACPI: ACPI bus type pnp unregistered
[   52.683055] PnPBIOS: Disabled by ACPI PNP
[   52.683556] PCI: Using ACPI for IRQ routing
[   52.683565] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   52.705192] NET: Registered protocol family 8
[   52.705197] NET: Registered protocol family 20
[   52.705357] AppArmor: AppArmor Filesystem Enabled
[   52.709177] Time: tsc clocksource has been installed.
[   52.717273] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   52.717278] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[   52.717283] system 00:00: iomem range 0x1000000-0x1ff76fff could not be reserved
[   52.717287] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   52.717293] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   52.717298] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   52.717302] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   52.717307] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[   52.717332] system 00:0c: ioport range 0x800-0x85f has been reserved
[   52.717336] system 00:0c: ioport range 0xc00-0xc7f has been reserved
[   52.717341] system 00:0c: ioport range 0x860-0x8ff could not be reserved
[   52.748172] PCI: Bridge: 0000:00:01.0
[   52.748176]   IO window: disabled.
[   52.748184]   MEM window: fb000000-fdffffff
[   52.748189]   PREFETCH window: e0000000-efffffff
[   52.748197] PCI: Bridge: 0000:00:1e.0
[   52.748202]   IO window: e000-efff
[   52.748210]   MEM window: fe100000-fe2fffff
[   52.748215]   PREFETCH window: disabled.
[   52.748240] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   52.748270] NET: Registered protocol family 2
[   52.785332] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   52.785771] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   52.785962] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   52.786177] TCP: Hash tables configured (established 16384 bind 16384)
[   52.786183] TCP reno registered
[   52.797552] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   53.309740]  it is
[   53.898844] Freeing initrd memory: 7704k freed
[   53.899225] Simple Boot Flag at 0x7a set to 0x1
[   53.900050] audit: initializing netlink socket (disabled)
[   53.900081] audit(1244217449.096:1): initialized
[   53.903926] VFS: Disk quotas dquot_6.5.1
[   53.904101] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   53.904425] io scheduler noop registered
[   53.904430] io scheduler anticipatory registered
[   53.904433] io scheduler deadline registered
[   53.904463] io scheduler cfq registered (default)
[   53.904527] Boot video device is 0000:01:00.0
[   53.905134] isapnp: Scanning for PnP cards...
[   54.259538] isapnp: No Plug & Play device found
[   54.364151] Real Time Clock Driver v1.12ac
[   54.364326] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.364513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.364895] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.366544] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.367415] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.369067] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.369208] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   54.369423] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   54.372114] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.372123] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.381096] mice: PS/2 mouse device common for all mice
[   54.381352] EISA: Probing bus 0 at eisa.0
[   54.381396] EISA: Detected 0 cards.
[   54.381403] cpuidle: using governor ladder
[   54.381407] cpuidle: using governor menu
[   54.381594] NET: Registered protocol family 1
[   54.381653] Using IPI No-Shortcut mode
[   54.381719] registered taskstats version 1
[   54.381870]   Magic number: 13:407:992
[   54.381888]   hash matches device ttyd5
[   54.382062] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   54.382065] EDD information not available.
[   54.382963] Freeing unused kernel memory: 364k freed
[   54.420870] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   55.831729] fuse init (API version 7.9)
[   57.032421] usbcore: registered new interface driver usbfs
[   57.032466] usbcore: registered new interface driver hub
[   57.046447] SCSI subsystem initialized
[   57.084406] usbcore: registered new device driver usb
[   57.156453] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 16
[   57.156472] 3c59x: Donald Becker and others.
[   57.156482] 0000:02:0c.0: 3Com PCI 3c905C Tornado at e083ec00.
[   57.186346] libata version 3.00 loaded.
[   57.196641] USB Universal Host Controller Interface driver v3.0
[   57.196793] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 17
[   57.196814] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   57.196820] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   57.197484] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   57.197537] uhci_hcd 0000:00:1f.2: irq 17, io base 0x0000ff80
[   57.197849] usb usb1: configuration #1 chosen from 1 choice
[   57.197893] hub 1-0:1.0: USB hub found
[   57.197907] hub 1-0:1.0: 2 ports detected
[   57.292430] Floppy drive(s): fd0 is 1.44M
[   57.300549] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 18
[   57.300572] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   57.300578] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   57.300625] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   57.300670] uhci_hcd 0000:00:1f.4: irq 18, io base 0x0000ff60
[   57.300910] usb usb2: configuration #1 chosen from 1 choice
[   57.300955] hub 2-0:1.0: USB hub found
[   57.300966] hub 2-0:1.0: 2 ports detected
[   57.314395] FDC 0 is a post-1991 82077
[   57.404667] ata_piix 0000:00:1f.1: version 2.12
[   57.404782] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   57.412276] scsi0 : ata_piix
[   57.419529] scsi1 : ata_piix
[   57.419645] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   57.419650] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   57.596523] ata1.00: HPA unlocked: 78125000 -> 78165360, native 78165360
[   57.596535] ata1.00: ATA-5: WDC WD400BB-75CAA0, 16.06V16, max UDMA/100
[   57.596540] ata1.00: 78165360 sectors, multi 8: LBA 
[   57.597536] ata1.01: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
[   57.597543] ata1.01: 78165360 sectors, multi 8: LBA 
[   57.613411] ata1.00: configured for UDMA/100
[   57.629409] ata1.01: configured for UDMA/100
[   57.940579] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-616T, F308, max UDMA/33
[   58.104558] ata2.00: configured for UDMA/33
[   58.104810] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-75CA 16.0 PQ: 0 ANSI: 5
[   58.105039] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
[   58.105665] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F308 PQ: 0 ANSI: 5
[   58.751883] Driver 'sd' needs updating - please use bus_type methods
[   58.754288] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   58.754317] sd 0:0:0:0: [sda] Write Protect is off
[   58.754321] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   58.754357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.754477] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   58.754497] sd 0:0:0:0: [sda] Write Protect is off
[   58.754501] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   58.754534] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.754544]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   58.768111]  sda1 sda2 < sda5 sda6 sda7 >
[   58.821847] sd 0:0:0:0: [sda] Attached SCSI disk
[   58.824015] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   58.824045] sd 0:0:1:0: [sdb] Write Protect is off
[   58.824049] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   58.824085] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.824200] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   58.824220] sd 0:0:1:0: [sdb] Write Protect is off
[   58.824224] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   58.824257] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.824266]  sdb: sdb2 < sdb5 >
[   58.841853] sd 0:0:1:0: [sdb] Attached SCSI disk
[   58.863376] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   58.863418] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   58.863449] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   58.865335] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   58.865346] Uniform CD-ROM driver Revision: 3.20
[   58.865455] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   59.564934] Attempting manual resume
[   59.564943] swsusp: Resume From Partition 8:7
[   59.564946] PM: Checking swsusp image.
[   59.565229] PM: Resume from disk failed.
[   59.626673] kjournald starting.  Commit interval 5 seconds
[   59.626708] EXT3-fs: mounted filesystem with ordered data mode.
[   66.086509] usb 1-2: new full speed USB device using uhci_hcd and address 36
[   66.626306] usb 1-2: device not accepting address 36, error -71
[   68.750026] Linux agpgart interface v0.102
[   68.814192] agpgart: Detected an Intel 845G Chipset.
[   68.818845] agpgart: AGP aperture is 64M @ 0xf0000000
[   68.882038] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   68.935377] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   69.065856] intel_rng: FWH not detected
[   69.205880] iTCO_vendor_support: vendor-support=0
[   69.252399] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   69.252699] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0860)
[   69.252787] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   69.326311] input: Power Button (FF) as /devices/virtual/input/input2
[   69.341783] ACPI: Power Button (FF) [PWRF]
[   69.342036] input: Power Button (CM) as /devices/virtual/input/input3
[   69.357788] ACPI: Power Button (CM) [VBTN]
[   71.775277] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   72.530186] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   72.639583] nvidia: module license 'NVIDIA' taints kernel.
[   73.017756] parport_pc 00:0b: reported by Plug and Play ACPI
[   73.017822] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   73.028575] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   73.197330] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 19
[   73.197362] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   73.816905] intel8x0_measure_ac97_clock: measured 55969 usecs
[   73.816915] intel8x0: clocking to 41146
[   73.818523] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   73.819273] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   74.033018] usb 1-2: new full speed USB device using uhci_hcd and address 65
[   74.176812] usb 1-2: device descriptor read/64, error -71
[   74.804699] usb 1-2: device not accepting address 65, error -71
[   76.052368] usb 1-2: new full speed USB device using uhci_hcd and address 70
[   76.580332] usb 1-2: device not accepting address 70, error -71
[   76.647311] lp0: using parport0 (interrupt-driven).
[   76.752770] Adding 746980k swap on /dev/sda7.  Priority:-1 extents:1 across:746980k
[   77.345536] EXT3 FS on sda5, internal journal
[   86.410283] usb 1-2: new full speed USB device using uhci_hcd and address 110
[   88.145897] usb 1-2: new full speed USB device using uhci_hcd and address 116
[  104.262620] usb 1-2: new full speed USB device using uhci_hcd and address 54
[  104.382556] usb 1-2: device descriptor read/64, error -71
[  105.010417] usb 1-2: device not accepting address 54, error -71
[  106.994028] usb 1-2: new full speed USB device using uhci_hcd and address 62
[  113.188753] usb 1-2: new full speed USB device using uhci_hcd and address 86
[  122.862773] usb 1-2: new full speed USB device using uhci_hcd and address 124
[  125.587191] usb 1-2: new full speed USB device using uhci_hcd and address 8
[  126.110085] usb 1-2: device not accepting address 8, error -71
[  137.239800] usb 1-2: new full speed USB device using uhci_hcd and address 53
[  137.359776] usb 1-2: device descriptor read/64, error -71
[  140.711086] usb 1-2: new full speed USB device using uhci_hcd and address 65
[  158.319490] usb 1-2: new full speed USB device using uhci_hcd and address 9
[  160.798945] usb 1-2: new full speed USB device using uhci_hcd and address 18
[  163.026470] usb 1-2: new full speed USB device using uhci_hcd and address 26
[  163.550450] usb 1-2: device not accepting address 26, error -71
[  163.805310] kjournald starting.  Commit interval 5 seconds
[  163.805533] EXT3 FS on sda6, internal journal
[  163.805542] EXT3-fs: mounted filesystem with ordered data mode.
[  164.660238] ip_tables: (C) 2000-2006 Netfilter Core Team
[  164.762957] usb 1-2: new full speed USB device using uhci_hcd and address 31
[  165.286003] usb 1-2: device not accepting address 31, error -71
[  166.497778] usb 1-2: new full speed USB device using uhci_hcd and address 36
[  166.715183] No dock devices found.
[  167.025684] usb 1-2: device not accepting address 36, error -71
[  168.554020] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  168.554032] apm: overridden by ACPI.
[  168.724181] ppdev: user-space parallel port driver
[  168.952468] audit(1244228364.470:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5659 profile="/usr/sbin/cupsd" namespace="default"
[  169.174267] RPC: Registered udp transport module.
[  169.174277] RPC: Registered tcp transport module.
[  169.243015] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  169.353746] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  169.365017] NFSD: starting 90-second grace period
[  171.718214] eth0:  setting full-duplex.
[  173.192402] usb 1-2: new full speed USB device using uhci_hcd and address 61
[  174.493656] usb 1-2: new full speed USB device using uhci_hcd and address 64
[  174.496315] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  174.496343] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  174.496369] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  174.613368] Bluetooth: Core ver 2.11
[  174.614394] NET: Registered protocol family 31
[  174.614400] Bluetooth: HCI device and connection manager initialized
[  174.614407] Bluetooth: HCI socket layer initialized
[  174.644161] Bluetooth: L2CAP ver 2.9
[  174.644166] Bluetooth: L2CAP socket layer initialized
[  174.678789] usb 1-2: configuration #1 chosen from 1 choice
[  174.757281] Bluetooth: RFCOMM socket layer initialized
[  174.757316] Bluetooth: RFCOMM TTY layer initialized
[  174.757319] Bluetooth: RFCOMM ver 1.8
[  174.967006] usbcore: registered new interface driver libusual
[  175.026225] Initializing USB Mass Storage driver...
[  175.183704] scsi2 : SCSI emulation for USB Mass Storage devices
[  175.190253] usbcore: registered new interface driver usb-storage
[  175.190268] USB Mass Storage support registered.
[  175.192600] usb-storage: device found at 64
[  175.192608] usb-storage: waiting for device to settle before scanning
[  175.325334] NET: Registered protocol family 17
[  177.109322] NET: Registered protocol family 10
[  177.110874] lo: Disabled Privacy Extensions
[  180.192561] usb-storage: device scan complete
[  180.199572] scsi 2:0:0:0: Direct-Access     VIMICRO  U-disk Bridge    1.00 PQ: 0 ANSI: 0 CCS
[  180.224487] sd 2:0:0:0: [sdc] 1950720 512-byte hardware sectors (999 MB)
[  180.228549] sd 2:0:0:0: [sdc] Write Protect is off
[  180.228564] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  180.228570] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  180.251504] sd 2:0:0:0: [sdc] 1950720 512-byte hardware sectors (999 MB)
[  180.255487] sd 2:0:0:0: [sdc] Write Protect is off
[  180.255498] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  180.255503] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  180.255520]  sdc: unknown partition table
[  180.299573] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  180.299666] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  192.108302] eth0: no IPv6 routers present
[  220.288412] end_request: I/O error, dev fd0, sector 0
[  220.312433] end_request: I/O error, dev fd0, sector 0

```
That's all. Thanks for reading.

---

