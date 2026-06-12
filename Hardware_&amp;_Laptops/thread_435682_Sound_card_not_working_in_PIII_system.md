---
title: "Sound card not working in PIII system"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by SoundFriend on 2007-05-07
Hi,
Yes, it's the sound card not working problem again.  I'd be grateful for any help.

lspci says:```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
00:0d.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
00:0f.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)

```

and ismod says: ```

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
dock                   10268  0 
video                  16388  0 
ac                      6020  0 
battery                10756  0 
sbs                    15652  0 
container               5248  0 
button                  8720  0 
i2c_ec                  5888  1 sbs
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268704  8 
lp                     12452  0 
fuse                   46612  1 
snd_maestro3           27012  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
psmouse                38920  0 
nvidia               4713780  22 
pcspkr                  4224  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_ymfpci             62368  1 
gameport               16520  1 snd_ymfpci
i2c_piix4               9740  0 
snd_ac97_codec         98336  2 snd_maestro3,snd_ymfpci
intel_agp              25116  1 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_maestro3,snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           11520  1 snd_ymfpci
snd_hwdep               9988  1 snd_opl3_lib
snd_page_alloc         10888  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         9472  1 snd_ymfpci
agpgart                35400  2 nvidia,intel_agp
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_timer              23684  4 snd_seq,snd_ymfpci,snd_pcm,snd_opl3_lib
snd_seq_device          9100  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_opl3_lib,snd_rawmidi
snd                    54020  16 snd_maestro3,snd_seq_oss,snd_seq,snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_timer,snd_seq_device
soundcore               8672  1 snd
i2c_core               22784  3 i2c_ec,nvidia,i2c_piix4
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  2 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
piix                   10756  0 [permanent]
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

and dmesg says: ```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e7000 size: 0000000000019000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000013efdc00 end: 0000000013ffdc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000013ffdc00 size: 0000000000002000 end: 0000000013fffc00 type: 3
[    0.000000] copy_e820_map() start: 0000000013fffc00 size: 0000000000000400 end: 0000000014000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffe7000 size: 0000000000019000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000013ffdc00 (usable)
[    0.000000]  BIOS-e820: 0000000013ffdc00 - 0000000013fffc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000013fffc00 - 0000000014000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 319MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 81917) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    81917
[    0.000000]   HighMem     81917 ->    81917
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81917
[    0.000000] On node 0 totalpages: 81917
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 607 pages used for memmap
[    0.000000]   Normal zone: 77214 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ad0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001 PTL  0x01000000) @ 0x13ffdd96
[    0.000000] ACPI: FADT (v001 INTEL  SEATTLE2 0x20000301 PTL  0x000f4240) @ 0x13fffb8c
[    0.000000] ACPI: DSDT (v001  Intel  S2440BX 0x00000001 MSFT 0x01000004) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebfe7000)
[    0.000000] Detected 648.538 MHz processor.
[  129.466430] Built 1 zonelists.  Total pages: 81278
[  129.466440] Kernel command line: root=UUID=ae4df8d7-e492-43dd-b982-0cd1f2b8fb2d ro quiet splash
[  129.467039] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  129.467060] mapped APIC to ffffd000 (0128b000)
[  129.467071] Enabling fast FPU save and restore... done.
[  129.467079] Enabling unmasked SIMD FPU exception support... done.
[  129.467102] Initializing CPU#0
[  129.467204] PID hash table entries: 2048 (order: 11, 8192 bytes)
[  129.468621] Console: colour VGA+ 80x25
[  129.469696] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  129.471072] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  129.505077] Memory: 313408k/327668k available (1992k kernel code, 13656k reserved, 893k data, 328k init, 0k highmem)
[  129.505111] virtual kernel memory layout:
[  129.505115]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[  129.505120]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  129.505125]     vmalloc : 0xd4800000 - 0xff7fe000   ( 687 MB)
[  129.505129]     lowmem  : 0xc0000000 - 0xd3ffd000   ( 319 MB)
[  129.505134]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[  129.505138]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[  129.505143]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[  129.505154] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  129.583141] Calibrating delay using timer specific routine.. 1298.20 BogoMIPS (lpj=2596402)
[  129.583265] Security Framework v1.0.0 initialized
[  129.583284] SELinux:  Disabled at boot.
[  129.583334] Mount-cache hash table entries: 512
[  129.583697] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  129.583729] CPU: L1 I cache: 16K, L1 D cache: 16K
[  129.583738] CPU: L2 cache: 256K
[  129.583747] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  129.583777] Compat vDSO mapped to ffffe000.
[  129.583796] Remapping vsyscall page to ffffe000
[  129.583822] Checking 'hlt' instruction... OK.
[  129.599369] SMP alternatives: switching to UP code
[  129.599797] Freeing SMP alternatives: 11k freed
[  129.600323] Early unpacking initramfs... done
[  130.581422] ACPI: Core revision 20060707
[  130.582397] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[  130.584661] ACPI: setting ELCR to 0200 (from 0e00)
[  130.585977] CPU0: Intel Pentium III (Coppermine) stepping 03
[  130.585993] SMP motherboard not detected.
[  130.586000] Local APIC not detected. Using dummy APIC emulation.
[  130.586113] Brought up 1 CPUs
[  130.586824] Booting paravirtualized kernel on bare hardware
[  130.586976] Time: 10:55:30  Date: 04/07/107
[  130.587062] NET: Registered protocol family 16
[  130.587320] EISA bus registered
[  130.587334] ACPI: bus type pci registered
[  130.587786] PCI: PCI BIOS revision 2.10 entry at 0xfd9b4, last bus=1
[  130.587794] PCI: Using configuration type 1
[  130.587800] Setting up standard PCI resources
[  130.593781] ACPI: Interpreter enabled
[  130.593794] ACPI: Using PIC for interrupt routing
[  130.594626] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  130.594643] PCI: Probing PCI hardware (bus 00)
[  130.594686] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[  130.598333] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[  130.598339] * this clock source is slow. Consider trying other clock sources
[  130.598397] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[  130.598407] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[  130.598782] Boot video device is 0000:01:00.0
[  130.598847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  130.601825] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[  130.602437] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[  130.603110] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[  130.603676] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[  130.603975] ACPI: Power Resource [PFAN] (on)
[  130.610493] Linux Plug and Play Support v0.97 (c) Adam Belay
[  130.610528] pnp: PnP ACPI init
[  130.621998] pnp: PnP ACPI: found 12 devices
[  130.622014] PnPBIOS: Disabled by ACPI PNP
[  130.622172] PCI: Using ACPI for IRQ routing
[  130.622182] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  130.623991] NET: Registered protocol family 8
[  130.623999] NET: Registered protocol family 20
[  130.624240] pnp: 00:01: ioport range 0x7000-0x700f has been reserved
[  130.624251] pnp: 00:01: ioport range 0x8000-0x803f could not be reserved
[  130.625131] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:01:00.0
[  130.625199] PCI: Bridge: 0000:00:01.0
[  130.625204]   IO window: disabled.
[  130.625215]   MEM window: e9000000-e9ffffff
[  130.625225]   PREFETCH window: f0000000-f7ffffff
[  130.625312] NET: Registered protocol family 2
[  130.658728] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  130.658969] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[  130.659379] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  130.659622] TCP: Hash tables configured (established 16384 bind 8192)
[  130.659632] TCP reno registered
[  130.670924] checking if image is initramfs... it is
[  132.545339] Freeing initrd memory: 6998k freed
[  132.546428] audit: initializing netlink socket (disabled)
[  132.546466] audit(1178535332.268:1): initialized
[  132.546838] VFS: Disk quotas dquot_6.5.1
[  132.546906] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  132.547039] io scheduler noop registered
[  132.547048] io scheduler anticipatory registered
[  132.547055] io scheduler deadline registered
[  132.547087] io scheduler cfq registered (default)
[  132.547109] Limiting direct PCI/PCI transfers.
[  132.547698] isapnp: Scanning for PnP cards...
[  132.901688] isapnp: No Plug & Play device found
[  132.992979] Real Time Clock Driver v1.12ac
[  132.993104] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  132.993425] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  132.993871] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  132.995445] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  132.996045] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  132.996751] mice: PS/2 mouse device common for all mice
[  132.998532] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  132.999216] input: Macintosh mouse button emulation as /class/input/input0
[  132.999321] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  132.999334] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  132.999803] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MICE] at 0x60,0x64 irq 1,12
[  133.002936] serio: i8042 KBD port at 0x60,0x64 irq 1
[  133.002952] serio: i8042 AUX port at 0x60,0x64 irq 12
[  133.003308] EISA: Probing bus 0 at eisa.0
[  133.003328] Cannot allocate resource for EISA slot 1
[  133.003364] Cannot allocate resource for EISA slot 7
[  133.003371] Cannot allocate resource for EISA slot 8
[  133.003377] EISA: Detected 0 cards.
[  133.033608] TCP cubic registered
[  133.033632] NET: Registered protocol family 1
[  133.033693] Using IPI No-Shortcut mode
[  133.033851] ACPI: (supports S0 S1 S5)
[  133.033961]   Magic number: 7:468:931
[  133.035268] Freeing unused kernel memory: 328k freed
[  133.037136] Time: tsc clocksource has been installed.
[  133.049562] input: AT Translated Set 2 keyboard as /class/input/input1
[  134.765109] Capability LSM initialized
[  134.875508] ACPI: Fan [FAN1] (on)
[  134.888323] ACPI: CPU0 (power states: C1[C1] C2[C2])
[  136.374887] PIIX4: IDE controller at PCI slot 0000:00:07.1
[  136.374919] PIIX4: chipset revision 1
[  136.374926] PIIX4: not 100% native mode: will probe irqs later
[  136.374943]     ide0: BM-DMA at 0x14a0-0x14a7, BIOS settings: hda:DMA, hdb:pio
[  136.374969]     ide1: BM-DMA at 0x14a8-0x14af, BIOS settings: hdc:pio, hdd:DMA
[  136.374987] Probing IDE interface ide0...
[  136.428971] usbcore: registered new interface driver usbfs
[  136.429034] usbcore: registered new interface driver hub
[  136.429106] usbcore: registered new device driver usb
[  136.433553] USB Universal Host Controller Interface driver v3.0
[  136.745908] Floppy drive(s): fd0 is 1.44M
[  136.751175] hda: IC35L060AVVA07-0, ATA DISK drive
[  136.916458] FDC 0 is a post-1991 82077
[    7.544000] Time: acpi_pm clocksource has been installed.
[    7.964000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.964000] Probing IDE interface ide1...
[    8.364000] hdc: SAMSUNG CD-R/RW DRIVE SW-212B, ATAPI CD/DVD-ROM drive
[    9.148000] hdd: ATAPI DVD-ROM, ATAPI CD/DVD-ROM drive
[    9.204000] ide1 at 0x170-0x177,0x376 on irq 15
[    9.232000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    9.232000] PCI: setting IRQ 9 as level-triggered
[    9.232000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    9.232000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    9.236000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    9.236000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001480
[    9.236000] usb usb1: configuration #1 chosen from 1 choice
[    9.236000] hub 1-0:1.0: USB hub found
[    9.236000] hub 1-0:1.0: 2 ports detected
[    9.240000] SCSI subsystem initialized
[    9.272000] libata version 2.20 loaded.
[    9.340000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    9.340000] PCI: setting IRQ 10 as level-triggered
[    9.340000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[    9.340000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[    9.340000] 0000:00:0f.0: 3Com PCI 3c905B Cyclone 100baseTx at d4850000.
[    9.360000]  ***INVALID CHECKSUM 0020*** <6>hda: max request size: 128KiB
[    9.460000] hda: 120103200 sectors (61492 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(33)
[    9.460000] hda: cache flushes supported
[    9.464000]  hda: hda1 hda2 hda3 < hda5 >
[    9.484000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 8192kB Cache, DMA
[    9.484000] Uniform CD-ROM driver Revision: 3.20
[    9.488000] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    9.976000] Attempting manual resume
[    9.976000] swsusp: Resume From Partition 3:5
[    9.976000] PM: Checking swsusp image.
[    9.992000] PM: Resume from disk failed.
[   10.076000] kjournald starting.  Commit interval 5 seconds
[   10.076000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.520000] eth0:  setting full-duplex.
[   23.168000] NET: Registered protocol family 17
[   24.620000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.632000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.372000] Linux agpgart interface v0.102 (c) Dave Jones
[   26.640000] agpgart: Detected an Intel 440BX Chipset.
[   26.644000] agpgart: AGP aperture is 64M @ 0xec000000
[   26.708000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   27.260000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   27.628000] input: PC Speaker as /class/input/input2
[   27.732000] nvidia: module license 'NVIDIA' taints kernel.
[   28.156000] parport: PnPBIOS parport detected.
[   28.156000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   28.756000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   28.812000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   28.812000] PCI: setting IRQ 11 as level-triggered
[   28.812000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   28.816000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   28.816000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.280000] fuse init (API version 7.8)
[   30.320000] lp0: using parport0 (interrupt-driven).
[   30.408000] Adding 939760k swap on /dev/disk/by-uuid/3590c127-3f12-46d7-8030-d845a60d78ea.  Priority:-1 extents:1 across:939760k
[   30.564000] EXT3 FS on hda2, internal journal
[   30.992000] NET: Registered protocol family 10
[   30.992000] lo: Disabled Privacy Extensions
[   31.136000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   38.616000] ibm_acpi: ec object not found
[   38.808000] input: Power Button (FF) as /class/input/input4
[   38.808000] ACPI: Power Button (FF) [PWRF]
[   39.172000] Using specific hotkey driver
[   39.240000] No dock devices found.
[   39.292000] pcc_acpi: loading...
[   41.448000] eth0: no IPv6 routers present
[   48.248000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   48.248000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   48.252000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   48.556000] ppdev: user-space parallel port driver
[   48.804000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   48.808000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   48.808000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   50.760000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   50.760000] apm: overridden by ACPI.
[   51.404000] Bluetooth: Core ver 2.11
[   51.404000] NET: Registered protocol family 31
[   51.404000] Bluetooth: HCI device and connection manager initialized
[   51.404000] Bluetooth: HCI socket layer initialized
[   51.640000] Bluetooth: L2CAP ver 2.8
[   51.640000] Bluetooth: L2CAP socket layer initialized
[   51.656000] Bluetooth: RFCOMM socket layer initialized
[   51.656000] Bluetooth: RFCOMM TTY layer initialized
[   51.656000] Bluetooth: RFCOMM ver 1.8
[   60.936000] eth0: no IPv6 routers present

```

There does appear to be a problem assigning interrupts, which might be the problem, but I don't know how to fix this.  Help?

SF

---

### Post by SoundFriend on 2007-05-07
I found a conflict between two audio playback devices, and resolved it by disabling one in the BIOS.

Now working  :) 

SF

---

