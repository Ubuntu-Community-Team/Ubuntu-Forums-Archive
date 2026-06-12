---
title: "Nvidia GEforce 6500 - Dual monitors?"
date: 2013-02-07
forum: Hardware
---

### Post by S Hartwell on 2013-02-07
The card has a VGA and DVI port which leads me to the belief that I can use each port for a seperate monitor but, I've researched and some people on the internet say you can't(VGA is just a split off DVI?)

Here's my SysInfo(From terminal command.)

```

id:	
shawn-nv54-series
description:	Desktop Computer
product:	System Product Name
vendor:	System manufacturer
version:	System Version
serial:	System Serial Number
width:	64 bits
capabilities:	smbios-2.3 dmi-2.3 vsyscall32
configuration:	
boot	=	normal
chassis	=	desktop
uuid	=	BC6501C3-0C36-DA11-8118-4CDBA640BCE8


id:	
core
description:	Motherboard
product:	P5GL-MX
vendor:	ASUSTeK Computer INC.
physical id:	
0
version:	Rev 1.xx
serial:	MB-1234567890
id:	
firmware
description:	BIOS
vendor:	American Megatrends Inc.
physical id:	
0
version:	0605
date:	09/02/2005
size:	64KiB
capacity:	448KiB
capabilities:	isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
id:	
cpu:0
description:	CPU
product:	Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor:	Intel Corp.
physical id:	
4
bus info:	
cpu@0
version:	Intel(R) Pentium(R) 4 CPU 3.00GHz
serial:	To Be Filled By O.E.M.
slot:	LGA 775
size:	3GHz
capacity:	3GHz
width:	64 bits
clock:	200MHz
capabilities:	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
id:	
cache:0
description:	L1 cache
physical id:	
5
slot:	L1-Cache
size:	16KiB
capacity:	16KiB
capabilities:	pipeline-burst internal varies data
id:	
cache:1
description:	L2 cache
physical id:	
6
slot:	L2-Cache
size:	2MiB
capacity:	2MiB
capabilities:	pipeline-burst internal varies unified
id:	
memory
description:	System Memory
physical id:	
30
slot:	System board or motherboard
size:	1536MiB
id:	
bank:0
description:	DIMM SDRAM Synchronous
product:	PartNum0
vendor:	Manufacturer0
physical id:	
0
serial:	SerNum0
slot:	DIMM0
size:	512MiB
width:	64 bits
id:	
bank:1
description:	DIMM [empty]
product:	PartNum1
vendor:	Manufacturer1
physical id:	
1
serial:	SerNum1
slot:	DIMM1
id:	
bank:2
description:	DIMM SDRAM Synchronous
product:	PartNum2
vendor:	Manufacturer2
physical id:	
2
serial:	SerNum2
slot:	DIMM2
size:	1GiB
width:	64 bits
id:	
bank:3
description:	DIMM [empty]
product:	PartNum3
vendor:	Manufacturer3
physical id:	
3
serial:	SerNum3
slot:	DIMM3
id:	
cpu:1
product:	Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor:	Intel Corp.
physical id:	
1
bus info:	
cpu@1
size:	3GHz
capacity:	3GHz
width:	64 bits
capabilities:	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
id:	
pci
description:	Host bridge
product:	82915G/P/GV/GL/PL/910GL Memory Controller Hub
vendor:	Intel Corporation
physical id:	
100
bus info:	
pci@0000:00:00.0
version:	0e
width:	32 bits
clock:	33MHz
id:	
multimedia
description:	Audio device
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
vendor:	Intel Corporation
physical id:	
1b
bus info:	
pci@0000:00:1b.0
version:	05
width:	64 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	snd_hda_intel
latency	=	0
resources:	
irq	:	41
memory	:	dddf8000-dddfbfff
id:	
pci:0
description:	PCI bridge
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
vendor:	Intel Corporation
physical id:	
1c
bus info:	
pci@0000:00:1c.0
version:	05
width:	32 bits
clock:	33MHz
capabilities:	pci pciexpress msi pm normal_decode bus_master cap_list
configuration:	
driver	=	pcieport
resources:	
irq	:	40
ioport	:	e000(size=4096)
memory	:	ddf00000-dfffffff
ioport	:	c0000000(size=486539264)
id:	
display
description:	VGA compatible controller
product:	NV44 [GeForce 6200 TurboCache(TM)]
vendor:	NVIDIA Corporation
physical id:	
0
bus info:	
pci@0000:02:00.0
version:	a1
width:	64 bits
clock:	33MHz
capabilities:	pm msi pciexpress vga_controller bus_master cap_list rom
configuration:	
driver	=	nvidia
latency	=	0
resources:	
irq	:	16
memory	:	df000000-dfffffff
memory	:	c0000000-cfffffff
memory	:	de000000-deffffff
memory	:	ddfe0000-ddffffff
id:	
usb:0
description:	USB controller
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
vendor:	Intel Corporation
physical id:	
1d
bus info:	
pci@0000:00:1d.0
version:	05
width:	32 bits
clock:	33MHz
capabilities:	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	23
ioport	:	b880(size=32)
id:	
usb:1
description:	USB controller
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
vendor:	Intel Corporation
physical id:	
1d.1
bus info:	
pci@0000:00:1d.1
version:	05
width:	32 bits
clock:	33MHz
capabilities:	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	19
ioport	:	bc00(size=32)
id:	
usb:2
description:	USB controller
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
vendor:	Intel Corporation
physical id:	
1d.2
bus info:	
pci@0000:00:1d.2
version:	05
width:	32 bits
clock:	33MHz
capabilities:	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	18
ioport	:	c000(size=32)
id:	
usb:3
description:	USB controller
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
vendor:	Intel Corporation
physical id:	
1d.3
bus info:	
pci@0000:00:1d.3
version:	05
width:	32 bits
clock:	33MHz
capabilities:	uhci bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
resources:	
irq	:	16
ioport	:	c080(size=32)
id:	
usb:4
description:	USB controller
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
vendor:	Intel Corporation
physical id:	
1d.7
bus info:	
pci@0000:00:1d.7
version:	05
width:	32 bits
clock:	33MHz
capabilities:	pm debug ehci bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
resources:	
irq	:	23
memory	:	dddffc00-dddfffff
id:	
pci:1
description:	PCI bridge
product:	82801 PCI Bridge
vendor:	Intel Corporation
physical id:	
1e
bus info:	
pci@0000:00:1e.0
version:	d5
width:	32 bits
clock:	33MHz
capabilities:	pci subtractive_decode bus_master cap_list
resources:	
ioport	:	d000(size=4096)
memory	:	dde00000-ddefffff
id:	
network
description:	Ethernet interface
product:	RTL-8139/8139C/8139C+
vendor:	Realtek Semiconductor Co., Ltd.
physical id:	
2
bus info:	
pci@0000:01:02.0
logical name:	
eth1
version:	10
serial:	00:13:d4:b2:89:17
size:	10Mbit/s
capacity:	100Mbit/s
width:	32 bits
clock:	33MHz
capabilities:	pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	8139too
driverversion	=	0.9.28
duplex	=	half
latency	=	64
link	=	no
maxlatency	=	64
mingnt	=	32
multicast	=	yes
port	=	MII
speed	=	10Mbit/s
resources:	
irq	:	17
ioport	:	d800(size=256)
memory	:	ddeffc00-ddeffcff
id:	
multimedia
description:	Multimedia audio controller
product:	CA0106 Soundblaster
vendor:	Creative Labs
physical id:	
3
bus info:	
pci@0000:01:03.0
version:	00
width:	32 bits
clock:	33MHz
capabilities:	pm bus_master cap_list
configuration:	
driver	=	snd_ca0106
latency	=	64
maxlatency	=	20
mingnt	=	2
resources:	
irq	:	20
ioport	:	dc00(size=32)
id:	
isa
description:	ISA bridge
product:	82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
vendor:	Intel Corporation
physical id:	
1f
bus info:	
pci@0000:00:1f.0
version:	05
width:	32 bits
clock:	33MHz
capabilities:	isa bus_master
configuration:	
latency	=	0
id:	
ide:0
description:	IDE interface
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
vendor:	Intel Corporation
physical id:	
1f.1
bus info:	
pci@0000:00:1f.1
version:	05
width:	32 bits
clock:	33MHz
capabilities:	ide bus_master
configuration:	
driver	=	ata_piix
latency	=	0
resources:	
irq	:	18
ioport	:	1f0(size=8)
ioport	:	3f6
ioport	:	170(size=8)
ioport	:	376
ioport	:	ffa0(size=16)
id:	
ide:1
description:	IDE interface
product:	82801FB/FW (ICH6/ICH6W) SATA Controller
vendor:	Intel Corporation
physical id:	
1f.2
bus info:	
pci@0000:00:1f.2
version:	05
width:	32 bits
clock:	66MHz
capabilities:	ide pm bus_master cap_list
configuration:	
driver	=	ata_piix
latency	=	0
resources:	
irq	:	19
ioport	:	cc00(size=8)
ioport	:	c880(size=4)
ioport	:	c800(size=8)
ioport	:	c480(size=4)
ioport	:	c400(size=16)
id:	
serial
description:	SMBus
product:	82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
vendor:	Intel Corporation
physical id:	
1f.3
bus info:	
pci@0000:00:1f.3
version:	05
width:	32 bits
clock:	33MHz
configuration:	
latency	=	0
resources:	
ioport	:	400(size=32)
id:	
scsi:0
physical id:	
2
logical name:	
scsi0
capabilities:	emulated
id:	
disk
description:	ATA Disk
product:	ST320014A
vendor:	Seagate
physical id:	
0.0.0
bus info:	
scsi@0:0.0.0
logical name:	
/dev/sda
version:	3.07
serial:	5JZGERVQ
size:	18GiB (20GB)
capabilities:	partitioned partitioned:dos
configuration:	
ansiversion	=	5
sectorsize	=	512
signature	=	000893da
id:	
volume:0
description:	EXT4 volume
vendor:	Linux
physical id:	
1
bus info:	
scsi@0:0.0.0,1
logical name:	
/dev/sda1
version:	1.0
serial:	7be0ec4d-db47-4018-9603-2ac3152bd919
size:	17GiB
capacity:	17GiB
capabilities:	primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration:	
created	=	2013-02-03 14:41:31
filesystem	=	ext4
lastmountpoint	=	/
modified	=	2013-02-05 19:39:01
mounted	=	2013-02-05 19:39:01
state	=	clean
id:	
volume:1
description:	Extended partition
physical id:	
2
bus info:	
scsi@0:0.0.0,2
logical name:	
/dev/sda2
size:	1533MiB
capacity:	1533MiB
capabilities:	primary extended partitioned partitioned:extended
id:	
logicalvolume
description:	Linux swap / Solaris partition
physical id:	
5
logical name:	
/dev/sda5
capacity:	1533MiB
capabilities:	nofs
id:	
cdrom
description:	DVD-RAM writer
product:	DVDRAM GSA-4167B
vendor:	HL-DT-ST
physical id:	
0.1.0
bus info:	
scsi@0:0.1.0
logical name:	
/dev/cdrom
logical name:	
/dev/cdrw
logical name:	
/dev/dvd
logical name:	
/dev/dvdrw
logical name:	
/dev/sr0
version:	DL10
capabilities:	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
scsi:1
physical id:	
3
logical name:	
scsi2
capabilities:	emulated
id:	
disk
description:	ATA Disk
product:	Maxtor 6L160M0
vendor:	Maxtor
physical id:	
0.0.0
bus info:	
scsi@2:0.0.0
logical name:	
/dev/sdb
version:	BANC
serial:	L39A9RZG
size:	152GiB (163GB)
capabilities:	partitioned partitioned:dos
configuration:	
ansiversion	=	5
sectorsize	=	512
signature	=	00057a24
id:	
volume:0
description:	EXT4 volume
vendor:	Linux
physical id:	
1
bus info:	
scsi@2:0.0.0,1
logical name:	
/dev/sdb1
logical name:	
/
version:	1.0
serial:	9886af24-8838-4dad-8ef5-9e09b9f1c344
size:	151GiB
capacity:	151GiB
capabilities:	primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration:	
created	=	2013-02-03 20:04:22
filesystem	=	ext4
lastmountpoint	=	/
modified	=	2013-02-07 08:18:08
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,data=ordered
mounted	=	2013-02-07 08:18:08
state	=	mounted
id:	
volume:1
description:	Extended partition
physical id:	
2
bus info:	
scsi@2:0.0.0,2
logical name:	
/dev/sdb2
size:	1534MiB
capacity:	1534MiB
capabilities:	primary extended partitioned partitioned:extended
id:	
logicalvolume
description:	Linux swap / Solaris partition
physical id:	
5
logical name:	
/dev/sdb5
capacity:	1534MiB
capabilities:	nofs
id:	
scsi:2
physical id:	
5
bus info:	
usb@1:2
logical name:	
scsi4
capabilities:	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description:	SCSI Disk
product:	Expansion
vendor:	Seagate
physical id:	
0.0.0
bus info:	
scsi@4:0.0.0
logical name:	
/dev/sdc
version:	0219
serial:	NA41NRTY
size:	698GiB (750GB)
capabilities:	partitioned partitioned:dos
configuration:	
ansiversion	=	6
sectorsize	=	512
signature	=	00031447
id:	
volume
description:	Windows FAT volume
vendor:	mkdosfs
physical id:	
1
bus info:	
scsi@4:0.0.0,1
logical name:	
/dev/sdc1
logical name:	
/media/s-hartwell/7289-7B11
version:	FAT32
serial:	7289-7b11
size:	698GiB
capacity:	698GiB
capabilities:	primary fat initialized
configuration:	
FATs	=	2
filesystem	=	fat
mount.fstype	=	vfat
mount.options	=	rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
state	=	mounted
id:	
scsi:3
physical id:	
6
bus info:	
usb@1:3
logical name:	
scsi5
capabilities:	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description:	SCSI Disk
product:	JumpDrive
vendor:	Lexar
physical id:	
0.0.0
bus info:	
scsi@5:0.0.0
logical name:	
/dev/sdd
version:	1.00
serial:	4128696102
size:	14GiB (16GB)
capabilities:	removable
configuration:	
ansiversion	=	6
sectorsize	=	512
id:	
medium
physical id:	
0
logical name:	
/dev/sdd
size:	14GiB (16GB)
capabilities:	partitioned partitioned:dos
configuration:	
signature	=	0008882f
id:	
volume
description:	Windows FAT volume
vendor:	SYSLINUX
physical id:	
1
logical name:	
/dev/sdd1
logical name:	
/media/s-hartwell/KIMS STUFF
version:	FAT32
serial:	11df-232f
size:	14GiB
capacity:	14GiB
capabilities:	primary bootable fat initialized
configuration:	
FATs	=	2
filesystem	=	fat
mount.fstype	=	vfat
mount.options	=	rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
state	=	mounted
id:	
network
description:	Wireless interface
physical id:	
1
logical name:	
ra0
serial:	c8:d7:19:1e:49:99
capabilities:	ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	RALINK WLAN
ip	=	192.168.2.19
multicast	=	yes
wireless	=	Ralink STA
```

If this card isn't any good does anyone have suggestions? I'd put money into this old Desktop before considering building a new one.

Also, if anyone could recommend some Newegg.ca (I'm from Canada) Memory replacements. I've got 1.5G in there now but after some research this motherboard can hold 4GB. I'd like to put in 4GB in the near-future. Please suggest some sticks along with a new Graphics card that'll work better with this motherboard. Pretty much suggest any parts I could upgrade that'll boost performance.

---

