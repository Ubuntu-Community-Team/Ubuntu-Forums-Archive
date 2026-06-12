---
title: "Problem with enabling DMA on an SIS chipset based Asus KS8 - Mx motherboard."
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by neville_lobo on 2005-02-20
Hi,

I have been having trouble trying to enable DMA on my system. I have looked all over this board for a solution but have come up blank so far. I will mention what I have tried below.

-----------------
My hardware specs are as follows:

AMD Athlon-64 2800+
Asus K8S-MX Motherboard (Integrated Video, Audio, LAN, SATA)
512MB Kingston RAM
HDD - Seagate 80 GB IDE drive (ST380011A)
CD-Rom/Writer - LG52X (HL-DT-ST GCE-8526B)
-----------------
hdparam gives the following

 sudo hdparm -tT /dev/hda

/dev/hda:
 Timing buffer-cache reads:   2248 MB in  2.00 seconds = 1123.61 MB/sec
 Timing buffered disk reads:   14 MB in  3.07 seconds =   4.56 MB/sec



 sudo hdparm -i /dev/hda

/dev/hda:

 Model=ST380011A, FwRev=8.01, SerialNo=4JV13N53
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:

 * signifies the current active mode



sudo hdparm -X66 -u1 -m16 -c3 -d1 /dev/hda

/dev/hda:
 setting 32-bit IO_support flag to 3
 setting multcount to 16
 setting unmaskirq to 1 (on)
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 setting xfermode to 66 (UltraDMA mode2)
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
------------------------------------

dmesg shows the following:



Linux version 2.6.10-3-k7 (root@omega2) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Feb 17 21:57:45 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001e000000 (usable)
 BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
480MB LOWMEM available.
found SMP MP-table at 000ff780
On node 0 totalpages: 122880
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 118784 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: Unable to locate RSDP
Intel MultiProcessor Specification v1.4
    Virtual Wire compatibility mode.
OEM ID: ASUSTek  Product ID:  APIC at: 0xFEE00000
Processor #0 15:4 APIC version 16
I/O APIC #1 Version 20 at 0xFEC00000.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Processors: 1
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1804.747 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 479224k/491520k available (1660k kernel code, 11652k reserved, 720k data, 172k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3571.71 BogoMIPS (lpj=1785856)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000010 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: AMD Athlon(tm) 64 Processor 2800+ stepping 08
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=0
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4568k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050125
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f8ab0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x987a, dseg 0xf0000
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: Missing SMALL_TAG_ENDDEP tag
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Discovered primary peer bus ff [IRQ]
PCI: Using IRQ router default [1039/0965] at 0000:00:02.0
PCI->APIC IRQ transform: (B0,I2,P2) -> 18
PCI->APIC IRQ transform: (B0,I3,P0) -> 20
PCI->APIC IRQ transform: (B0,I3,P1) -> 21
PCI->APIC IRQ transform: (B0,I3,P2) -> 22
PCI->APIC IRQ transform: (B0,I3,P3) -> 23
PCI->APIC IRQ transform: (B0,I10,P0) -> 17
pnp: 00:0c: ioport range 0x800-0x87f has been reserved
pnp: 00:0c: ioport range 0x880-0x8cf has been reserved
pnp: 00:0c: ioport range 0x8d0-0x8ff has been reserved
pnp: 00:0c: ioport range 0x480-0x48f has been reserved
pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0c: ioport range 0xcf8-0xcff could not be reserved
audit: initializing netlink socket (disabled)
audit(1108823701.478:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
inotify device minor=63
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4568KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 172k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 1
SIS5513: not 100% native mode: will probe irqs later
Probing IDE interface ide0...
hda: ST380011A, ATA DISK drive
Probing IDE interface ide1...
hdc: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 1024KiB
hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
mice: PS/2 mouse device common for all mice
hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email="dm-devel@redhat.com"]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-3-k7
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 760 chipset
agpgart: Maximum main memory to use for agp memory: 410M
agpgart: AGP aperture is 4M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
intel8x0_measure_ac97_clock: measured 49213 usecs
intel8x0: clocking to 48000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:03.0: irq 20, pci mem 0xfebf4000
ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:03.1: irq 21, pci mem 0xfebf5000
ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
ohci_hcd 0000:00:03.2: irq 22, pci mem 0xfebf6000
ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
usb 1-1: new low speed USB device using ohci_hcd and address 2
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:03.0-1usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
ehci_hcd 0000:00:03.3: irq 23, pci mem 0xfebf7000
ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
PCI: cache line size of 64 is not supported by device 0000:00:03.3
ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 8 ports detected
ts: Compaq touchscreen protocol output
usb 1-1: USB disconnect, address 2
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
eth0: RealTek RTL8139 at 0xe400, 00:08:a1:6c:e6:6c, IRQ 17
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
usb 1-1: new low speed USB device using ohci_hcd and address 3
input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:03.0-1CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
NET: Registered protocol family 24
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0325d40(lo)
IPv6 over IPv4 tunneling driver
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present


-----------------------
I think my IDE driver is the SIS5513. I have added that to the modules but it did'nt help. I upgraded to a backported 2.6.10 kernel but that did'nt help. I mucked about with hdparm.conf but to no avail. I have done everything else mentioned on this forum except recompile the kernel as I dont know how to. Please could someone help me out. If I have to recomplie, please point to an easy guide. Thanks,

Neville

PS: Never buy SIS. My graphics chip will never have 3d Acceleration on linux according to [http://www.winischhofer.net/linuxsisvga.shtml]("http://www.winischhofer.net/linuxsisvga.shtml") and the onboard lan does not work either. That is not as important as the DMA though.

---

### Post by cuoog on 2005-02-20
I have an ECS board with the same SiS755 chipset that I believe you have.  After asking questions here, and also on a couple of other forums, I've been told the only way to do this is to custom compile the kernel and force the generic idedma driver to be loaded.  I will admit however that most people thought SiS755 dma would be enabled in 2.6.10, so the fact that it hasn't worked for you is discouraging.  I've been too busy lately to recompile the kernel.  I only hope that I don't have to end up getting a new mobo to get DMA enabled, that would really suck.  Please keep us informed if you do get it to work, as I think there are a growing number of people saddled with this chipset that are having a similar problem.

Best of luck,

dan

p.s. My network did work, as did my sound (out of the box using kernel 2.6.9), so i dont know if your ethernet problems are a function of the SiS chipset but the specific device on the mobo, might need to hunt down a driver.

---

### Post by cuoog on 2005-02-20
Ok, try this.  It might work for you.  Edit your /etc/modules file and put sis5513 in before idecd and satasis and all the other ide modules.  That could work.

Dan

---

### Post by neville_lobo on 2005-02-21
[QUOTE=cuoog]Ok, try this. It might work for you. Edit your /etc/modules file and put sis5513 in before idecd and satasis and all the other ide modules. That could work.
  
  Dan[/QUOTE]
  
  Hi Dan,
     I already did that but with no result. :(
 I'll keep trying different things and see what works out. My system is quite usable at the moment but I know it can perform better and thats whats bugging me. I might pop in another harddisk and try another distro but I really love ubuntu and dont want to change. 
  
  Neville

---

### Post by neville_lobo on 2005-02-21
Part of dmesg:
  ----------------
  Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
   ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
   SIS5513: IDE controller at PCI slot 0000:00:02.5
   SIS5513: chipset revision 1
   SIS5513: not 100% native mode: will probe irqs later
   Probing IDE interface ide0...
   hda: ST380011A, ATA DISK drive
   Probing IDE interface ide1...
   hdc: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
  -----------------
  Could this line be the problem
  ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
  
  If so, what do I do?
  
  Neville

---

### Post by cuoog on 2005-02-21
yeah, i dont know about messing with that bus speed.  Since the IDE controller is running on the PCI bus, it should be operating at 33 mhz like all other PCI devices, I think.  I really think the problem here is the sis5513 driver.  That thing is old as all hell.  There are even some comments that I saw on some of the kernel dev message lists from like 2 years ago (when i googled for sis5513 linux kernel) about how its flakey on a lot of boards and there are a lot of hacks for certain boards, and your board is really, really new.  I don't have time to hunt around right now, but is it possible another driver could work?

for ideas, you could try a livecd of another distro and see if it gets it right, then use whatever it does as a hint.  

p.s. how do you like your mobo otherwise?  did you find a way to fix the nic? I just built my box 6 or 7 weeks ago and I got some deals so I didnt wait for pci-express, but might be something i could just drop in and reuse the processor.  if you dont mind my asking, where did you get it?

---

### Post by neville_lobo on 2005-02-21
I tried the Ubuntu  Live CD for AMD 64 but it did'nt work out. I'll get the latest of Knoppix and give it a try.
   
 With regards to the board, it performed very well under windows. XP was very smooth and quick. The graphics chip seems to be pretty good too for an integrated solution. Sound and LAN worked well and without any issues as expected. The performance under ubuntu is very usable (Still no NIC or 3D accel) but I know it can get a LOT better. 
   
   Regarding the board........
 I live in Mumbai (India). There is a place called Lamington Road which is the electronics market of Mumbai. There are probably more than a 100 dealers on that street an the by lanes. I picked up the board for about Rs 5000/- (about 110$). Its a bit expensive out here because the import duty is still a bit high and this was a new product. I paid about Rs 12000 for the Processor & motherboard (About 265$) in January but the price has already fallen to Rs 9800 for the combo (115$ approx). It was the only AMD64 integrated solution available. My only option was a VIA or N-force3 based board with a Nvidia TI400 based graphics card . But that would have driven up the cost. But atleast ubuntu would have worked well. :). 
   
 Lets hope I can find a solution. Do you think Slackware would work out? I just got 10.1. I'll check out their forums tomorrow and see if slackers are facing issues with this chipset.
  
  Neville

---

