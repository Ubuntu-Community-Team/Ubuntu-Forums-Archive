---
title: "Installed a &quot;Hp CD Writer plus&quot; Need Help"
date: 2011-03-03
forum: Hardware
---

### Post by eino1953 on 2011-03-03
I'm having problems with the drive reading blank disks. 
This is the error. When I try to write to the drive.
1: cannot open /dev/sr0: Read-only file system
How do I change this? :confused:

---

### Post by eino1953 on 2011-03-05
This is the output from "sudo lshw" command.  How do I remove write protection?

 *-cdrom
                description: CD-R/CD-RW writer
                product: R/RW 8x4x32
                vendor: IDE-CD
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D2,7
                serial: 3IDE-CD  R/RW 8x4x32     D2,75
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

---

### Post by eino1953 on 2011-03-05
more Information on CDROM

>  cdrdao drive-info
Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
/dev/sr0: IDE-CD R/RW 8x4x32    Rev: D2,7
Using driver: Generic SCSI-3/MMC (raw writing) - Version 2.0 (options 0x0000)

Maximum reading speed: 5648 kB/s
Current reading speed: 5648 kB/s
Maximum writing speed: 1411 kB/s
Current writing speed: 1411 kB/s
BurnProof supported: no
JustLink supported: no
JustSpeed supported: no> sudo hdparm /dev/sr0

/dev/sr0:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
steve@steve-desktop:~$ sudo hdparm /dev/sr1
/dev/sr1: No such file or directory

$ hwinfo --cdrom
18: SCSI 01.0: 10602 CD-ROM                                     
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_R_RW_8x4x32
  Unique ID: KD9E.opzDN1tCisC
  Parent ID: 3p2J.KISc1LKiP4A
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:1:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0
  Hardware Class: cdrom
  Model: "IDE-CD R/RW 8x4x32"
  Vendor: "IDE-CD"
  Device: "R/RW 8x4x32"
  Revision: "D2,7"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:1:0, /dev/cdrom
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (IDE interface)
  Drive Speed: 32


---

### Post by eino1953 on 2011-03-05
Tried to mount cdrom.

 > $ mount cdrom
mount: can't find cdrom in /etc/fstab or /etc/mtab

---

### Post by eino1953 on 2011-03-07
Should I just re install Ubuntu? 
Dose anyone know how to configure a CDROM or NOT ? ? !!!!
 
If I'm in the wrong forum, LET ME KNOW NOW !!!!

---

### Post by cchhrriiss121212 on 2011-03-07
What program are you using to write the data?
Have you checked the disks you are using are any good? On another machine for example?

---

### Post by eino1953 on 2011-03-07
I used K3b, with no results. It shows no media in drive. I used a live Puppy Linux, and I could write to the cdrom. I made another copy of Puppy with no problem.

---

### Post by eino1953 on 2011-03-07
This is what I'm working with, I'll put in the original cdrom and use this one for another project.

  description: Low Profile Desktop Computer
    product: 818311U
    vendor: IBM
    serial: KCX9MZW
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=low-profile cpus=1 keyboard_password=enabled power-on_password=disabled uuid=0872B458-8E26-3C03-A2B0-C3ED087DDE03
  *-core
       description: Motherboard
       product: IBM
       vendor: IBM
       physical id: 0
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 2AKT51AUS (07/06/2005)
          size: 110KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot edd acpi usb agp ls120boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: WMT478/NWD
          size: 2400MHz
          capacity: 3400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: J4
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: J5
        *-bank:2
             description: DIMM DDR Synchronous
             physical id: 2
             slot: J15
             size: 256MiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous [empty]
             physical id: 3
             slot: J16
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:ec000000-efffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:e8000000-e807ffff ioport:1800(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e8080000-e80803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:2000(size=4096) memory:e8100000-e81fffff
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 02
                serial: 00:09:6b:2f:e1:a7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:e8104000-e8104fff ioport:2000(size=64)
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 9
                bus info: pci@0000:03:09.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: irq:21 ioport:2040(size=64)
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 9.1
                bus info: pci@0000:03:09.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:2080(size=8)
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 9.2
                bus info: pci@0000:03:09.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:e8105000-e81057ff memory:e8100000-e8103fff
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:20000000-200003ff
           *-disk
                description: ATA Disk
                product: IC35L060AVV207-0
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: V22O
                serial: VNVB30G8TX1J9H
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cccdcccd
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ac4a7aa8-9cf7-424f-9cda-071b728377cf
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-03-29 15:12:17 filesystem=ext3 modified=2011-03-07 16:43:28 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-03-07 19:09:26 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1427MiB
                   capacity: 1427MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1427MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: R/RW 8x4x32
                vendor: IDE-CD
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D2,7
                serial: 3IDE-CD  R/RW 8x4x32     D2,75
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

It's good enough to surf the web, and listen to music.
I done with this one !!!

---

