---
title: "eSata PCMCIA Card, Please Help"
date: 2009-03-23
forum: Hardware
---

### Post by bikerman2299 on 2009-03-23
Hi, I have an old school Dell XPS. 2005 model year. I just recently purchased a Vantec Sata II- 150 2 Port Cardbus. Right now I cannot figure out how to get Ubuntu to recognize it. I am running Ubuntu 8.04.1 Hardy. I am really new to Ubuntu, and still learning all the terminal commands. Any help would be greatly appreciated! Thanks!

---

### Post by teaker1s on 2009-03-25
Okay not my area of expertise, but if we assume that the PCMCIA port works place card into computer then boot
(port may not hotplug if the card is inserted after booting)

 we could try, 
list hardware with this command

```
sudo lshw
```

list pci

```
sudo lspci -v
```

list usb

```
lsusb
```

lastly the makers website states at least some of their products work with 

Linux kernel version of 2.4.18-14 or later 
check your kernel

```
uname -r
```



Dump the output into your next post and I will try to see if we can see the card

---

### Post by bikerman2299 on 2009-03-26
sudo lshw
wax-laptop                
    description: Portable Computer
    product: Inspiron XPS
    vendor: Dell Inc.
    serial: C5HF961
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-3500-1048-8046-C3C04F393631
  *-core
       description: Motherboard
       product: 0X1193
       vendor: Dell Inc.
       physical id: 0
       serial: .C5HF961.CN129614BE2430.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (11/01/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Microprocessor
          size: 3400MHz
          capacity: 3400MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: M18 JN [Radeon Mobility 9800]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master vga_palette cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5705M Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:11:43:5d:c9:f4
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.100 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
           *-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4510 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=32 module=ssb
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: FUJITSU MHU2100A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: NQ06T4B26B6S
                size: 93GiB (100GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=41ab2316
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7
                   size: 90GiB
                   capacity: 90GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-28 23:48:45 filesystem=ext3 modified=2009-03-26 05:23:45 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-03-26 05:21:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2957MiB
                   capacity: 2957MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2957MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6500A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 202C
                serial: [_NEC    DVD+-RW ND-6500A202C04081200
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
     *-storage
          description: Mass storage controller
          product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
          vendor: Silicon Image, Inc.
          physical id: 1
          bus info: pci@0000:03:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm bus_master cap_list
          configuration: driver=sata_sil latency=64 module=sata_sil
     *-scsi
          physical id: 2
          bus info: usb@5:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: My Book
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1010
             serial: WU2Q10051462
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:mac
             configuration: ansiversion=4
           *-volume:0
                description: Apple partition map
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                capacity: 31KiB
           *-volume:1
                description: Apple Free
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                capacity: 128MiB
           *-volume:2
                description: Apple HFS
                vendor: Mac OS
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sdb3
                version: 4
                serial: 997aff92-cf70-0bd8-0000-000003a38000
                size: 1862GiB
                capacity: 1862GiB
                capabilities: journaled hfsplus initialized
                configuration: checked=2008-08-06 09:13:58 created=2008-08-05 23:13:58 filesystem=hfsplus lastmountedby=8.10 modified=2008-10-16 11:15:50 state=unclean
           *-volume:3
                description: Apple Free
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sdb4
                capacity: 8KiB
        *-enclosure UNCLAIMED
             description: SCSI Enclosure
             product: My Book Device
             vendor: WD
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             version: 1010
             serial: WU2Q10051462
             configuration: ansiversion=4
  *-battery
       product: DELL R11854A
       vendor: Sony
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 95460mWh
       configuration: voltage=14.8V
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:0f:79:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Unknown device 017c
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [e4] Vendor Specific Information
	Capabilities: [a0] AGP version 3.0

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: e0000000-efffffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at f8fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-fbffffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc40 [size=64]
	Memory at f8fff800 (32-bit, non-prefetchable) [size=512]
	Memory at f8fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Conexant Unknown device 5422
	Flags: medium devsel, IRQ 17
	I/O ports at d400 [size=256]
	I/O ports at d080 [size=128]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: ATI Technologies Inc M18 JN [Radeon Mobility 9800] (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 5106
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 255, IRQ 18
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 3.0
	Capabilities: [50] Power Management version 2

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
	Subsystem: Dell Latitude D400
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at faff0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at fa000000 [disabled] [size=64K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-

02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fa010000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 54000000-57fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 0000e000-0000e0ff
	I/O window 1: 0000e400-0000e4ff
	16-bit legacy interface ports at 0001

02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 017c
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fafef800 (32-bit, non-prefetchable) [size=2K]
	Memory at fafe8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
	Flags: bus master, fast devsel, latency 32, IRQ 17
	Memory at fafec000 (32-bit, non-prefetchable) [size=8K]

03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
	Subsystem: Silicon Image, Inc. SiI 3512 SATALink Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at e010 [size=8]
	I/O ports at e020 [size=4]
	I/O ports at e018 [size=8]
	I/O ports at e024 [size=4]
	I/O ports at e000 [size=16]
	Memory at 58000000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 54000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2

lsusb
Bus 005 Device 002: ID 1058:1105 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

 lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M18 JN [Radeon Mobility 9800]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)


Alright that is everything I have. I went looking through it myself, and I don't see it. Thanks for the help!!

---

### Post by teaker1s on 2009-03-26
[COLOR="Red"]03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
[/COLOR] is the chip in your card

it appears supported as found on many forums with linux the post below says about bios configuration issue causing card to be detected,but not in use

[http://forums.opensuse.org/hardware/laptop/404259-silicon-image-3512-works-live-cd-but-not-installed-system.html#post1926274]("http://forums.opensuse.org/hardware/laptop/404259-silicon-image-3512-works-live-cd-but-not-installed-system.html#post1926274")

check tis first and if it's not a bios configuration issue, we can have another stab at it

---

### Post by bikerman2299 on 2009-03-26
Tried, but no avail. Now I am just trying to get my laptop to recognize my external. Its a WD 2TB preformated HFS+. I can pug it in and I can see it under fdisk -l but I cannot mount it, cannot force mount it, or anything. I even gedit /etc/fstab see's it. check it out....
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 /dev/sda5  hfsplus
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

this is fdisk -l 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5<------    11785       12161     3028221   82  Linux swap / Solaris

this is what i get if i normally try to mount it. 

root@wax-laptop:/# mount /dev/sda5
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

this is dmesg | tail

 dmesg | tail
[ 5162.155854] input: failed to attach handler evdev to device input59, error: -23
[ 5162.161938] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 5162.161949] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 5186.539726] hfs: unable to parse mount options.
[ 5219.797518] hfs: unable to find HFS+ superblock
[ 5283.801319] input: b43-phy0 as /devices/virtual/input/input60
[ 5283.844365] evdev: no more free evdev devices
[ 5283.844378] input: failed to attach handler evdev to device input60, error: -23
[ 5283.850479] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 5283.850490] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

Yeah I was thinking about mounting it on a windows machine and reformating it there to just a regular FAT, or NTSF format then trying again to get it to mount in this comp. I am sorry if I am eatting up your time. Thanks for the help

---

### Post by teaker1s on 2009-03-26
Okay, a really dumb question, forgive me for this -have you tried disk mounter applet which uses pmount? it also appears you have not specified read write options

for example.
fstab entry:
> /dev/sda5 /mnt/ntfs-sys ntfs ro,dmask=0222,fmask=0333 0 0


Also If you can see the drive via esata than it would appear you have a mounting issue,rather than a hardware driver issue with sata pcmcia card.

I will admit,I'm not the best at mount options-if you have no joy with my suggestions I will try to find a good howto for successfully mounting windows drive.

It also appears to me you may need a uid for esata as the drive location may change and fstab will need to recognize it on different ports

---

### Post by bikerman2299 on 2009-03-26
root@wax-laptop:/# /dev/sda5 /mnt/ntfs-sys ntfs ro,dmask=0222,fmask=0333 0 0 
bash: /dev/sda5: Permission denied


note: I am in root. I gave up on the eSata card. I even contacted the company and the sent my call down to a programmer and he had no joy. I am just going to return it. I will repost this under a correct heading. I am just try to access the external HDD so I can reformat it into ext3 filesystem. Thank you for your help though. I really appreciate it!

---

### Post by teaker1s on 2009-03-26
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by bikerman2299 on 2009-03-26
> **teaker1s said:**
> [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

tried already, i went through that post many a times. Thanks though! I really appreciate the help.

---

### Post by teaker1s on 2009-03-26
Okay one final idea, it seems that your drive refuses to mount, you could try "Knoppix live" it has the ability to mount damaged/dirty file systems.

---

