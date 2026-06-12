---
title: "[SOLVED] screen freezes out after installing new DH 2600 graphic card on ubuntu 8.04"
date: 2008-11-10
forum: Hardware
---

### Post by Ant68 on 2008-11-10
Hello all,

I have an issue with the set up of a graphic card "ATI Radeon™ HD 2600" - ([_see specs_]("http://www.sapphiretech.com/us/products/products_overview.php?gpid=180&grp=3")) on my desktop (see specs below in this post). I run ubuntu 8.04. I can no longer log in the system.

Step by step description of the issue:
1 - I have installed the HD 2600 graphic card in the desktop and then started ubuntu (8.04). Ubuntu was working fine before I put in the Graphic card. 
2 - The system worked well and I managed to log in without any issues. 
3 - I have then been in the administration area to get the driver set up for the new graphic card and I saw a driver ready to be installed for the graphic card. 
4 - I did run the driver install successfully. 
5 - I then rebooted my desktop (as it was suggested). The system shut down nicely. it then re-started and the system popped up the normal login page. 
6 - I keying in my username and password and submitted it. **The screen take a few seconds and then freezes.** 
7 - I tried several times with the same result... :(.
8 - I have then remove the graphic card and rebooted again. I could log in but the system was running a low graphic resolution.


I still would like to get the graphic card running:
- Could you please tell me if the HD 6000 graphic card is compatible with my desktop? If not what card is compatible with it?
- What should I do to pass the freeze stage?


[U][COLOR="Black"]Desktop specs:
[/COLOR][/U]

Ant-desktop
    description: Desktop Computer
    product: PROD00000000
    vendor: MEDIONPC
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=F00218DD-091E-B211-8000-64456E4E6973
  *-core
       description: Motherboard
       product: MS-6719
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       slot: &#65533;PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (11/12/2002)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 2800MHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 651 Host
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
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
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
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=12 mingnt=4 module=ohci1394
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: ATA Disk
                product: ST360012A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.30
                serial: 3KC0AKE6
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b9e8b9e8
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 77bf5e72-7d6f-4d5f-a7ee-d36ccf67ced1
                   size: 54GiB
                   capacity: 54GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-27 00:13:40 filesystem=ext3 modified=2008-11-06 08:44:02 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-06 08:04:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1380MiB
                   capacity: 1380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1380MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM 16X
                vendor: IDE
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom1
                version: 3.10
                serial: IDE     DVD-ROM 16X     3.10&#65533;
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom1
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CR-48XETE
                vendor: MITSUMI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 482R
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
        *-multimedia
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
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:10:dc:d4:aa:71
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
        *-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth1
             version: 00
             serial: 00:09:5b:1f:da:5d
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=32 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
        *-network:2
             description: Wireless interface
             product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@0000:00:07.0
             logical name: wlan0
             version: 20
             serial: 00:02:44:93:6b:ad
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,10/20/2005,5.103.10 ip=192.168.0.6 latency=32 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
        *-communication UNCLAIMED
             description: Communication controller
             product: 536EP Data Fax Modem
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
     *-scsi
          physical id: 1
          bus info: usb@4:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: OneTouch
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0125
             serial: 2HA19PVV
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=e9865289
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/OneTouch4
                version: 3.1
                serial: 1c2888f8-1edc-9c4f-828a-cca8f6ea3774
                size: 698GiB
                capacity: 698GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2007-11-08 01:49:02 filesystem=ntfs label=OneTouch4 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted

---

### Post by Ant68 on 2008-11-11
I have now have the confirmation the graphic card was suitable for my desktop. _[see google group link]("http://groups.google.com/group/computer-tech-support/browse_thread/thread/1bac9b9bc154cff0/d94f94aa7e2af7a1#d94f94aa7e2af7a1")_


the problem seems to be with the operating system (i.e. ubuntu).


Can anyone help troubleshooting the issue?

rs, Ant

---

### Post by Ant68 on 2008-12-12
AYI graphic card caused me trouble. I use now NVIDIA card and it works fine.

---

