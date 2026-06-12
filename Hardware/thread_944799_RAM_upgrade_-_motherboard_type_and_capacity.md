---
title: "RAM upgrade - motherboard type and capacity"
date: 2008-10-11
forum: Hardware
---

### Post by eekfonky on 2008-10-11
Hello

I really want to upgrade my RAM from 512MB to as much as possible. I have 2 RAM slots, but I do not know the Speed, name, type or capacity of the motherboard.

Please help

---

### Post by phidia on 2008-10-11
There are websites out there that will test your system and tell you what type of ram you need. [URL="http://www.4allmemory.com/"]
This[/URL] is one site like that but there are several others. 

Note: The auto checker requires windows unfortunately but there are other methods at that site for determining your ram type.

You can also open a terminal and enter > sudo lshw that may give you the info you want too, or enough info to use the other methods the memory seller has.

---

### Post by eekfonky on 2008-10-11
```
description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop uuid=1CE60F23-260C-1101-860F-00A0C968133D
  *-core
       description: Motherboard
       product: SiS-650
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (05/17/2002)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.1.3
          slot: Socket 478
          size: 1700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk:0
                description: ATA Disk
                product: ExcelStor Techno
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: VA2O
                serial: VNP210J2A6WL3A
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=81a081a0
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: c9aa83d8-5222-4839-9875-b581a32c0955
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-03 02:58:59 filesystem=ext3 modified=2008-10-10 10:26:14 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-10-10 10:26:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1466MiB
                   capacity: 1466MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: HDS728080PLAT20
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: PF2O
                serial: PFD219SYTD8ZGF
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fa925d02
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/Chris
                   version: 3.1
                   serial: 7087-7215
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-10-11 16:34:09 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
           *-cdrom:0
                description: DVD writer
                product: DVD RW AD-5170A
                vendor: Optiarc
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                serial: [Optiarc DVD RW AD-5170A 1.11 Jul19,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GD-2500
                vendor: HITACHI
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0011
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-multimedia:0
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-multimedia:1
             description: Multimedia controller
             product: SAA7130 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15 module=saa7134
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:04:61:42:68:78
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: MuVo T200
             vendor: CREATIVE
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             serial: 441C111381602107
             size: 3863MiB (4050MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 3863MiB (4050MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=37e0c6e0
              *-volume
                   description: Windows FAT volume
                   vendor: NXP
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/MUVO T200
                   version: FAT32
                   serial: 1234-5678
                   size: 3862MiB
                   capacity: 3862MiB
                   capabilities: primary fat initialized
                   configuration: FATs=1 filesystem=fat label=MUVO T200 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
```
Any suggestions or is there a website that doesn't require windows that can help?

---

### Post by phidia on 2008-10-13
> -memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3

That is your memory unfortunatey it doesn't give the number of pins.

If you know the make and model of your computer you can plug those parameters into the form at the site I linked previously.

---

### Post by eekfonky on 2008-10-13
short of opening up and trying to find out I don't know what make it is, sorry

---

