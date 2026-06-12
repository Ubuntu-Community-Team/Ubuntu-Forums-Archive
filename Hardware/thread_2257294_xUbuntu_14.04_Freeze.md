---
title: "xUbuntu 14.04 Freeze"
date: 2014-12-18
forum: Hardware
---

### Post by acetace on 2014-12-18
Many people has reported 

Symptom of the freeze
[LIST]
[*]Unable to move mosue 
[*]Unable to use keyboard 
[*]Unable to get into console only mode (ctrl + alt + F1) 
[*]No particularity about currently running applications (including minimized application visable on the GUI), sometimes it is Firefox, somtimes it is Thunderbird, sometimes it is browsing the recycling bin (thunar)) 
[/LIST]

Problem does not previously occur in Ubuntu 12.04.4 and starts to appear after *fresh install* for xUbuntu 14.04

Following are some additional configuration information
[LIST]
[*]ACPI power management is diabled by unchecking ACPI managment checkboxy through xUbuntu GUI 
[*]Primary hard drive SMART information all passed and healthy. 
[*]Sensors (sensors from lm-sensors and aticonfig --odgt) data shows no overheating component or significant deviation of the voltage reading
[*]System is setup and configured to dual boot with Windows 7. The crash and freeze is not felt when booted into Winodws 7 (unfortunately, kind of discouraging given the many years I have used Ubuntu as my primary box). 
[/LIST]

Freeze does not occur all the time, but one line around the same kernel time seems to foreshadow the impending failure see output for dmesg.

Console Ouput of Various Commands
**Xubuntu Version**
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

```

**Kernel**
```

$ uname -a
Linux andy-home 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

**Hardware**
```

$ sudo lshw.txt
andy-home
    description: Desktop Computer
    product: Rampage Formula (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=6074001E-8C00-012F-160F-001FC6619DD6
  *-core
       description: Motherboard
       product: Rampage Formula
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MS1C83BZFL00461
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1001
          date: 03/11/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
          serial: To Be Filled By O.E.M.
          slot: LGA775
          size: 3GHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 3f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82X38/X48 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=x38_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82X38/X48 Express Host-Primary PCI Express Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:fe700000-fe7fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Curacao XT [Radeon R9 270X]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:49 memory:d0000000-dfffffff memory:fe780000-fe7bffff ioport:a000(size=256) memory:fe7c0000-fe7dffff
           *-multimedia
                description: Audio device
                product: Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:48 memory:fe7fc000-fe7fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:9800(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:9880(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:9c00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fe6ffc00-fe6fffff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:fe6f8000-fe6fbfff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f0000000-f03fffff ioport:fdf00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fea00000-feafffff ioport:f0400000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 12
                serial: 00:1f:c6:61:9d:d6
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:feafc000-feafffff ioport:d800(size=256) memory:feac0000-feadffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:c000(size=4096) memory:fe900000-fe9fffff ioport:f0600000(size=2097152)
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress bus_master cap_list rom
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) memory:fe9f0000-fe9fffff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:b000(size=4096) memory:fe800000-fe8fffff ioport:f0800000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 12
                serial: 00:1f:c6:61:9d:d7
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.114 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:46 memory:fe8fc000-fe8fffff ioport:b800(size=256) memory:fe8c0000-fe8dffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:9080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:9400(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:9480(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe6ff800-fe6ffbff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR5212/AR5213 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: wlan0
                version: 01
                serial: 00:17:9a:01:bb:7c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.13.0-40-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:febf0000-febfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:06:03.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:19 memory:febef800-febeffff ioport:ec00(size=128)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:8000(size=8) ioport:7c00(size=4) ioport:7880(size=8) ioport:7800(size=4) ioport:7480(size=16) ioport:7400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe6ff400-fe6ff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:9000(size=8) ioport:8c00(size=4) ioport:8880(size=8) ioport:8800(size=4) ioport:8480(size=16) ioport:8400(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD6400AAKS-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCASY0697651
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00001e8a
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 7823-e5ff
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-07-16 05:48:47 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 229663cb-62f9-2649-a5de-fdc12ce3af30
                size: 119GiB
                capacity: 120GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-07-16 05:49:39 filesystem=ntfs state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 476GiB
                capacity: 476GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5912MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 363GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /mnt/dd
                   capacity: 93GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /
                   capacity: 13GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00J
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: 80.0
             serial: WD-WCAYY0150334
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7fd0dd96-6f2c-4439-b29f-8bb8bb93ee46 sectorsize=512
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                logical name: /mnt/2TBD
                version: 1.0
                serial: 5df921a5-283a-4a94-8312-00ac02880440
                size: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-09-05 07:35:54 filesystem=ext4 label=2TBDint lastmountpoint=/mnt/2TBD modified=2014-12-18 14:14:33 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-12-18 14:14:33 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-2014L1T
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD30EZRX-00M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             version: 80.0
             serial: WD-WCAWZ2730360
             size: 2794GiB (3TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4368b068-3dae-4d9a-b018-c67a40a91c0e sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /mnt/3TBD
                version: 1.0
                serial: a9ad77bf-eabe-40af-b17c-fe29428cf4bd
                size: 2794GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-09-03 08:06:10 filesystem=ext4 label=3TBD lastmountpoint=/mnt/3TBD modified=2014-12-18 14:14:33 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-12-18 14:14:33 state=mounted

```

**Kernel Debug Ring (dmesg)**
[LIST]
[*]The following message does not show all the time 
[*]If it does show there is a high likelihood that the system will encounter a crash some point down the line. 
[*]A system start that has the greatest uptime will not encounter this message. 
[*]If it does it always show around the [299.xxxxxx] kernel time. 
[/LIST]
```

$ dmesg
.....
[  299.816012] mce: [Hardware Error]: Machine check events logged
.....

```

[B]mcelog
[/B]Following the information from above, mcelog is examined.
```

$ sudo mcelog

```

```

[/var/log/mcelog]
MCE 0
CPU 0 BANK 0 
TIME 1418770210 Tue Dec 16 17:50:10 2014
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1418770210 Tue Dec 16 17:50:10 2014
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1418770210 Tue Dec 16 17:50:10 2014
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23

```

---

### Post by ajgreeny on 2014-12-18
Have you tried using the open source radeon driver for the graphic card rather than the fglrx currently in use?

Or try the most recent fglrx from AMD as suggested in [http://ubuntuforums.org/showthread.php?t=2240403](http://ubuntuforums.org/showthread.php?t=2240403)

---

### Post by acetace on 2014-12-23
Hi ajgreeny:

Thanks for the reply and sorry for the delay. I have tried both the oopen source ati driver as well as the propriatory driver sitting in the ubuntu repository, the result is the same. However, I did not try to fglrx-update package. I was going to try the latest Catalyst driver for linux directly off AMD, however, I stopped and thought about it.

If video card driver is really the cause, I should not get this very inconsistent freeze and reading of the dmesg log. Also the computer should fail all the time with 100% certainty. However, if I do not encounter that message in the dmesg log I can have a very long uptime without encountering the freeze. This do me does not sound like a video card issue.

Thanks for your suggestion, ajgreeny, and let me know if there is anything you think I could try.


acetace

---

### Post by acetace on 2015-01-04
If anybody is wondering, I have gained stability by doing the following tweaks to BIOS

[LIST]
[*]Disable legacy floppy drive support
[*]Disable Intel Speed Step technology (aka let your OS manage CPU speed as mentioned in this post [http://ubuntuforums.org/showthread.php?t=2257257](http://ubuntuforums.org/showthread.php?t=2257257))
[*]Set flag to enable identification of processor core (E8400 has 2 cores)
[/LIST]

Can somebody confirm these help them as well. Does this constitute a bug (lack of support for the hardware configuration) or a setting (as expected and should be added to installation note as in these should be set to begin with)? Should I file a report to the Ubuntu community for this observation?


Cheers.

---

