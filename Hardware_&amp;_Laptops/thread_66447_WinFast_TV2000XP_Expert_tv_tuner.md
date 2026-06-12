---
title: "WinFast TV2000XP Expert tv tuner"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by zerooo on 2005-09-17
Hello, i have a WinFast TV2000XP Expert TV tuner from Leadtek and want to make it work on ubuntu. I tried to set it up earlier on linux, but failed (black&white and no sound) So i want ask you how to set up it correctly. Here is my lspci, lsmod and dmesg outputs:
**lspci:** 
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 A GP]
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:0b.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:14.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
0000:00:14.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  0a)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200 ] (rev a3)
```
**lsmod:** 
```
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
ipt_TCPMSS              4096  1
ipt_tcpmss              2304  1
iptable_filter          2944  1
ip_tables              18176  3 ipt_TCPMSS,ipt_tcpmss,iptable_filter
video                  16004  0
sony_acpi               5516  0
pcc_acpi               11392  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
pppoe                  13120  2
pppox                   3464  1 pppoe
ipv6                  217408  8
af_packet              20232  2
ppp_generic            25748  6 pppoe,pppox
slhc                    6656  1 ppp_generic
tsdev                   7616  0
snd_mpu401              6344  0
snd_mpu401_uart         6784  1 snd_mpu401
analog                 10528  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
emu10k1_gp              3712  0
gameport               14472  3 analog,emu10k1_gp
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  2 snd_emu10k1_synth
snd_rawmidi            22816  4 snd_mpu401_uart,snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         71804  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  17 snd_mpu401,snd_mpu401_uart,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
i2c_viapro              7696  0
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
tda9887                13208  0
tuner                  24488  0
cx8800                 28812  0
cx88xx                 50976  1 cx8800
i2c_algo_bit            8584  1 cx88xx
video_buf              19844  2 cx8800,cx88xx
ir_common               7428  1 cx88xx
tveeprom               12568  1 cx88xx
i2c_core               19728  7 i2c_acpi_ec,i2c_viapro,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom
v4l1_compat            12420  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4872  2 cx8800,cx88xx
videodev                9344  2 cx8800,cx88xx
pci_hotplug            24628  0
via_agp                 9472  1
dm_mod                 50364  1
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  2 via_agp,nvidia
psmouse                25988  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
vga16fb                12232  1
vgastate                8320  1 vga16fb
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
usbhid                 30688  0
uhci_hcd               28048  0
usbcore               104188  3 usbhid,uhci_hcd
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
unix                   24624  688
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  2 vga16fb,vesafb
cfbimgblt               2944  2 vga16fb,vesafb
cfbfillrect             3840  2 vga16fb,vesafb
softcursor              2432  2 vga16fb,vesafb
capability              5000  0
commoncap               6784  1 capability
```
**dmesg:**
```
[4294667.687000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.689000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.706000] Memory: 511364k/524224k available (1415k kernel code, 12252k reserved, 763k data, 224k init, 0k highmem)[4294667.706000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.706000] Calibrating delay loop... 3039.23 BogoMIPS (lpj=1519616)
[4294667.728000] Security Framework v1.0.0 initialized
[4294667.728000] SELinux:  Disabled at boot.
[4294667.728000] Mount-cache hash table entries: 512
[4294667.728000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.728000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.728000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.728000] CPU: L2 Cache: 256K (64 bytes/line)
[4294667.728000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294667.728000] CPU: AMD Athlon(tm) XP 1800+ stepping 02
[4294667.728000] Enabling fast FPU save and restore... done.
[4294667.728000] Enabling unmasked SIMD FPU exception support... done.
[4294667.728000] Checking 'hlt' instruction... OK.
[4294667.732000] Checking for popad bug... OK.
[4294667.732000] checking if image is initramfs... it is
[4294668.192000] Freeing initrd memory: 4672k freed
[4294668.193000] ACPI: Looking for DSDT in initrd... not found!
[4294668.253000]  not found!
[4294668.260000] ACPI: setting ELCR to 0200 (from 1a20)
[4294668.478000] NET: Registered protocol family 16
[4294668.478000] EISA bus registered
[4294668.478000] ACPI: bus type pci registered
[4294668.478000] PCI: PCI BIOS revision 2.10 entry at 0xfb460, last bus=1
[4294668.478000] PCI: Using configuration type 1
[4294668.478000] mtrr: v2.0 (20020519)
[4294668.479000] ACPI: Subsystem revision 20050729
[4294668.484000] ACPI: Interpreter enabled
[4294668.484000] ACPI: Using PIC for interrupt routing
[4294668.485000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.485000] PCI: Probing PCI hardware (bus 00)
[4294668.485000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.485000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294668.487000] Boot video device is 0000:01:00.0
[4294668.507000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.508000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294668.509000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[4294668.509000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294668.509000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[4294668.513000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.513000] pnp: PnP ACPI init
[4294668.518000] pnp: PnP ACPI: found 13 devices
[4294668.518000] PnPBIOS: Disabled by ACPI PNP
[4294668.518000] PCI: Using ACPI for IRQ routing
[4294668.518000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.539000] audit: initializing netlink socket (disabled)
[4294668.539000] audit: initialized
[4294668.539000] VFS: Disk quotas dquot_6.5.1
[4294668.539000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.539000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.539000] devfs: boot_options: 0x0
[4294668.539000] Initializing Cryptographic API
[4294668.539000] isapnp: Scanning for PnP cards...
[4294668.893000] isapnp: No Plug & Play device found
[4294668.913000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294668.913000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294668.913000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.913000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.913000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.913000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.914000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.916000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.916000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.916000] io scheduler noop registered
[4294668.916000] io scheduler anticipatory registered
[4294668.916000] io scheduler deadline registered
[4294668.916000] io scheduler cfq registered
[4294668.916000] RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
[4294668.917000] EISA: Probing bus 0 at eisa.0
[4294668.917000] Cannot allocate resource for EISA slot 4
[4294668.917000] EISA: Detected 0 cards.
[4294668.917000] NET: Registered protocol family 2
[4294668.927000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.927000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294668.927000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.928000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.928000] NET: Registered protocol family 8
[4294668.928000] NET: Registered protocol family 20
[4294668.928000] ACPI wakeup devices:
[4294668.928000] SLPB PCI0 USB0 USB1 USB2 LAN0 UAR1 LPT1
[4294668.928000] ACPI: (supports S0 S1 S4 S5)
[4294668.928000] Freeing unused kernel memory: 224k freed
[4294668.966000] Capability LSM initialized
[4294668.981000] NET: Registered protocol family 1
[4294668.984000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.009000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294669.009000] 8139cp: pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294669.009000] 8139cp: Try the "8139too" driver instead.
[4294669.011000] 8139too Fast Ethernet driver 0.9.27
[4294669.012000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[4294669.012000] PCI: setting IRQ 12 as level-triggered
[4294669.012000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[4294669.012000] eth0: RealTek RTL8139 at 0xd000, 00:08:a1:35:99:bd, IRQ 12
[4294669.012000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294669.041000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.041000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.041000] ACPI: bus type ide registered
[4294669.052000] usbcore: registered new driver usbfs
[4294669.052000] usbcore: registered new driver hub
[4294669.054000] USB Universal Host Controller Interface driver v2.2
[4294669.054000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294669.054000] PCI: setting IRQ 11 as level-triggered
[4294669.054000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294669.054000] PCI: Via IRQ fixup for 0000:00:11.2, from 9 to 11
[4294669.054000] uhci_hcd 0000:00:11.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294669.116000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[4294669.116000] uhci_hcd 0000:00:11.2: irq 11, io base 0x0000d800
[4294669.116000] hub 1-0:1.0: USB hub found
[4294669.116000] hub 1-0:1.0: 2 ports detected
[4294669.119000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294669.119000] PCI: Via IRQ fixup for 0000:00:11.3, from 9 to 11
[4294669.119000] uhci_hcd 0000:00:11.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294669.181000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[4294669.181000] uhci_hcd 0000:00:11.3: irq 11, io base 0x0000dc00
[4294669.181000] hub 2-0:1.0: USB hub found
[4294669.181000] hub 2-0:1.0: 2 ports detected
[4294669.411000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294671.239000] usbcore: registered new driver hiddev
[4294671.257000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:11.2-2
[4294671.257000] usbcore: registered new driver usbhid
[4294671.257000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294671.268000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294671.269000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294671.269000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294671.269000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 11
[4294671.269000] VP_IDE: chipset revision 6
[4294671.269000] VP_IDE: not 100% native mode: will probe irqs later
[4294671.269000] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294671.269000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
[4294671.269000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:pio, hdd:DMA
[4294671.269000] Probing IDE interface ide0...
[4294671.653000] hda: Maxtor 6E040L0, ATA DISK drive
[4294671.908000] hdb: Maxtor 90648D3, ATA DISK drive
[4294671.959000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.959000] Probing IDE interface ide1...
[4294673.006000] hdd: LITE-ON DVDRW SOHW-1673S, ATAPI CD/DVD-ROM drive
[4294673.057000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.057000] Probing IDE interface ide2...
[4294673.570000] Probing IDE interface ide3...
[4294674.082000] Probing IDE interface ide4...
[4294674.594000] Probing IDE interface ide5...
[4294675.109000] hda: max request size: 128KiB
[4294675.817000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[4294675.818000] hda: cache flushes supported
[4294675.818000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294675.847000] hdb: max request size: 128KiB
[4294676.769000] hdb: 12656448 sectors (6480 MB) w/512KiB Cache, CHS=12556/16/63, UDMA(33)
[4294676.769000] hdb: cache flushes not supported
[4294676.769000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294676.779000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294676.779000] Uniform CD-ROM driver Revision: 3.20
[4294677.083000] ACPI: Fan [FAN] (on)
[4294677.087000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294677.087000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294677.089000] ACPI: Thermal Zone [THRM] (45 C)
[4294677.096000] vga16fb: initializing
[4294677.096000] vga16fb: mapped to 0xc00a0000
[4294677.224000] Console: switching to colour frame buffer device 80x30
[4294677.224000] fb0: VGA16 VGA frame buffer device
[4294677.407000] Attempting manual resume
[4294677.431000] swsusp: Suspend partition has wrong signature?
[4294677.461000] kjournald starting.  Commit interval 5 seconds
[4294677.461000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.706000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.240000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
[4294682.443000] EXT3 FS on hda1, internal journal
[4294688.131000] parport: PnPBIOS parport detected.
[4294688.131000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294688.215000] lp0: using parport0 (interrupt-driven).
[4294688.233000] mice: PS/2 mouse device common for all mice
[4294688.254000] Linux agpgart interface v0.101 (c) Dave Jones
[4294688.290000] nvidia: module license 'NVIDIA' taints kernel.
[4294688.298000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294688.299000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294691.080000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294691.789000] cdrom: open failed.
[4294694.259000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4294694.283000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294694.383000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.390000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294694.390000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294694.582000] Linux video capture interface: v1.00
[4294694.653000] cx2388x v4l2 driver version 0.0.4 loaded
[4294694.659000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294694.659000] PCI: setting IRQ 5 as level-triggered
[4294694.659000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294694.659000] cx88[0]: subsystem: 107d:6611, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[4294694.821000] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=38, eeprom[0]=0x01
[4294694.867000] cx88[0]: registered IR remote control
[4294694.867000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 5, latency: 32, mmio: 0xe6000000
[4294694.886000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[4294694.886000] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[4294694.949000] tda9885/6/7: chip found @ 0x86
[4294694.975000] cx88[0]/0: registered device video0 [v4l2]
[4294694.977000] cx88[0]/0: registered device vbi0
[4294694.978000] cx88[0]/0: registered device radio0
[4294695.220000] irda_init()
[4294695.220000] NET: Registered protocol family 23
[4294695.744000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294696.747000] gameport: EMU10K1 is pci0000:00:14.1/gameport0, io 0xec00, speed 1193kHz
[4294698.391000] Real Time Clock Driver v1.12
[4294698.479000] input: PC Speaker
[4294698.571000] Floppy drive(s): fd0 is 1.44M
[4294698.588000] FDC 0 is a post-1991 82077
[4294699.494000] ts: Compaq touchscreen protocol output
[4294700.024000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294700.215000] CSLIP: code copyright 1989 Regents of the University of California
[4294700.219000] PPP generic driver version 2.4.2
[4294700.244000] NET: Registered protocol family 17
[4294700.262000] NET: Registered protocol family 10
[4294700.262000] Disabled Privacy Extensions on device c02eb280(lo)
[4294700.263000] IPv6 over IPv4 tunneling driver
[4294700.598000] NET: Registered protocol family 24
[4294702.909000] ACPI: Power Button (FF) [PWRF]
[4294702.909000] ACPI: Power Button (CM) [PWRB]
[4294702.909000] ACPI: Sleep Button (CM) [SLPB]
[4294702.997000] Using specific hotkey driver
[4294703.050000] ibm_acpi: ec object not found
[4294704.557000] ip_tables: (C) 2000-2002 Netfilter core team
[4294708.080000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294708.080000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294708.080000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294708.455000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294708.455000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294708.455000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294710.289000] eth0: no IPv6 routers present
[4294713.756000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294713.756000] apm: overridden by ACPI.
[4294714.552000] Bluetooth: Core ver 2.7
[4294714.552000] NET: Registered protocol family 31
[4294714.552000] Bluetooth: HCI device and connection manager initialized
[4294714.552000] Bluetooth: HCI socket layer initialized
[4294714.577000] Bluetooth: L2CAP ver 2.7
[4294714.577000] Bluetooth: L2CAP socket layer initialized
[4294714.629000] Bluetooth: RFCOMM ver 1.5
[4294714.629000] Bluetooth: RFCOMM socket layer initialized
[4294714.629000] Bluetooth: RFCOMM TTY layer initialized
[4297073.216000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4297073.216000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4297073.216000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4297073.537000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4297073.537000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4297073.538000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
```

If more info needed please ask. Don't be shy to help :)
Thanks in advance.

---

### Post by zerooo on 2005-09-17
Somehow i managed to get it working thx anyways :P

---

### Post by monkey.eat(banana) on 2005-09-21
How did you fix it/what was the problem?

I'm currently trying to decide between a Haupauge PVR150 and the RM version of the Leadtek card. The 150 is pricier so if you're happy with your TV2000 then i'll go for that one.

m.e(b)

---

### Post by beefbowel on 2007-11-12
how did you fix it?  don't you care about all of us out here with these nonfunctioning expert cards?  don't you feel guilty not posting how you fixed the problem?  i don't know how you can live with yourself.  : P

---

### Post by LeDechaine on 2008-02-01
IMHO these TV2000 XP Cards are only useful if you are deaf or if you like to look at the TV without having the sound because these cards can't seem to produce any freaking sound in linux.

---

### Post by LeDechaine on 2008-03-18
Correction: the problem is my Audigy 2 sound card.

Output from the TV Card goes to the Audigy 2 AUX Input, which is still useless under linux because of crappy drivers.

---

### Post by testecletes on 2008-04-01
> **LeDechaine said:**
> Correction: the problem is my Audigy 2 sound card.

Output from the TV Card goes to the Audigy 2 AUX Input, which is still useless under linux because of crappy drivers.


I'm running Gutsy (7.10) with a LeadTek Winfast 2000/XP card. I'm using tvtime to watch TV.

I have the same problem with the Audigy 2 Aux input not working. As a fix, I plugged the LINEOUT from the tuner into the Audigy's MIC jack.

 
In order to control the volume in tvtime, I edited  /etc/tvtime/tvtime.xml and /home/USER/.tvtime/tvtime.xml accordingly:

>   <!--
    This sets the mixer device and channel to use.  The format is device
    name:channel name.  Valid channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor
   -->
  <option name="MixerDevice" value="/dev/mixer:mic"/>


Downsides of this is that you don't get to use your mic, but I don't need one, so it works for me :)






EDITED:

I read that this is a bad idea (from the MythTV docs) because the Line-Out jack and the Mic In jacks have different powers, so it could do some potential damage. I got mine to work via enabling Analog Mix.

---

### Post by LeDechaine on 2008-04-01
Eh, i'm using a Winfast TV2000XP **Expert** card, so there's **no** lineout!

Thanks anyway! ;)

---

### Post by testecletes on 2008-04-01
Darn :-/

I just checked and I found out that I had the Deluxe edition which has the audio out and radio antenna in jack.

I really hope you get it working!

---

### Post by LeDechaine on 2008-04-03
I simply abandoned :p

I'll switch to XP (dual boot) when i'll really want to watch something. ;)

---

### Post by twistadias on 2008-04-03
> **monkey.eat(banana) said:**
> How did you fix it/what was the problem?

I'm currently trying to decide between a Haupauge PVR150 and the RM version of the Leadtek card. The 150 is pricier so if you're happy with your TV2000 then i'll go for that one.

m.e(b)

Please don't get this card. It doesnt have a hardware decoder which means theres more stress on the cpu. also it will NOT work in any of the windows media centers if you ever happen to switch back. On XP you will only be able to watch tv using the default app that comes with the product.

Gonna be installing linux on my media center once hardy comes out, so I hope this card works

---

