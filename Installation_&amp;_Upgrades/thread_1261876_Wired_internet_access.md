---
title: "Wired internet access"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by AdeBruijn on 2009-09-09
[FONT=Arial][SIZE=2]I have been using ubuntu for approximately one year now. I am now using a Packard Bell, MZ35 laptop running Ubuntu 9.04 and I cannot get access to the internet. I did find some threats with similar problems but I'm not familiar enough to understand some of the details, hoping that one of u will help me.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**pppoeconf** finds three ethernet devices[/SIZE][/FONT]
[FONT=Arial][SIZE=2]eth0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]pan0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]wlan0[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]But returns: Sorry, I scanned 3 interfaces, but the Access Concentrator of your provider did not respons. Please check your network and modem cables. Antoher reason for the scan failure may also be another running pppoe process which controls the modem[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]**ifconfig**. It seems that it contains a clue because there is no ip-adress for the laptop at eth0.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]----------------------[/SIZE][/FONT]
[FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:1b:24:3b:a9:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 [/SIZE][/FONT]
[FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]pan0      Link encap:Ethernet  HWaddr ce:15:51:2d:1f:e0  
          inet6 addr: fe80::cc15:51ff:fe2d:1fe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:3b:ca:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]wmaster0  Link encap:UNSPEC  HWaddr 00-0D-F0-3B-CA-96-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]--------------------[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]**pinging** [www.google**.com]("http://www.google.com/")** does not deliver either.:confused:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]The connection is up because I switched cables with my (windows) desktop or another (ubuntu) laptop.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT][FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]System specifications are  pasted below (lshw)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Any help would be appreciated.:P[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Cheers,[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Arjan[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]---------------------------------------------------[/SIZE][/FONT]
    description: Notebook
    product: EasyNote MZ35
    vendor: Packard Bell BV
    version: PB77Q07586
    serial: 111415880139
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=D13A72C0-001B-243B-A902-4E45435F4349
  *-core
       description: Motherboard
       product: EasyNote MZ35
       vendor: Packard Bell BV
       physical id: 0
       version: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       serial: QPCPBD72202172&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
     *-firmware
          description: BIOS
          vendor: Packard Bell
          physical id: 0
          version: V0.20 (02/06/2007)
          size: 102KiB
          capacity: 14MiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U23
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: CACHE1
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: CACHE2
             size: 1MiB
             capabilities: burst external write-back
     *-cache
          description: L2 cache
          physical id: 7
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: J400
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: J401
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: J501
        *-bank:3
             description: DIMM DRAM Synchronous
             physical id: 3
             slot: J500
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: [EMAIL="pci@0000:00:00.0"]pci@0000:00:00.0[/EMAIL]
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: [EMAIL="pci@0000:00:01.0"]pci@0000:00:01.0[/EMAIL]
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: [EMAIL="pci@0000:01:05.0"]pci@0000:01:05.0[/EMAIL]
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=66 mingnt=8
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: [EMAIL="pci@0000:00:12.0"]pci@0000:00:12.0[/EMAIL]
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST980811AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: [EMAIL="scsi@0:0.0.0"]scsi@0:0.0.0[/EMAIL]
                logical name: /dev/sda
                version: 3.AL
                serial: 5LY4RT3Y
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b6848ea6
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: [EMAIL="scsi@0:0.0.0,1"]scsi@0:0.0.0,1[/EMAIL]
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 71c197c8-b18f-4992-9742-1c3d2dd16dcf
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-08 18:54:45 filesystem=ext3 modified=2009-09-09 09:01:11 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-09 08:35:24 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: [EMAIL="scsi@0:0.0.0,2"]scsi@0:0.0.0,2[/EMAIL]
                   logical name: /dev/sda2
                   size: 1262MiB
                   capacity: 1262MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1262MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: [EMAIL="pci@0000:00:13.0"]pci@0000:00:13.0[/EMAIL]
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: [EMAIL="pci@0000:00:13.1"]pci@0000:00:13.1[/EMAIL]
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: [EMAIL="pci@0000:00:13.2"]pci@0000:00:13.2[/EMAIL]
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: [EMAIL="pci@0000:00:14.0"]pci@0000:00:14.0[/EMAIL]
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: [EMAIL="pci@0000:00:14.1"]pci@0000:00:14.1[/EMAIL]
             logical name: scsi3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
           *-cdrom
                description: DVD writer
                product: UJ-850D
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: [EMAIL="scsi@3:0.0.0"]scsi@3:0.0.0[/EMAIL]
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.10
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: [EMAIL="pci@0000:00:14.2"]pci@0000:00:14.2[/EMAIL]
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
             bus info: [EMAIL="pci@0000:00:14.3"]pci@0000:00:14.3[/EMAIL]
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
             bus info: [EMAIL="pci@0000:00:14.4"]pci@0000:00:14.4[/EMAIL]
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: [EMAIL="pci@0000:09:02.0"]pci@0000:09:02.0[/EMAIL]
                logical name: eth0
                version: 10
                serial: 00:1b:24:3b:a9:02
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-network:1
                description: Wireless interface
                product: RT2561/RT61 rev B 802.11g
                vendor: RaLink
                physical id: 4
                bus info: [EMAIL="pci@0000:09:04.0"]pci@0000:09:04.0[/EMAIL]
                logical name: wmaster0
                version: 00
                serial: 00:0d:f0:3b:ca:96
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:15:51:2d:1f:e0
       capabilities: ethernet physical
       configuration: broadca

---

