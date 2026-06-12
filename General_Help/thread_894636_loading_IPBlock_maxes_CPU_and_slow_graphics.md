---
title: "loading IPBlock maxes CPU and slow graphics"
date: 2008-08-19
forum: General Help
---

### Post by rbjscv on 2008-08-19
Firstly I'm still rather new to linux but I love it.  Now on loading the IPBlock program my CPU usage goes to 99% and the fan howls like a banshee.  When loaded it calms down.  This doesn't happen when updating.

Second concern:  In compiz I can do the cube rotation really quick. But when I added the raised windows to it, the rotation slowed down to mud.  
My video card is Nvidia e-GeForce 8400GS, 245 MB.  I'm using the drivers that Envy supplied.  Just to get the card working was a major feat to me and to enable the cool stuff was even more trying.  BUT I read and read, and suddenly I had cube and rotation.

Below is the print-out of my specs as Ubuntu sees them.  Is there something not fast enough that is causing these problems?  Oh, Yeah, Linux is on the 160GB drive and WinXP has been relegated 80 GB.  Dual boot for now.

What am I missing, or is this the best life is going to get?  

ALSO, show I be running 64bit on this?  Right now it has 32. Everything is fine, but if I figure if I can make a mess of things and then have too clean it up, why not?


```

emachine                   
    description: Desktop Computer
    product: W3503
    serial: CRC65 100 27114
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=6AB50F88-C86C-11DA-B2B4-00112FEB4149
  *-core
       description: Motherboard
       product: D101GGC
       vendor: Intel Corporation
       physical id: 0
       version: AAD54032-300
       serial: BTGC614002YX
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) D CPU 3.33GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 3333MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: asynchronous internal write-back unified
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: GC11010M.15A.0009.2006.0420.1045 (04/20/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x0000000000000000
             physical id: 0
             serial: 0x00000000
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: 0x4A4959473138545642203147422020202020
             vendor: 0x7F7F7F1900000000
             physical id: 1
             serial: 0x00000000
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8400 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD800AB-00CBA1
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 04.07B04
                   serial: WD-WCAA52207153
                   size: 74GiB (80GB)
                   capacity: 74GiB (80GB)
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 signature=d355ce69 smart=on
                 *-volume
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: 3.1
                      serial: 3a92fc59-c9ad-f745-bee5-375e84b575cf
                      size: 74GiB
                      capacity: 74GiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2008-07-03 18:47:31 filesystem=ntfs state=clean
              *-disk:1
                   description: ATA Disk
                   product: WDC WD1600BB-22GUC0
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 08.02D08
                   serial: WD-WCAL98416988
                   size: 149GiB (160GB)
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 signature=03080307 smart=on
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: 34504801-1330-4523-b53f-ccf773780e9d
                      size: 143GiB
                      capacity: 143GiB
                      capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-08-01 18:04:50 filesystem=ext3 modified=2008-08-18 12:55:42 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-18 12:55:42 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      size: 5883MiB
                      capacity: 5883MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hdb5
                         capacity: 5883MiB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: ATAPI DVD A DH-3H20A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: YX13
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma4 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:16:76:54:15:d4
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sda
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdb
             version: 1.01
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdc
             version: 1.02
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdd
             version: 1.03
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd 
```

---

