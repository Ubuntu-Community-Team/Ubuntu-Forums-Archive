---
title: "Onboard NIC on old Acer TravelMate 720TX not found, also does not show up with lspci!"
date: 2009-03-10
forum: Hardware
---

### Post by otakuj462 on 2009-03-10
Hi all,

This is a strange one. I have an old Acer TravelMate 720TX that I'm refurbishing for a friend. Unfortunately, the onboard ethernet car is not is not being found (drivers not being loaded, ifconfig does not reveal any interfaces other than lo, no link lights). The strange thing is, I cannot find any NIC's with lspci. I believe this NIC worked before when windows 98 was installed, so I believe that this is not a hardware failure. Perhaps I've missed something, though, so I've posted the output of lspci here, along with lsmod and dmesg.

lspci
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:06.0 CardBus bridge: Texas Instruments PCI1251A (rev 01)
00:06.1 CardBus bridge: Texas Instruments PCI1251A (rev 01)
00:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
libusual               27156  1 usb_storage
ipv6                  263972  8 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
apm                    26332  2 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  1 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
joydev                 18368  0 
pcmcia                 43052  0 
snd_nm256              74400  0 
snd_ac97_codec        111652  1 snd_nm256
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_nm256,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  10 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
evdev                  17696  4 
psmouse                45200  0 
serio_raw              13444  0 
shpchp                 37908  0 
i2c_piix4              16144  0 
pcspkr                 10624  0 
intel_agp              33724  1 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pci_hotplug            35236  1 shpchp
agpgart                42184  1 intel_agp
i2c_core               31892  1 i2c_piix4
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ata_piix               24580  2 
libata                177312  3 ata_generic,pata_acpi,ata_piix
uhci_hcd               30736  0 
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
usbcore               148848  4 usb_storage,libusual,uhci_hcd
dock                   16656  1 libata
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

```


dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9c00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000007fffc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007fffc00 - 0000000008000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe9c00 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7ff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 7ff0000 @ 7000-d000
[    0.000000] RAMDISK: 07812000 - 07fdf98d
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP 000F7260, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 07FFFB15, 002C (r1 PTLTD    RSDT          0  LTP        0)
[    0.000000] ACPI: FACP 07FFFB65, 0074 (r1 ACER   720_FACP        0 ASL       3F2)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
[    0.000000] ACPI: DSDT 07FFFB41, 0024 (r1    PTL    BX-TJ        0 MSFT  1000004)
[    0.000000] ACPI: FACS 07FFFFC0, 0040
[    0.000000] ACPI: BOOT 07FFFBD9, 0027 (r1 PTLTD  $SBFTBL$        0  LTP        1)
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 127MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 07ff0000
[    0.000000]   low ram: 00000000 - 07ff0000
[    0.000000]   bootmap 00002000 - 00003000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0007ff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0007812000 - 0007fdf98d]          RAMDISK ==> [0007812000 - 0007fdf98d]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000003000]          BOOTMAP ==> [0000002000 - 0000003000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00007ff0
[    0.000000]   HighMem  0x00007ff0 -> 0x00007ff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00007ff0
[    0.000000] On node 0 totalpages: 32655
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 28404 pages, LIFO batch:7
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01121000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 8000000:f7fe9c00)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32367
[    0.000000] Kernel command line: root=UUID=52aeb15a-402f-478e-b2dc-ab582620d4d9 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 299.294 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[    0.004000] Memory: 116248k/131008k available (2572k kernel code, 14216k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xc8800000 - 0xff3fe000   ( 875 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xc7ff0000   ( 127 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004042] Calibrating delay loop (skipped), value calculated using timer frequency.. 598.58 BogoMIPS (lpj=1197176)
[    0.004171] Security Framework initialized
[    0.004220] SELinux:  Disabled at boot.
[    0.004366] AppArmor: AppArmor initialized
[    0.004434] Mount-cache hash table entries: 512
[    0.005515] Initializing cgroup subsys ns
[    0.005545] Initializing cgroup subsys cpuacct
[    0.005567] Initializing cgroup subsys memory
[    0.005663] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.005687] CPU: L2 cache: 256K
[    0.005773] Checking 'hlt' instruction... OK.
[    0.020259] SMP alternatives: switching to UP code
[    0.044117] Freeing SMP alternatives: 11k freed
[    0.044498] weird, boot CPU (#0) not listedby the BIOS.
[    0.044518] SMP motherboard not detected.
[    0.044539] Local APIC not detected. Using dummy APIC emulation.
[    0.044555] SMP disabled
[    0.045164] Brought up 1 CPUs
[    0.045187] Total of 1 processors activated (598.58 BogoMIPS).
[    0.048107] CPU0 attaching sched-domain:
[    0.048131]  domain 0: span 0 level CPU
[    0.048151]   groups: 0
[    0.050201] net_namespace: 840 bytes
[    0.050253] Booting paravirtualized kernel on bare hardware
[    0.051921] Time:  0:30:05  Date: 04/19/08
[    0.052197] NET: Registered protocol family 16
[    0.055340] EISA bus registered
[    0.073139] PCI: PCI BIOS revision 2.10 entry at 0xfd9c4, last bus=1
[    0.073163] PCI: Using configuration type 1 for base access
[    0.082945] ACPI: Interpreter disabled.
[    0.082973] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.083341] pnp: PnP ACPI: disabled
[    0.083370] PnPBIOS: Scanning system for PnP BIOS support...
[    0.083510] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7280
[    0.083535] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa066, dseg 0x400
[    0.093986] pnp 00:0e: unknown tag 0x82 length 20
[    0.098080] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[    0.101922] PCI: Probing PCI hardware
[    0.101950] PCI: Probing PCI hardware (bus 00)
[    0.102454] PCI: 0000:00:00.0 reg 10 32bit mmio: [0, 3ffffff]
[    0.102841] PCI: 0000:00:04.1 reg 20 io port: [fcd0, fcdf]
[    0.102986] PCI: 0000:00:04.2 reg 20 io port: [fce0, fcff]
[    0.103089] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[    0.103102] * this clock source is slow. Consider trying other clock sources
[    0.103228] pci 0000:00:04.3: quirk: region 1000-103f claimed by PIIX4 ACPI
[    0.103254] pci 0000:00:04.3: quirk: region 1040-104f claimed by PIIX4 SMB
[    0.103372] PCI: 0000:00:06.0 reg 10 32bit mmio: [0, fff]
[    0.103422] pci 0000:00:06.0: supports D1
[    0.103438] pci 0000:00:06.0: supports D2
[    0.103456] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot
[    0.103480] pci 0000:00:06.0: PME# disabled
[    0.103562] PCI: 0000:00:06.1 reg 10 32bit mmio: [0, fff]
[    0.103610] pci 0000:00:06.1: supports D1
[    0.103625] pci 0000:00:06.1: supports D2
[    0.103641] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot
[    0.103664] pci 0000:00:06.1: PME# disabled
[    0.103763] PCI: 0000:00:08.0 reg 10 32bit mmio: [fedffc00, fedffcff]
[    0.103795] PCI: 0000:00:08.0 reg 14 io port: [fcc8, fccf]
[    0.103824] PCI: 0000:00:08.0 reg 18 io port: [f800, f8ff]
[    0.103910] pci 0000:00:08.0: supports D2
[    0.103927] pci 0000:00:08.0: PME# supported from D2 D3hot D3cold
[    0.103950] pci 0000:00:08.0: PME# disabled
[    0.104179] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.104213] PCI: 0000:01:00.0 reg 14 32bit mmio: [fe400000, fe7fffff]
[    0.104243] PCI: 0000:01:00.0 reg 18 32bit mmio: [feb00000, febfffff]
[    0.104328] pci 0000:01:00.0: supports D1
[    0.104343] pci 0000:01:00.0: supports D2
[    0.104423] PCI: 0000:01:00.1 reg 10 32bit mmio: [fcc00000, fcffffff]
[    0.104454] PCI: 0000:01:00.1 reg 14 32bit mmio: [fea00000, feafffff]
[    0.104650] PCI: bridge 0000:00:01.0 32bit mmio: [fe400000, febfffff]
[    0.104676] PCI: bridge 0000:00:01.0 32bit mmio pref: [fcc00000, fdffffff]
[    0.111260] pci 0000:00:04.0: PIIX/ICH IRQ router [8086/7110]
[    0.111379] PCI: setting IRQ 11 as level-triggered
[    0.111400] pci 0000:00:06.0: found PCI INT A -> IRQ 11
[    0.111466] pci 0000:00:06.0: sharing IRQ 11 with 0000:00:06.1
[    0.112386] NET: Registered protocol family 8
[    0.112386] NET: Registered protocol family 20
[    0.112581] NetLabel: Initializing
[    0.112599] NetLabel:  domain hash size = 128
[    0.112614] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.112740] NetLabel:  unlabeled traffic allowed by default
[    0.114973] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.114993]    actual entries 65620
[    0.116750] AppArmor: AppArmor Filesystem Enabled
[    0.116898] system 00:00: ioport range 0x398-0x399 has been reserved
[    0.116926] system 00:00: ioport range 0x3810-0x381f has been reserved
[    0.116955] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.117015] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[    0.117041] system 00:01: iomem range 0xe8000-0xfffff could not be reserved
[    0.117065] system 00:01: iomem range 0x100000-0x7ffffff could not be reserved
[    0.117154] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.117179] system 00:0a: ioport range 0x1000-0x103f has been reserved
[    0.117203] system 00:0a: ioport range 0x1040-0x104f has been reserved
[    0.123169] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.123194] pci 0000:00:01.0:   IO window: disabled
[    0.123221] pci 0000:00:01.0:   MEM window: 0xfe400000-0xfebfffff
[    0.123247] pci 0000:00:01.0:   PREFETCH window: 0x000000fcc00000-0x000000fdffffff
[    0.123280] pci 0000:00:06.0: CardBus bridge, secondary bus 0000:02
[    0.123300] pci 0000:00:06.0:   IO window: 0x001400-0x0014ff
[    0.123324] pci 0000:00:06.0:   IO window: 0x001800-0x0018ff
[    0.123349] pci 0000:00:06.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.123374] pci 0000:00:06.0:   MEM window: 0x14000000-0x17ffffff
[    0.123399] pci 0000:00:06.1: CardBus bridge, secondary bus 0000:06
[    0.123419] pci 0000:00:06.1:   IO window: 0x001c00-0x001cff
[    0.123442] pci 0000:00:06.1:   IO window: 0x002000-0x0020ff
[    0.123466] pci 0000:00:06.1:   PREFETCH window: 0x18000000-0x1bffffff
[    0.123491] pci 0000:00:06.1:   MEM window: 0x1c000000-0x1fffffff
[    0.123563] pci 0000:00:06.0: found PCI INT A -> IRQ 11
[    0.123632] pci 0000:00:06.0: sharing IRQ 11 with 0000:00:06.1
[    0.123679] pci 0000:00:06.0: setting latency timer to 64
[    0.123720] pci 0000:00:06.1: found PCI INT A -> IRQ 11
[    0.123780] pci 0000:00:06.1: sharing IRQ 11 with 0000:00:06.0
[    0.123832] pci 0000:00:06.1: setting latency timer to 64
[    0.123857] bus: 00 index 0 io port: [0, ffff]
[    0.123876] bus: 00 index 1 mmio: [0, ffffffff]
[    0.123892] bus: 01 index 0 mmio: [0, 0]
[    0.123909] bus: 01 index 1 mmio: [fe400000, febfffff]
[    0.123928] bus: 01 index 2 mmio: [fcc00000, fdffffff]
[    0.123945] bus: 01 index 3 mmio: [0, 0]
[    0.123962] bus: 02 index 0 io port: [1400, 14ff]
[    0.123980] bus: 02 index 1 io port: [1800, 18ff]
[    0.124094] bus: 02 index 2 mmio: [10000000, 13ffffff]
[    0.124116] bus: 02 index 3 mmio: [14000000, 17ffffff]
[    0.124135] bus: 06 index 0 io port: [1c00, 1cff]
[    0.124152] bus: 06 index 1 io port: [2000, 20ff]
[    0.124170] bus: 06 index 2 mmio: [18000000, 1bffffff]
[    0.124188] bus: 06 index 3 mmio: [1c000000, 1fffffff]
[    0.124263] NET: Registered protocol family 2
[    0.125521] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.127439] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[    0.127601] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[    0.127783] TCP: Hash tables configured (established 4096 bind 4096)
[    0.127804] TCP reno registered
[    0.128527] NET: Registered protocol family 1
[    0.129380] checking if image is initramfs... it is
[    5.166036] Freeing initrd memory: 7990k freed
[    5.167293] Simple Boot Flag at 0x37 set to 0x1
[    5.170969] audit: initializing netlink socket (disabled)
[    5.171063] type=2000 audit(1208565010.168:1): initialized
[    5.213261] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    5.237774] VFS: Disk quotas dquot_6.5.1
[    5.238642] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.239527] msgmni has been set to 242
[    5.240777] io scheduler noop registered
[    5.240800] io scheduler anticipatory registered
[    5.240818] io scheduler deadline registered
[    5.240954] io scheduler cfq registered (default)
[    5.241024] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    5.241174] pci 0000:01:00.0: Boot video device
[    5.243636] isapnp: Scanning for PnP cards...
[    5.337871]  01:01: card 'NeoMagic MagicWave 3DX Sound System'
[    5.337898] isapnp: 1 Plug & Play card detected total
[    5.807870] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    5.808605] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.809818] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    5.816076] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.834142] brd: module loaded
[    5.834776] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    5.835949] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    5.839479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.839530] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.843067] mice: PS/2 mouse device common for all mice
[    5.844495] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.844577] rtc0: alarms up to one day
[    5.845789] EISA: Probing bus 0 at eisa.0
[    5.845829] Cannot allocate resource for EISA slot 1
[    5.845849] Cannot allocate resource for EISA slot 2
[    5.845871] Cannot allocate resource for EISA slot 3
[    5.845938] EISA: Detected 0 cards.
[    5.845959] cpuidle: using governor ladder
[    5.845977] cpuidle: using governor menu
[    5.850765] TCP cubic registered
[    5.850967] Using IPI No-Shortcut mode
[    5.853480] registered taskstats version 1
[    5.854166]   Magic number: 4:887:506
[    5.854781] rtc_cmos 00:05: setting system clock to 2008-04-19 00:30:05 UTC (1208565005)
[    5.854808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.854825] EDD information not available.
[    5.858168] Freeing unused kernel memory: 424k freed
[    5.858604] Write protecting the kernel text: 2576k
[    5.858857] Write protecting the kernel read-only data: 936k
[    5.881869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    7.032725] fuse init (API version 7.9)
[    7.628246] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   10.581440] usbcore: registered new interface driver usbfs
[   10.581603] usbcore: registered new interface driver hub
[   10.588463] usbcore: registered new device driver usb
[   10.624632] SCSI subsystem initialized
[   10.636871] USB Universal Host Controller Interface driver v3.0
[   10.651133] PCI: setting IRQ 9 as level-triggered
[   10.651164] uhci_hcd 0000:00:04.2: found PCI INT D -> IRQ 9
[   10.651298] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   10.651648] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   10.651747] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000fce0
[   10.652997] usb usb1: configuration #1 chosen from 1 choice
[   10.653233] hub 1-0:1.0: USB hub found
[   10.653310] hub 1-0:1.0: 2 ports detected
[   10.868372] libata version 3.00 loaded.
[   10.912496] ata_piix 0000:00:04.1: version 2.12
[   10.921003] scsi0 : ata_piix
[   10.922159] scsi1 : ata_piix
[   10.922470] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcd0 irq 14
[   10.922495] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcd8 irq 15
[   11.395456] ata1.00: ATA-4: IBM-DADA-26480, AD6OA4AA, max UDMA/33
[   11.395487] ata1.00: 12685680 sectors, multi 16: LBA 
[   11.438265] ata1.00: configured for UDMA/33
[   11.593224] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   16.749446] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   21.905776] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   27.086303] ata2.00: ATAPI: UJDA150, 1.17, max MWDMA2
[   27.118228] ata2.00: configured for MWDMA2
[   27.119042] scsi 0:0:0:0: Direct-Access     ATA      IBM-DADA-26480   AD6O PQ: 0 ANSI: 5
[   27.125488] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA150          1.17 PQ: 0 ANSI: 5
[   27.320235] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   27.320586] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   27.539182] Driver 'sd' needs updating - please use bus_type methods
[   27.539908] sd 0:0:0:0: [sda] 12685680 512-byte hardware sectors (6495 MB)
[   27.540067] sd 0:0:0:0: [sda] Write Protect is off
[   27.540091] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.540354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.540890] sd 0:0:0:0: [sda] 12685680 512-byte hardware sectors (6495 MB)
[   27.541039] sd 0:0:0:0: [sda] Write Protect is off
[   27.541063] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.541324] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.541364]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   27.844524]  sda1 sda2 < sda5 >
[   27.879818] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.925387] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   27.925421] Uniform CD-ROM driver Revision: 3.20
[   27.926227] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.052188] PM: Starting manual resume from disk
[   29.052219] PM: Resume from partition 8:5
[   29.052233] PM: Checking hibernation image.
[   29.052876] PM: Resume from disk failed.
[   29.337807] kjournald starting.  Commit interval 5 seconds
[   29.337930] EXT3-fs: mounted filesystem with ordered data mode.
[   51.896081] udevd version 124 started
[   58.689381] Linux agpgart interface v0.103
[   58.854182] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.025428] Yenta: CardBus bridge found at 0000:00:06.0 [0000:0000]
[   59.025492] Yenta: Enabling burst memory read transactions
[   59.025516] Yenta: Using CSCINT to route CSC interrupts to PCI
[   59.025534] Yenta: Routing CardBus interrupts to PCI
[   59.025559] Yenta TI: socket 0000:00:06.0, mfunc 0x00000000, devctl 0x64
[   59.262622] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   59.262647] Socket status: 30000006
[   59.262722] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   59.352885] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   59.363996] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0x24000000
[   59.364187] Yenta: CardBus bridge found at 0000:00:06.1 [0000:0000]
[   59.364243] Yenta: Using CSCINT to route CSC interrupts to PCI
[   59.364262] Yenta: Routing CardBus interrupts to PCI
[   59.364286] Yenta TI: socket 0000:00:06.1, mfunc 0x00000000, devctl 0x64
[   59.596778] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   59.596802] Socket status: 30000006
[   59.637210] piix4_smbus 0000:00:04.3: SMBus Host Controller at 0x1040, revision 0
[   59.642761] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.282406] Synaptics Touchpad, model: 1, fw: 4.0, id: 0x856a1, caps: 0x0/0x0
[   61.319123] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3
[   71.007707] NeoMagic 256 0000:01:00.1: found PCI INT B -> IRQ 9
[   71.007804] NeoMagic 256 0000:01:00.1: sharing IRQ 9 with 0000:01:00.0
[   71.007867] nm256: no ac97 is found!
[   71.007888]   force the driver to load by passing in the module parameter
[   71.007906]     force_ac97=1
[   71.007919]   or try sb16, opl3sa2, or cs423x drivers instead.
[   72.689393] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   72.692074] cs: IO port probe 0x3e0-0x4ff: clean.
[   72.694143] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   72.696872] cs: IO port probe 0x3e0-0x4ff: clean.
[   72.698198] cs: IO port probe 0x820-0x8ff: clean.
[   72.699369] cs: IO port probe 0xc00-0xcf7: clean.
[   72.701066] cs: IO port probe 0x820-0x8ff: clean.
[   72.702242] cs: IO port probe 0xc00-0xcf7: clean.
[   72.704422] cs: IO port probe 0xa00-0xaff: clean.
[   72.709382] cs: IO port probe 0xa00-0xaff: clean.
[   78.863718] loop: module loaded
[   79.257308] parport_pc 00:11: reported by Plug and Play BIOS
[   79.257419] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   79.356433] lp0: using parport0 (interrupt-driven).
[   81.268376] Adding 321260k swap on /dev/sda5.  Priority:-1 extents:1 across:321260k
[   82.180300] EXT3 FS on sda1, internal journal
[   86.440519] type=1505 audit(1208565086.082:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3586
[   86.442575] type=1505 audit(1208565086.086:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3586
[   87.148362] ip_tables: (C) 2000-2006 Netfilter Core Team
[   91.490857] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   91.492027] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   91.497073] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   91.499016] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   95.036244] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   95.413531] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   96.242693] ppdev: user-space parallel port driver
[  104.892352] Bluetooth: Core ver 2.13
[  104.902883] NET: Registered protocol family 31
[  104.902926] Bluetooth: HCI device and connection manager initialized
[  104.902953] Bluetooth: HCI socket layer initialized
[  105.186129] Bluetooth: L2CAP ver 2.11
[  105.186179] Bluetooth: L2CAP socket layer initialized
[  105.370867] Bluetooth: RFCOMM socket layer initialized
[  105.372567] Bluetooth: RFCOMM TTY layer initialized
[  105.372614] Bluetooth: RFCOMM ver 1.10
[  105.402575] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  105.402617] Bluetooth: BNEP filters: protocol multicast
[  105.748170] Bridge firewalling registered
[  105.750644] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  106.229409] Bluetooth: SCO (Voice Link) ver 0.6
[  106.229466] Bluetooth: SCO socket layer initialized
[  191.101178] NET: Registered protocol family 10
[  191.110826] lo: Disabled Privacy Extensions
[  252.293258] ppdev0: registered pardevice
[  252.438585] ppdev0: unregistered pardevice
[  272.235062] ppdev0: registered pardevice
[  272.301968] ppdev0: unregistered pardevice
[  273.871657] ppdev0: registered pardevice
[  273.921817] ppdev0: unregistered pardevice
[  278.220716] type=1503 audit(1208565277.863:4): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/4720/net/" pid=4720 profile="/usr/sbin/cupsd"
[  278.234412] type=1503 audit(1208565277.879:5): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234505] type=1503 audit(1208565277.879:6): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234565] type=1503 audit(1208565277.879:7): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234623] type=1503 audit(1208565277.879:8): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234681] type=1503 audit(1208565277.879:9): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234740] type=1503 audit(1208565277.879:10): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234799] type=1503 audit(1208565277.879:11): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.234856] type=1503 audit(1208565277.879:12): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=4720 profile="/usr/sbin/cupsd"
[  278.235196] type=1503 audit(1208565277.879:13): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/4720/net/dev" pid=4720 profile="/usr/sbin/cupsd"
[  437.516262] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  437.686665] usb 1-1: configuration #1 chosen from 1 choice
[  439.783768] usbcore: registered new interface driver libusual
[  440.977908] Initializing USB Mass Storage driver...
[  440.988584] scsi2 : SCSI emulation for USB Mass Storage devices
[  441.000840] usbcore: registered new interface driver usb-storage
[  441.007184] USB Mass Storage support registered.
[  441.012465] usb-storage: device found at 2
[  441.012504] usb-storage: waiting for device to settle before scanning
[  446.015787] usb-storage: device scan complete
[  446.028135] scsi 2:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[  446.651650] sd 2:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[  446.666684] sd 2:0:0:0: [sdb] Write Protect is off
[  446.666794] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  446.666850] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  446.711578] sd 2:0:0:0: [sdb] 2013184 512-byte hardware sectors (1031 MB)
[  446.734019] sd 2:0:0:0: [sdb] Write Protect is off
[  446.734214] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  446.734259] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  446.734561]  sdb: sdb1
[  446.783017] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  446.783971] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

I'd appreciate any guidance anyone can offer. Thanks!

Jake

---

### Post by otakuj462 on 2009-03-24
Bump?

If I can't fix this within a few days, I'll need to put Win 98 back on :(

Any guidance anyone can offer would be greatly appreciated. Much thanks,

Jake

---

### Post by mister_playboy on 2009-03-27
Unfortunately, I only have a question for you, rather than any help.

Is the sound working on that laptop?  I have one with the same chipset (NeoMagic 256AV), and I can't get it to work in Ubuntu, even though there is a ALSA driver for it.

---

