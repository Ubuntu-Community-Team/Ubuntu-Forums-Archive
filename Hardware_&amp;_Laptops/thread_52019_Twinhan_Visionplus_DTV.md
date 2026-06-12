---
title: "Twinhan Visionplus DTV"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by trollzor on 2005-07-26
I am a newbie working on getting [this card](http://www.mittoni.com.au/visionplus-dvbt-digital-tv-tuner-card-p-1558.html) (in Australia) working with Hoary and will write up a HOWTO once I am finished (fingers crossed). The only other info for ubuntu around seems to be [this](http://ubuntuforums.org/archive/index.php/t-17085.html) post from a while ago on Warty.

I got all the dvb userland apps in via synaptic (dvbstream,dvbtune,dvb-utils), and have been modprobing (by hand after boot):
[INDENT][COLOR=Olive]
dvb-bt8xx
videodev
bttv card=0x71 i2c_hw=1
dvb-core
dst dst_type=0
bttv
[/COLOR][/INDENT]
from when I had the card working in Fedora Core 3 which nets me this lsmod:

[INDENT][COLOR=Olive]# lsmod
Module                  Size  Used by
dvb_bt8xx              10116  0
dvb_core               74408  1 dvb_bt8xx
nxt6000                 6532  1 dvb_bt8xx
mt352                   5380  1 dvb_bt8xx
dst                    12040  1 dvb_bt8xx
bt878                  10552  2 dvb_bt8xx,dst
sp887x                  7172  1 dvb_bt8xx
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
binfmt_misc            11272  1
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
af_packet              20744  0
ipt_limit               2688  8
iptable_mangle          2944  0
ipt_LOG                 6656  8
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  1
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  6
ip_conntrack           43668  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ohci1394               31876  0
snd_bt87x              12612  0
tuner                  20388  0
bttv                  142928  2 dvb_bt8xx,bt878
video_buf              20484  1 bttv
firmware_class          9728  3 dvb_bt8xx,sp887x,bttv
i2c_algo_bit            9224  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4744  1 bttv
videodev                9728  1 bttv
usblp                  12032  0
e1000                  77748  0
tsdev                   7488  0
snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  5 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_ossusb_storage            64064  1
snd_timer              23300  2 snd_pcm
snd                    50276  9 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  3 snd_bt87x,snd_intel8x0,snd_pcm
sd_mod                 16784  2
ata_piix                8836  0
libata                 44548  1 ata_piix
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  6 usblp,usb_storage,usbhid,ehci_hcd,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_mch_agp          10000  0
intel_agp              20636  1
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
reiserfs              225616  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
i2c_isa                 2176  0
i2c_i801                8076  0
it87                   19748  0
i2c_sensor              3584  1 it87
i2c_core               21264  12 dvb_bt8xx,nxt6000,mt352,dst,sp887x,tuner,bttv,i2c_algo_bit,i2c_isa,i2c_i801,it87,i2c_sensor
nvidia               3923388  12
agpgart                31784  3 intel_mch_agp,intel_agp,nvidia
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  5 usb_storage,sd_mod,libata,sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  932
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb[/COLOR][/INDENT]


And I get this dmesg

[INDENT][COLOR=Olive]
 # dmesg
T Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
SLPB PCI0 CSAD HUB0 USB0 USB1 USB2 USB3 USBE
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: ST340016A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: DVD-ROM DDU1621, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: hda1: orphan cleanup on readonly fs
ext3_orphan_cleanup: deleting unreferenced inode 234190
ext3_orphan_cleanup: deleting unreferenced inode 1672359
ext3_orphan_cleanup: deleting unreferenced inode 1672358
ext3_orphan_cleanup: deleting unreferenced inode 1672357
ext3_orphan_cleanup: deleting unreferenced inode 1672356
EXT3-fs: hda1: 5 orphan inodes deleted
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
agpgart: Detected an Intel 865 Chipset.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xb000
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xb400
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xb800
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xbc00
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xf4200000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usbcore: registered new driver hiddev
usbhid: probe of 2-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random: RNG not detected
usb 2-1: USB disconnect, address 2
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xD000 irq 18
ata2: SATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD008 irq 18
ata1: dev 0 cfg 49:2f00 82:74eb 83:7fea 84:4023 85:74e8 86:3c02 87:4023 88:203f
ata1: dev 0 ATA, max UDMA/100, 160836480 sectors: lba48
ata1: dev 0 configured for UDMA/100
scsi0 : ata_piix
ata2: SATA port has no device.
scsi1 : ata_piix
  Vendor: ATA       Model: HDS722580VLSA80   Rev: V32O
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0:<6>usb 5-4: new high speed USB device using ehci_hcd and address 3
 p1 p2 p3 p4 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
usb 2-1: new low speed USB device using uhci_hcd and address 3
intel8x0_measure_ac97_clock: measured 49622 usecs
intel8x0: clocking to 48000
input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1
ts: Compaq touchscreen protocol output
Intel(R) PRO/1000 Network Driver - version 5.5.4-k2
Copyright (c) 1999-2004 Intel Corporation.
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:02:01.0 to 64
usb 3-1: new full speed USB device using uhci_hcd and address 2
usb 3-2: new full speed USB device using uhci_hcd and address 3
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection[/COLOR][COLOR=DarkOrange]
Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:03:02.0[A] -> GSI 22 (level, low) -> IRQ 22
bttv0: Bt878 (rev 17) at 0000:03:02.0, irq: 22, latency: 32, mmio: 0xf4100000
bttv0: detected: Twinhan VisionPlus DVB-T [card=113], PCI subsystem ID is 1822:0001
bttv0: using: Twinhan DST + clones [card=113,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
bttv0: using tuner=4
bttv0: add subdevice "dvb0"
ACPI: PCI interrupt 0000:03:02.1[A] -> GSI 22 (level, low) -> IRQ 22
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:03:05.0[A] -> GSI 21 (level, low) -> IRQ 21
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f4004000-f40047ff]  Max Packet=[2048][/COLOR][COLOR=Olive]
e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d6100005fd2ca]
  Vendor: OTi       Model: Flash Disk        Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 256000 512-byte hdwr sectors (131 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Device is in legacy mode, falling back to 2.x
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Device is in legacy mode, falling back to 2.x
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (4095 buckets, 32760 max) - 336 bytes per conntrack
NET: Registered protocol family 17
device eth0 entered promiscuous mode
device eth0 left promiscuous mode
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive![/COLOR][COLOR=Red]
bt878: AUDIO driver version 0.0.0 loaded
dvb_bt8xx: unable to determine DMA core of card 0,
dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
dvb-bt8xx: probe of dvb0 failed with error -14[/COLOR][/INDENT]


and this LSPCI:
[INDENT][COLOR=Olive]
 # lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interf ace (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev  02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev  02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev  02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev  02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Contro ller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Sto rage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Con troller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC' 97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 1 00 DDR/200 DDR] (rev b2)
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller  (LOM)
0000:03:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Captu re (rev 11)
0000:03:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (re v 11)
0000:03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Co ntroller (PHY/Link)[/COLOR][/INDENT]




Ok so the two problems I am facing are the conflict at the end of dmesg re: the audio module which I do not know how to resolve (I'm a newbie). And the following error when I run tzap on a channel (using channel conf file I know works from fedora).

[INDENT][COLOR=Olive]# tzap -r SBS1[/COLOR][COLOR=Red]
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: failed opening '/dev/dvb/adapter0/frontend0' (No such device)
[/COLOR][/INDENT]

I have looked into /etc/udev/scripts/dvb.sh and it looks like it has the appropriate 212 settings, I haven't touched it, so it's all default there and seems the same as what people are suggesting on the net anyway. I also tried using [this script](http://svn.wilsonet.com/projects/mythtvology/attachment/ticket/15/MAKEDEV-DVB.sh) but it also recieves the same error. I don't know which of them made these device entries, but either way they don't work despite being there:

[INDENT][COLOR=Olive]
# ls /dev/dvb/
adapter0  adapter1  adapter2  adapter3[/COLOR][/INDENT]

[INDENT][COLOR=Olive]
# ls /dev/dvb/adapter0
audio0  ca0  demux0  dvr0  frontend0  net0  osd0  video0[/COLOR][/INDENT]


So am I missing any modules?
How do I resolve the conflicting audio module?
How do I re-create the frontend0 device or re-do the devices properly?

My first post on these forums, I have used them as a resource heaps already and want to contribute back a HOWTO for this card w/ Hoary once I am finished.

cheers,

Trollzor

---

### Post by art2003 on 2005-08-14
had the same problem and fixed it.
Mind you my card is actually a Satellite card although it was detected as Terrestrial.

Still the way to avoid the audio conflict is getting dvb-bt8xx to load BEFORE snd_bt8xx by default somehow it happens the other way round.

1)
sudo gedit /etc/hotplug/blacklist
Add these lines:
snd_bt87x
bttv
dvb_bt8xx
bt878

2)
sudo gedit /etc/modules
add these lines:
bttv
dvb-bt8xx
dst
snd_bt87x

reboot, start a program like kaffeine and it should detect your Twinhan PCI satellite card properly. Mind you in my case this has resulted in what used to be my default card /dev/dsp becoming /dev/dsp1 
I am working on fixing this too, let me know if this happens to you too.

---

