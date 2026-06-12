---
title: "System Locks-up"
date: 2016-03-22
forum: Hardware
---

### Post by Spen53 on 2016-03-22
Hello,
I have a new install of UbuntuGnome and after an hour or two the mouse starts to get jerky and I can no longer use the left or right buttons.  The keyboard becomes non-functional, Ctr-Alt-Sup does absolutely nothing and then the mouse even stops moving.  I have tried Mint-Cinnamon, Mint-Mate and  ElementaryOS and always the same problem.  I have Intel Q6600 quad core 2.4GHz  with 8GiB Ram.

What log files can I sent if someone can help me.  This problem doesn't happen on Win7 but I want to give up on MS.  I have used Ubuntu on and off for over 10 years and never had this problem.

Thanks for all and any help and advice!

Here's a print out of "lshw".  

```
description: Computer
    width: 64 bits
    capabilities: smbios-2.5 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7983MiB
     *-cpu
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2403MHz
          capacity: 2403MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:c000(size=4096) memory:fd000000-fe9fffff ioport:e6000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK208 [GeForce GT 720]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:28 memory:fd000000-fdffffff memory:e8000000-efffffff memory:e6000000-e7ffffff ioport:cc00(size=128) memory:fe900000-fe97ffff
           *-multimedia
                description: Audio device
                product: GK208 HDMI/DP Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fe9fc000-fe9fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:fcffc000-fcffffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:feb00000-febfffff ioport:e0000000(size=2097152)
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:27 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=32) memory:febffc00-febffdff memory:febe0000-febeffff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:fea00000-feafffff ioport:e0200000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: c0
                serial: 14:da:e9:90:46:7e
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.0.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:30 memory:feac0000-feafffff ioport:dc00(size=128)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-34-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: Microsoft Wireless Optical Desktop
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@2:1
                   version: 73.73
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-34-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Audio device
                   product: Sound Blaster Play! 2
                   vendor: Creative Technology Ltd
                   physical id: 2
                   bus info: usb@3:2
                   version: 10.01
                   serial: 000000011134
                   capabilities: usb-2.00 audio-control
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-34-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-34-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fcffbc00-fcffbfff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-34-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 42.47
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Mass storage device
                      product: STM3250318AS
                      vendor: ST
                      physical id: 1
                      bus info: usb@1:2.1
                      logical name: scsi6
                      version: 3.07
                      serial: 801000002F00400002000200
                      capabilities: usb-2.10 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: STM3250318AS
                         vendor: ST
                         physical id: 0.0.0
                         bus info: scsi@6:0.0.0
                         logical name: /dev/sdd
                         version: 0307
                         serial: &#65533;
                         size: 232GiB (250GB)
                         capabilities: partitioned partitioned:dos
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=0004ed75
                       *-volume:0
                            description: Windows NTFS volume
                            physical id: 1
                            bus info: scsi@6:0.0.0,1
                            logical name: /dev/sdd1
                            version: 3.1
                            serial: bc930717-fed8-e245-b12c-a3c26e701af5
                            size: 98MiB
                            capacity: 100MiB
                            capabilities: primary bootable ntfs initialized
                            configuration: clustersize=4096 created=2012-05-08 21:57:03 filesystem=ntfs label=System Reserved state=clean
                       *-volume:1
                            description: Windows NTFS volume
                            physical id: 2
                            bus info: scsi@6:0.0.0,2
                            logical name: /dev/sdd2
                            logical name: /media/spencer/250
                            version: 3.1
                            serial: 88e22bd5-3032-7c44-9dac-2bb43f59c474
                            size: 232GiB
                            capacity: 232GiB
                            capabilities: primary ntfs initialized
                            configuration: clustersize=4096 created=2014-04-13 10:31:21 filesystem=ntfs label=250 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-usb:1
                      description: USB hub
                      product: USB 2.0 Hub
                      vendor: Terminus Technology Inc.
                      physical id: 4
                      bus info: usb@1:2.4
                      version: 1.11
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb
                         description: Printer
                         vendor: Brother Industries, Ltd
                         physical id: 1
                         bus info: usb@1:2.4.1
                         version: 1.00
                         serial: E74226K4N282864
                         capabilities: usb-2.00 bidirectional
                         configuration: driver=usblp maxpower=2mA speed=480Mbit/s
              *-usb:1
                   description: Generic USB device
                   product: USB WLAN
                   vendor: 802.11n
                   physical id: 3
                   bus info: usb@1:3
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.00
                   configuration: driver=rtl8192cu maxpower=500mA speed=480Mbit/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:b400(size=8) ioport:b080(size=4) ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: INTEL SSDSC2CT18
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 335u
             serial: CVKI311100WH180CGN
             size: 167GiB (180GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0990d46c
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: c4c844f1-b358-5440-b091-8ab8931a66b5
                size: 97GiB
                capacity: 97GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-07-09 14:59:22 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 70GiB
                capacity: 70GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4058MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 40GiB
                   configuration: mount.fstype=xfs mount.options=rw,relatime,attr2,inode64,noquota state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 25GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00S
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/sdb
             version: 0A80
             serial: WD-WCAVY4994129
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=20716dad
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.1.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: e03acdea-5fbb-f442-bd70-6e93be7851cf
                size: 906GiB
                capacity: 906GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-12-01 19:40:51 filesystem=ntfs label=2tb-1 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@2:0.1.0,3
                logical name: /dev/sdb3
                version: 3.1
                serial: 545873ca-f8c3-cf4e-be37-a4767e3ca73f
                size: 956GiB
                capacity: 956GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-12-13 21:19:16 filesystem=ntfs label=2tb-2 state=clean
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD30EZRX-00D
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             version: 0A80
             serial: WD-WCC4N1396437
             size: 2794GiB (3TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=000c0a3f
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                version: 3.1
                serial: aed8683c-a2e3-ab4f-b52c-d2fc6ecc8c5d
                size: 1464GiB
                capacity: 1464GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-12-08 23:08:55 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdc2
                version: 3.1
                serial: 3afb2077-91c4-a04a-a5fc-c387fdca66f9
                size: 1329GiB
                capacity: 1329GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-12-08 23:08:56 filesystem=ntfs state=clean
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223L
             vendor: TSSTcorp
             physical id: 0.1.0
             bus info: scsi@3:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlxc4e9841e2bca
       serial: c4:e9:84:1e:2b:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.2.0-34-generic firmware=N/A ip=192.168.0.20 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by deadflowr on 2016-03-22
Please use code tags when posting the output from a terminal.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by Spen53 on 2016-03-29
Deadflowr,  Thanks for your advice, I've never had to post a problem on "ubuntuforums.org" before.  I hope someone can help me with this problem that persists even on a Live disk (usb).

again thanks

Spencer

---

### Post by weatherman2 on 2016-03-30
You have provided output that shows what kind of hardware you have.  But unless someone happens to familiar with issues with that specific hardware (I'm not), that's not going to be enough to help you.

Although you say Windows 7 works fine, I'd still rule out hardware issues.  I'd run Memtest overnight and make sure it is still running in the morning.  Also, I'd check CPU temperatures and make sure the CPU isn't overheating.  You can install psensor in Ubuntu from a live boot (after you enable the "universe" repository in Ubuntu Software Center) and that should let you monitor CPU temperatures.  Either way, it wouldn't hurt to make sure the CPU heat sink and fan are working and not dirty.

Which versions of these operating systems have you been trying?  Old ones?  Really new ones?  It makes a difference.  I would try Ubuntu 14.04 LTS as it should be stable.

---

### Post by Spen53 on 2016-03-30
I have been doing clean installs of the latest releases of Mint Cinnamon 17.3 lts, Mint Mate 17.3 lts, Elementaryos 0.3.2 stable, and ubuntu-gnome 15.10 desktop, all the same problem.  I've installed Conky each time to keep an eye the processor and the RAM.  The processor rarely goes over 50% usage and the RAM 4.9GB of 8GB total.  

I'll run a Memtest tonight to eliminate this possibility.  I'll try a older version of "Mint 13" soon but first, could I send a syslog read out or other log file to help locate this problem?

thanks

---

### Post by X-RED_Tech on 2016-03-30
```
[COLOR=#000000][FONT=Ubuntu Mono]*-display[/FONT][/COLOR]description: VGA compatible controller
product: GK208 [**GeForce GT 720**][COLOR=#222222][FONT=Verdana]
```


You need nvidia drivers (361.42) for this otherwise: a) it'll underperform and b) all sorts of issues with lock-ups, suspension, etc. can occur.

[/FONT][/COLOR]

---

