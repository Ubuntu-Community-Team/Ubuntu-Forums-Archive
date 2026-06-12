---
title: "Internal hard drive not recognized"
date: 2010-03-07
forum: Hardware
---

### Post by kinkajou45 on 2010-03-07
Two years ago I was given a Sony Vaio laptop, model PCG-FXA63. It's been running 9.10 with no problems. I replaced a broken keyboard and installed 9.4, later upgrading to 9.10. I recently had to replace the (original) hard drive. The new drive, Samsung 160 gig, was formatted with ext 3 by another linux machine.  I installed the new drive. At installation of 9.10 (and 9.04), the machine failed to recognize the drive.  I substituted a working, 9.04 loaded drive to verify read failure.  That drive was not recognized by Ubuntu.  The bios, Phoenix R0121k5 **DOES** recognize the drives.  I followed instructions at the SONY site, reverted to bios default settings with no change in drive recognition.  I ran installation with each option offered under PF6 on the installation CD. No hard drive seen at installation although dmesg shows that the ata drive is not accepting the address, so its existence is recognized by UBUNTU, at least at this level. I have removed and replaced the battery, removed and replaced the memory units, cleaned and checked the machine. Cables and sockets look good. Powers up no problem. Keyboard working. Display excellent.Internet/network working with live CD.  DVD working and is the only drive recognized.  The 9.04 CD is from Ubuntu, the 9.10 is a downloaded iso but passed disk integrity check and was used to set up three other machines. I have spent two days in the Community forums and Google researching this issue.  Flashing the bios is technically beyond my capabilities at this point.I could not find any way to edit scripts from the live CD even using su-and since I can't install the system, this appears to be a no go option. I have multiple machines so it's not critical that the Vaio remain in the network, but I hate to abandon it if it can be repaired by me. 

Output from terminal inquiries is posted for the internal drive that runs Ubuntu 9.04 and is fine on other machines. Current BIOS setting factory default.
Thanks in advance for suggestions.

ubuntu@ubuntu:~$ sudo rmmod echi-hcd
ERROR: Module echi_hcd does not exist in /proc/modules
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo lsmod
Module            Size Used by
binfmt_misc         16776 1
lp            17156 0
bridge          56340 0
stp            10500 1 bridge
bnep            20224 2
input_polldev       11912 0
snd_via82xx         32152 3
gameport           19340 1 snd_via82xx
joydev           18368 0
snd_via82xx_modem        19336 0
snd_ac97_codec        112292 2 snd_via82xx,snd_via82xx_modem
ac97_bus           9856 1 snd_ac97_codec
snd_pcm_oss          46336 0
snd_mixer_oss        22656 1 snd_pcm_oss
snd_pcm            82948 4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart        15104 1 snd_via82xx
snd_seq_dummy          10756 0
snd_seq_oss         37760 0
                    14336 0
snd_seq_midi
                    29696 2 snd_mpu401_uart,snd_seq_midi
snd_rawmidi
snd_seq_midi_event      15104 2 snd_seq_oss,snd_seq_midi
pcmcia            44748 0
                  56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq
                 15620 0
ppdev
via_agp          16256 1
snd_timer          29704 2 snd_pcm,snd_seq
                   61972 0
psmouse
via686a           20876 0
yenta_socket        32396 2
parport_pc         40100 1
video             25360 0
snd_seq_device          14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw           13316 0
i2c_viapro           15892 0
pcspkr             10496 0
rsrc_nonstatic        19328 1 yenta_socket
agpgart            42696 1 via_agp
parport            42220 3 lp,ppdev,parport_pc
shpchp             40212 0
output            11008 1 video
pcmcia_core            43540 3 pcmcia,yenta_socket,rsrc_nonstatic
snd              62628 18
snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_o
snd_page_alloc         16904 3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore            15200 1 snd
squashfs            46344 1
aufs             165924 1
exportfs           12544 1 aufs
nls_cp437            13696 1
isofs            39844 1
ohci1394             38576 0
8139too             32128 0
8139cp              27776 0
mii              13312 2 8139too,8139cp
ieee1394             94660 1 ohci1394
usbhid            42336 0
                  64324 0
floppy
fbcon             46112 0
                 10752 1 fbcon
tileblit
font             16384 1 fbcon
                 13824 1 fbcon
bitblit
softcursor           9984 1 bitblit
                       12876 1
compcache
lzo_decompress          10880 1 compcache
                       10880 1 compcache
lzo_compress
tlsf            14092 1 compcache
ubuntu@ubuntu:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.3 present.
Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
   Vendor: Sony Corporation
   Version: R0121K5
   Release Date: 08/13/2002
   Address: 0xE66E0
   Runtime Size: 104736 bytes
   ROM Size: 512 kB
   Characteristics:
      ISA is supported
      PCI is supported
      PC Card (PCMCIA) is supported
      PNP is supported
      APM is supported
      BIOS is upgradeable
BIOS shadowing is allowed
Boot from CD is supported
Selectable boot is supported
BIOS ROM is socketed
EDD is supported
ACPI is supported
USB legacy is supported
AGP is supported
BIOS boot specification is supported
Function key-initiated network boot is supported

dmesg -c, first page is blank, begin page 2
[ 0.000000]  #3 [0000100000 - 000087c52c] TEXT DATA BSS ==> [0000100000 - 000087c52c]
[ 0.000000]  #4 [000f75c000 - 000febf993]        RAMDISK ==> [000f75c000 - 000febf993]
[ 0.000000]  #5 [000087d000 - 0000881000] INIT_PG_TABLE ==> [000087d000 - 0000881000]
[ 0.000000]  #6 [000009f000 - 0000100000] BIOS reserved ==> [000009f000 - 0000100000]
[ 0.000000]  #7 [0000010000 - 0000011000]         PGTABLE ==> [0000010000 - 0000011000]
[ 0.000000]  #8 [0000011000 - 0000013000]         BOOTMAP ==> [0000011000 - 0000013000]
[ 0.000000] Zone PFN ranges:
[ 0.000000]  DMA      0x00000000 -> 0x00001000
[ 0.000000]  Normal 0x00001000 -> 0x00010000
[ 0.000000]  HighMem 0x00010000 -> 0x00010000
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[5] active PFN ranges
[ 0.000000]    0: 0x00000000 -> 0x00000002
               0: 0x00000006 -> 0x00000007
[ 0.000000]
[ 0.000000]    0: 0x00000010 -> 0x00000092
[ 0.000000]    0: 0x00000100 -> 0x0000fef0
[ 0.000000]    0: 0x0000ff00 -> 0x00010000
[ 0.000000] On node 0 totalpages: 65397
[ 0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[ 0.000000]  DMA zone: 32 pages used for memmap
[ 0.000000]  DMA zone: 0 pages reserved
[ 0.000000]  DMA zone: 3941 pages, LIFO batch:0
[ 0.000000]  Normal zone: 480 pages used for memmap
[ 0.000000]  Normal zone: 60944 pages, LIFO batch:15
[ 0.000000]  HighMem zone: 0 pages used for memmap
             Movable zone: 0 pages used for memmap
[ 0.000000]
            ACPI: PM-Timer IO Port: 0x8008
[ 0.000000]
[ 0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[ 0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
            PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[ 0.000000]
[ 0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[ 0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000c0000
[ 0.000000] PM: Registered nosave memory: 00000000000c0000 - 00000000000d4000
[ 0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[ 0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[ 0.000000] PM: Registered nosave memory: 000000000fef0000 - 000000000feff000
[ 0.000000] PM: Registered nosave memory: 000000000feff000 - 000000000ff00000
[ 0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effe0000)
[ 0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 64885
[ 0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed
boot=casper initrd=/casper/initrd.gz quiet splash --
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1399.871 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 0.004000] allocated 1310720 bytes of page_cgroup
[ 0.004000] please try cgroup_disable=memory option if you don't want
[ 0.004000] Scanning for low memory corruption every 60 seconds
[ 0.004000] Memory: 242404k/262144k available (4126k kernel code, 18872k reserved, 2208k data, 532k init,
0k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000]    fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
               pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000]
[ 0.004000]    vmalloc : 0xd0800000 - 0xff3fe000 ( 747 MB)
               lowmem : 0xc0000000 - 0xd0000000 ( 256 MB)
[ 0.004000]
[ 0.004000]      .init : 0xc0737000 - 0xc07bc000 ( 532 kB)
                 .data : 0xc0507a6f - 0xc072fe60 (2208 kB)
[ 0.004000]
[ 0.004000]      .text : 0xc0100000 - 0xc0507a6f (4126 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 2799.74 BogoMIPS
(lpj=5599484)
[ 0.004058] Security Framework initialized
[ 0.004073] SELinux: Disabled at boot.
[ 0.004122] AppArmor: AppArmor initialized
[ 0.004138] Mount-cache hash table entries: 512
[ 0.004398] Initializing cgroup subsys ns
[ 0.004406] Initializing cgroup subsys cpuacct
[ 0.004410] Initializing cgroup subsys memory
[ 0.004417] Initializing cgroup subsys freezer
[ 0.004440] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 0.004445] CPU: L2 Cache: 256K (64 bytes/line)
[ 0.004473] Checking 'hlt' instruction... OK.
[ 0.020721] SMP alternatives: switching to UP code
[ 0.237015] Freeing SMP alternatives: 18k freed
[ 0.237025] ACPI: Core revision 20080926
[ 0.242833] ACPI: Checking initramfs for custom DSDT
[ 0.675257] ACPI: setting ELCR to 0200 (from 0620)
  0.676130] weird, boot CPU (#0) not listedby the BIOS.
[ 0.676134] SMP motherboard not detected.
[ 0.676139] Local APIC not detected. Using dummy APIC emulation.
[ 0.676142] SMP disabled
[ 0.676740] Brought up 1 CPUs
[ 0.676744] Total of 1 processors activated (2799.74 BogoMIPS).
[ 0.676773] CPU0 attaching NULL sched-domain.
[ 0.677464] net_namespace: 776 bytes
[ 0.677488] Booting paravirtualized kernel on bare hardware
[ 0.677893] Time: 2:22:30 Date: 06/02/00
[ 0.677903] regulator: core version 0.5
[ 0.677989] NET: Registered protocol family 16
[ 0.680219] EISA bus registered
[ 0.680248] ACPI: bus type pci registered
[ 0.696556] PCI: PCI BIOS revision 2.10 entry at 0xfd7cd, last bus=1
[ 0.696561] PCI: Using configuration type 1 for base access
[ 0.698834] ACPI: EC: Look up EC in DSDT
[ 0.705615] ACPI: Interpreter enabled
[ 0.705623] ACPI: (supports S0 S3 S4 S5)
[ 0.705650] ACPI: Using PIC for interrupt routing
[ 0.724373] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[ 0.724377] ACPI: EC: driver started in poll mode
[ 0.724547] ACPI: No dock devices found.
[ 0.724563] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.724637] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
            pci 0000:00:01.0: supports D1
[ 0.724703]
[ 0.724808] pci 0000:00:07.1: reg 20 io port: [0x1c40-0x1c4f]
            pci 0000:00:07.2: reg 20 io port: [0x1c00-0x1c1f]
[ 0.724865]
[ 0.724920] pci 0000:00:07.3: reg 20 io port: [0x1c20-0x1c3f]
            pci 0000:00:07.4: quirk: region 6800-687f claimed by vt82c686 HW-mon
[ 0.724992]
[ 0.724998] pci 0000:00:07.4: quirk: region 8100-810f claimed by vt82c686 SMB
            pci 0000:00:07.5: reg 10 io port: [0x1000-0x10ff]
[ 0.725031]
[ 0.725038] pci 0000:00:07.5: reg 14 io port: [0x1c54-0x1c57]
            pci 0000:00:07.5: reg 18 io port: [0x1c50-0x1c53]
[ 0.725045]
[ 0.725096] pci 0000:00:07.6: reg 10 io port: [0x1400-0x14ff]
            pci 0000:00:0a.0: reg 10 32bit mmio: [0x000000-0x000fff]
[ 0.725157]
[ 0.725166] pci 0000:00:0a.0: supports D1 D2
            pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.725170]
[ 0.725176] pci 0000:00:0a.0: PME# disabled
[ 0.725209] pci 0000:00:0a.1: reg 10 32bit mmio: [0x000000-0x000fff]
[ 0.725218] pci 0000:00:0a.1: supports D1 D2
            pci 0000:00:0a.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.725221]
            pci 0000:00:0a.1: PME# disabled
[ 0.725226]
[ 0.725265] pci 0000:00:0e.0: reg 10 32bit mmio: [0xe8004000-0xe80047ff]
[ 0.725272] pci 0000:00:0e.0: reg 14 32bit mmio: [0xe8000000-0xe8003fff]
            pci 0000:00:0e.0: supports D2
[ 0.725302]
            pci 0000:00:0e.0: PME# supported from D2 D3hot
[ 0.725305]
[ 0.725310] pci 0000:00:0e.0: PME# disabled
[ 0.725340] pci 0000:00:10.0: reg 10 io port: [0x1800-0x18ff]
            pci 0000:00:10.0: reg 14 32bit mmio: [0xe8004800-0xe80048ff]
[ 0.725347]
[ 0.725374] pci 0000:00:10.0: supports D1 D2
[ 0.725377] pci 0000:00:10.0: PME# supported from D1 D2 D3hot D3cold
            pci 0000:00:10.0: PME# disabled
[ 0.725382]
[ 0.725437] pci 0000:01:00.0: reg 10 32bit mmio: [0xe9000000-0xe9ffffff]
[ 0.725445] pci 0000:01:00.0: reg 14 io port: [0x9000-0x90ff]
[ 0.725452] pci 0000:01:00.0: reg 18 32bit mmio: [0xe8100000-0xe8100fff]
[ 0.725470] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[ 0.725480] pci 0000:01:00.0: supports D1 D2
[ 0.725517] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[ 0.725522] pci 0000:00:01.0: bridge 32bit mmio: [0xe8100000-0xe9ffffff]
[ 0.725563] bus 00 -> node 0
[ 0.725573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.725679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[ 0.731737] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12)
[ 0.731959] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[ 0.732191] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12)
[ 0.732414] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[ 0.732566] ACPI: Power Resource [PCR0] (off)
[ 0.732626] ACPI: Power Resource [PCR1] (off)
[ 0.732742] ACPI: WMI: Mapper loaded
[ 0.733198] SCSI subsystem initialized
[ 0.733291] libata version 3.00 loaded.
[ 0.733388] usbcore: registered new interface driver usbfs
[ 0.733419] usbcore: registered new interface driver hub
[ 0.733475] usbcore: registered new device driver usb
[ 0.733701] PCI: Using ACPI for IRQ routing
[ 0.733848] Bluetooth: Core ver 2.13
[ 0.733848] NET: Registered protocol family 31
[ 0.733848] Bluetooth: HCI device and connection manager initialized
[ 0.733848] Bluetooth: HCI socket layer initialized
            NET: Registered protocol family 8
[ 0.733848]
[ 0.733848] NET: Registered protocol family 20
            NetLabel: Initializing
[ 0.733848]
[ 0.733848] NetLabel: domain hash size = 128
            NetLabel: protocols = UNLABELED CIPSOv4
[ 0.733848]
[ 0.733848] NetLabel: unlabeled traffic allowed by default
            AppArmor: AppArmor Filesystem Enabled
[ 0.733848]
[ 0.733848] pnp: PnP ACPI init
            ACPI: bus type pnp registered
[ 0.733848]
[ 0.747394] pnp: PnP ACPI: found 12 devices
            ACPI: ACPI bus type pnp unregistered
[ 0.747398]
[ 0.747404] PnPBIOS: Disabled by ACPI PNP
            system 00:05: iomem range 0x0-0x9ffff could not be reserved
[ 0.747427]
[ 0.747433] system 00:05: iomem range 0xdc000-0xdffff could not be reserved
[ 0.747437] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[ 0.747442] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
            system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[ 0.747452]
            system 00:06: ioport range 0x8000-0x807f has been reserved
[ 0.747457]
[ 0.747460] system 00:06: ioport range 0x8080-0x80ff has been reserved
[ 0.747465] system 00:06: ioport range 0x8100-0x811f could not be reserved
            system 00:06: ioport range 0x6800-0x687f has been reserved
[ 0.747469]
            pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.782323]
[ 0.782328] pci 0000:00:01.0: IO window: 0x9000-0x9fff
[ 0.782334] pci 0000:00:01.0: MEM window: 0xe8100000-0xe9ffffff
            pci 0000:00:01.0: PREFETCH window: 0x00000030000000-0x000000300fffff
[ 0.782340]
[ 0.782347] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[ 0.782351] pci 0000:00:0a.0: IO window: 0x002000-0x0020ff
            pci 0000:00:0a.0: IO window: 0x002400-0x0024ff
[ 0.782357]
[ 0.782362] pci 0000:00:0a.0: PREFETCH window: 0x20000000-0x23ffffff
[ 0.782367] pci 0000:00:0a.0: MEM window: 0x24000000-0x27ffffff
[ 0.782373] pci 0000:00:0a.1: CardBus bridge, secondary bus 0000:06
[ 0.782376] pci 0000:00:0a.1: IO window: 0x002800-0x0028ff
[ 0.782382] pci 0000:00:0a.1: IO window: 0x002c00-0x002cff
[ 0.782387] pci 0000:00:0a.1: PREFETCH window: 0x28000000-0x2bffffff
[ 0.782392] pci 0000:00:0a.1: MEM window: 0x2c000000-0x2fffffff
[ 0.782411] pci 0000:00:01.0: setting latency timer to 64
[ 0.782426] pci 0000:00:0a.0: power state changed by ACPI to D0
[ 0.782772] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[ 0.782778] PCI: setting IRQ 9 as level-triggered
[ 0.782785] pci 0000:00:0a.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[ 0.782797] pci 0000:00:0a.1: power state changed by ACPI to D0
[ 0.783122] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[ 0.783126] PCI: setting IRQ 10 as level-triggered
[ 0.783133] pci 0000:00:0a.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[ 0.783142] bus: 00 index 0 io port: [0x00-0xffff]
[ 0.783145] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[ 0.783148] bus: 01 index 0 io port: [0x9000-0x9fff]
[ 0.783152] bus: 01 index 1 mmio: [0xe8100000-0xe9ffffff]
[ 0.783155] bus: 01 index 2 mmio: [0x30000000-0x300fffff]
[ 0.783158] bus: 01 index 3 mmio: [0x0-0x0]
[ 0.783161] bus: 02 index 0 io port: [0x2000-0x20ff]
[ 0.783164] bus: 02 index 1 io port: [0x2400-0x24ff]
[ 0.783167] bus: 02 index 2 mmio: [0x20000000-0x23ffffff]
[ 0.783170] bus: 02 index 3 mmio: [0x24000000-0x27ffffff]
[ 0.783174] bus: 06 index 0 io port: [0x2800-0x28ff]
            bus: 06 index 1 io port: [0x2c00-0x2cff]
[ 0.783177]
[ 0.783180] bus: 06 index 2 mmio: [0x28000000-0x2bffffff]
            bus: 06 index 3 mmio: [0x2c000000-0x2fffffff]
[ 0.783183]
[ 0.783207] NET: Registered protocol family 2
            IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 0.783427]
[ 0.783862] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
            TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[ 0.784076]
[ 0.784250] TCP: Hash tables configured (established 8192 bind 8192)
            TCP reno registered
[ 0.784254]
[ 0.784375] NET: Registered protocol family 1
            checking if image is initramfs... it is
[ 0.784622]
[ 1.284135] Switched to high resolution mode on CPU 0
            Freeing initrd memory: 7566k freed
[ 1.750602]
[ 1.750690] Simple Boot Flag at 0x37 set to 0x1
[ 1.750810] cpufreq: No nForce2 chipset.
[ 1.751060] audit: initializing netlink socket (disabled)
            type=2000 audit(959912550.748:1): initialized
[ 1.751103]
            HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.762359]
[ 1.764488] VFS: Disk quotas dquot_6.5.1
[ 1.764582] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
            fuse init (API version 7.10)
[ 1.765540]
            msgmni has been set to 488
[ 1.765671]
[ 1.766037] alg: No test for stdrng (krng)
[ 1.766061] io scheduler noop registered
            io scheduler anticipatory registered
[ 1.766065]
[ 1.766068] io scheduler deadline registered
[ 1.766092] io scheduler cfq registered (default)
            pci 0000:00:00.0: Applying VIA southbridge workaround
[ 1.766127]
[ 1.766134] PCI: VIA PCI bridge detected.Disabling DAC.
[ 1.766141] pci 0000:00:07.0: Disabling VIA external APIC routing
[ 1.766194] pci 0000:01:00.0: Boot video device
[ 1.789703] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.789717] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.789941] ACPI: AC Adapter [ACAD] (on-line)
[ 1.795219] ACPI: Battery Slot [BAT1] (battery absent)
[ 1.799646] ACPI: Battery Slot [BAT2] (battery absent)
[ 1.799758] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 1.799764] ACPI: Power Button (FF) [PWRF]
[ 1.799830] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[ 1.799834] ACPI: Sleep Button (CM) [SBTN]
[ 1.799920] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[ 1.799989] ACPI: Lid Switch [LID]
[ 1.800275] ACPI: CPU0 (power states: C1[C1] C2[C2])
[ 1.800317] processor ACPI_CPU:00: registered as cooling_device0
[ 1.800323] ACPI: Processor [CPU0] (supports 16 throttling states)
[ 1.816371] thermal LNXTHERM:01: registered as thermal_zone0
[ 1.825637] ACPI: Thermal Zone [THRM] (66 C)
[ 1.825705] isapnp: Scanning for PnP cards...
[ 2.179820] isapnp: No Plug & Play device found
[ 2.182179] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 2.182320] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 2.182781] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 2.184126] brd: module loaded
[ 2.184681] loop: module loaded
[ 2.184850] Fixed MDIO Bus: probed
            PPP generic driver version 2.4.2
[ 2.184862]
[ 2.184973] input: Macintosh mouse button emulation as /devices/virtual/input/input3
            Driver 'sd' needs updating - please use bus_type methods
[ 2.185034]
[ 2.185048] Driver 'sr' needs updating - please use bus_type methods
            pata_via 0000:00:07.1: version 0.3.3
[ 2.185836]
[ 2.185877] pata_via 0000:00:07.1: power state changed by ACPI to D0
            pata_via 0000:00:07.1: setting latency timer to 64
[ 2.186043]
[ 2.186298] scsi0 : pata_via
            scsi1 : pata_via
[ 2.186518]
[ 2.187618] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c40 irq 14
            ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c48 irq 15
[ 2.187623]
[ 2.187679] ata1: port disabled. ignoring.
            ata2.01: NODEV after polling detection
[ 2.340228]
[ 2.348574] ata2.00: ATAPI: UJDA730 DVD/CDRW, 1.00, max UDMA/33
[ 2.364740] ata2.00: configured for UDMA/33
[ 2.373908] scsi 1:0:0:0: CD-ROM          MATSHITA UJDA730 DVD/CDRW 1.00 PQ: 0 ANSI: 5
            sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 2.376142]
            Uniform CD-ROM driver Revision: 3.20
[ 2.376149]
[ 2.376366] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2.376473] sr 1:0:0:0: Attached scsi generic sg0 type 5
            ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 2.376738]
            ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.376767]
[ 2.376787] uhci_hcd: USB Universal Host Controller Interface driver
[ 2.377310] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
            uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[ 2.377319]
[ 2.377337] uhci_hcd 0000:00:07.2: setting latency timer to 64
[ 2.377342] uhci_hcd 0000:00:07.2: UHCI Host Controller
            uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[ 2.377465]
[ 2.377498] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001c00
[ 2.377692] usb usb1: configuration #1 chosen from 1 choice
[ 2.377740] hub 1-0:1.0: USB hub found
[ 2.377762] hub 1-0:1.0: 2 ports detected
[ 2.377927] uhci_hcd 0000:00:07.3: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[ 2.377939] uhci_hcd 0000:00:07.3: setting latency timer to 64
[ 2.377943] uhci_hcd 0000:00:07.3: UHCI Host Controller
[ 2.378006] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[ 2.378027] uhci_hcd 0000:00:07.3: irq 9, io base 0x00001c20
[ 2.378149] usb usb2: configuration #1 chosen from 1 choice
[ 2.378196] hub 2-0:1.0: USB hub found
[ 2.378212] hub 2-0:1.0: 2 ports detected
[ 2.378380] usbcore: registered new interface driver libusual
[ 2.378439] usbcore: registered new interface driver usbserial
[ 2.378457] USB Serial support registered for generic
[ 2.378486] usbcore: registered new interface driver usbserial_generic
[ 2.378490] usbserial: USB Serial Driver core
[ 2.378565] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 2.383284] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.383295] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2.383481] mice: PS/2 mouse device common for all mice
[ 2.383741] rtc_cmos 00:02: RTC can wake from S4
[ 2.383801] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[ 2.383830] rtc0: alarms up to one year, y3k, 242 bytes nvram
[ 2.383993] device-mapper: uevent: version 1.0.3
[ 2.384233] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[ 2.384337] device-mapper: multipath: version 1.0.5 loaded
[ 2.384343] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2.384507] EISA: Probing bus 0 at eisa.0
[ 2.384521] Cannot allocate resource for EISA slot 1
[ 2.384526] Cannot allocate resource for EISA slot 2
[ 2.384545] Cannot allocate resource for EISA slot 6
[ 2.384552] Cannot allocate resource for EISA slot 8
[ 2.384555] EISA: Detected 0 cards.
[ 2.384653] cpuidle: using governor ladder
[ 2.384719] cpuidle: using governor menu
[ 2.385583] TCP cubic registered
[ 2.385730] NET: Registered protocol family 10
[ 2.386378] lo: Disabled Privacy Extensions
            NET: Registered protocol family 17
[ 2.386886]
[ 2.386920] Bluetooth: L2CAP ver 2.11
[ 2.386923] Bluetooth: L2CAP socket layer initialized
[ 2.386928] Bluetooth: SCO (Voice Link) ver 0.6
[ 2.386931] Bluetooth: SCO socket layer initialized
[ 2.386993] Bluetooth: RFCOMM socket layer initialized
[ 2.387020] Bluetooth: RFCOMM TTY layer initialized
[ 2.387023] Bluetooth: RFCOMM ver 1.10
[ 2.387080] powernow-k8: Processor cpuid 680 not supported
[ 2.387191] powernow: PowerNOW! T    echnology present. Can scale: frequency and voltage.
[ 2.394031] powernow: SGTC: 10000
[ 2.394035] powernow: Minimum speed 499 MHz. Maximum speed 1399 MHz.
            IO APIC resources could be not be allocated.
[ 2.394120]
[ 2.394178] Using IPI No-Shortcut mode
[ 2.394366] registered taskstats version 1
[ 2.394578]  Magic number: 8:186:358
            rtc_cmos 00:02: setting system clock to 2000-06-02 02:22:31 UTC (959912551)
[ 2.394745]
[ 2.394750] BIOS EDD facility v0.16 2004- Jun-25, 0 devices found
[ 2.394753] EDD information not available.
[ 2.396167] Freeing unused kernel memory: 532k freed
[ 2.396364] Write protecting the kernel text: 4128k
[ 2.396424] Write protecting the kernel read-only data: 1532k
[ 2.435920] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 2.533170] compcache: Compressed swap size set to: 62708 KB
[ 2.533639] TLSF: pool: d08be000, init_size=16384, max_size=0, grow_size=16384
[ 2.692075] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 2.865749] usb 1-2: configuration #1 chosen from 1 choice
[ 3.136256] Floppy drive(s): fd0 is 1.44M
[ 3.155792] FDC 0 is a post-1991 82077
[ 3.497420] usbcore: registered new interface driver hiddev
[ 3.514350] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input5
[ 3.548233] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on
usb-0000:00:07.2-2/input0
[ 3.548279] usbcore: registered new interface driver usbhid
[ 3.548287] usbhid: v2.6:USB HID core driver
[ 3.698331] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 3.698405] 8139cp 0000:00:10.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[ 3.703020] 8139too Fast Ethernet driver 0.9.28
[ 3.703284] 8139too 0000:00:10.0: power state changed by ACPI to D0
[ 3.703306] 8139too 0000:00:10.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[ 3.713910] eth0: RealT RTL8139 at 0x1800, 08:00:46:90:b3:f7, IRQ 10
                        ek
[ 3.713918] eth0: Identified 8139 chip type 'RTL-8139C'
[ 3.714398] ohci1394 0000:00:0e.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[ 3.714408] ohci1394 0000:00:0e.0: setting latency timer to 64
[ 3.765445] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9] MMIO=[e8004000-e80047ff] Max
Packet=[2048] IR/IT contexts=[4/8]
[ 4.511336] Adding 62704k swap on /dev/ramzswap0. Priority:100 extents:1 across:62704k
[ 5.077776] Marking TSC unstable due to TSC halts in idle
[ 5.100328] ieee1394: Host added: ID:BUS[0-00:1023] GUID[08004603014c1cf9]
[ 5.665775] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 5.737680] ISO 9660 Extensions: RRIP_1991A
[ 6.824828] aufs 20080922
[ 7.140225] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[ 10.488744] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 141.071997] udev: starting version 141
[ 145.881954] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 146.108629] Linux agpgart interface v0.103
[ 146.362337] input: PC Speaker as /devices/platform/pcspkr/input/input6
[ 146.602141] input: Video Bus
as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03/input/input7
[ 146.612247] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
[ 146.755146] yenta_cardbus 0000:00:0a.0: CardBus bridge found [104d:80f6]
[ 146.755173] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
[ 146.755179] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[ 146.755183] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[ 146.755189] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x012c1222, devctl 0x66
[ 146.755349] parport_pc: VIA 686A/8231 detected
[ 146.755353] parport_pc: probing current configuration
[ 146.755369] parport_pc: Current parallel port base: 0x378
[ 146.755444] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[ 146.852133] parport_pc: VIA parallel port: io=0x378, irq=7
[ 146.986073] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0808, PCI irq 9
[ 146.986083] yenta_cardbus 0000:00:0a.0: Socket status: 30000006
  146.991012] yenta_cardbus 0000:00:0a.1: CardBus bridge found [104d:80f6]
[ 146.991033] yenta_cardbus 0000:00:0a.1: Using CSCINT to route CSC interrupts to PCI
[ 146.991037] yenta_cardbus 0000:00:0a.1: Routing CardBus interrupts to PCI
[ 146.991043] yenta_cardbus 0000:00:0a.1: TI: mfunc 0x012c1222, devctl 0x66
[ 147.101957] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 147.221132] yenta_cardbus 0000:00:0a.1: ISA IRQ mask 0x0808, PCI irq 10
[ 147.221142] yenta_cardbus 0000:00:0a.1: Socket status: 30000006
[ 147.236553] agpgart: Detected VIA T  wister-K/KT133x/KM133 chipset
[ 147.249111] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[ 147.331459] ppdev: user-space parallel port driver
[ 147.698042] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[ 147.737978] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[ 147.812836] VIA 82xx Modem 0000:00:07.6: power state changed by ACPI to D0
[ 147.813231] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[ 147.813237] PCI: setting IRQ 5 as level-triggered
[ 147.813246] VIA 82xx Modem 0000:00:07.6: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[ 147.816179] VIA 82xx Modem 0000:00:07.6: setting latency timer to 64
[ 148.215661] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[ 148.218033] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[ 148.219014] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[ 148.219856] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[ 148.221018] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[ 148.224312] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[ 148.226616] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[ 148.227590] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[ 148.228463] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[ 148.229578] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[ 148.424090] MC'97 1 converters and GPIO not ready (0xff00)
[ 148.579118] VIA 82xx Audio 0000:00:07.5: power state changed by ACPI to D0
[ 148.579145] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[ 148.579292] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[ 178.514988] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 178.514999] Bluetooth: BNEP filters: protocol multicast
[ 178.593798] Bridge firewalling registered
[ 195.898166] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 202.276446] lp0: using parport0 (interrupt-driven).
[ 206.500038] eth0: no IPv6 routers present
[ 294.280078] Clocksource tsc unstable (delta = -188622914 ns)

---

