---
title: "Boot failure while 2nd SATA HDD is connected."
date: 2009-11-04
forum: Hardware
---

### Post by colalord on 2009-11-04
Ok, I'm not a complete noob, but I'm not an expert either.

I have an Alienware M9700 laptop.  It's about 2 to 3 years old and it has been running Ubuntu/Kubuntu since the beginning up through Kubuntu 9.04.  However, since I've started trying to get 9.10 to work I have been having nothing but one problem after another.  I've gotten most of the problems ironed out, but I have one major problem let, and that is with my hard drive configuration.

I have an nVidia SATA w/ RAID controller, and 2x 100GB Seagate SATA hard drives configured in this system.  I had to use the Alt i386 ISO to install because the primary graphical desktop installer disk only viewed my hard drives as one 200GB disk in RAID Striped configuration with no other options.  With the Alt disk things installed smoothly.  However, the problems started to occur again after booting the fresh install.

When I boot the freshly installed system it goes to the Kubuntu splash screen and sits there for about 30 seconds after which it dumps me to a BusyBox terminal with the prompt "(initramfs)".  I have pulled a lot of logs for diagnosing this problem which you will find below.  However, it says something about it not being able to mount the root filesystem and then times out.  If I do a command such as "ls /dev | grep sd" it displays the drives sda and sdb, but it doesn't display their respective partitions. 

(sda1 [windows], sda2 [extended], sda5 [ubuntu], sda6 [swap], sdb1 [data])

The odd thing I find is it only times out while trying to mount the root filesystem while the second SATA HDD is connected to the system.  e.g. If I physically disconnect the second SATA HDD from the system and boot up it will find the root filesystem which is located on sda5.

I can also boot into my installation of Windows Vista with or without the second hard drive connected and access my data.  Therefore, the drive is verifiable still good and still working properly.  As near as I can tell there is a kernel and/or a driver/module issue.

This is a new problem that I have not experienced before.  I was running Kubuntu 9.04 happily before without any such issues.  The only identifiable changes are I have reformatted the partition sda5 as ext4 as where it was ext3 previously, and that I have installed Kubuntu 9.10.  I doubt that the ext4 FS is the issue as I'm able to boot into the system while the second hard drive is disconnected which indicates that the FS is working.

Please let me know if anyone has an idea as where I'm at a loss?  Thank you very much!

Here are the log captures I have taken:

dmesg when system hangs on boot.
```
[    1.231325] sata_nv 0000:00:07.0: version 3.5
[    1.231535] sata_nv 0000:00:07.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.231575] sata_nv 0000:00:07.0: setting latency timer to 64
[    1.231629] scsi0 : sata_nv
[    1.231701] scsi1 : sata_nv
[    1.234603] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA1] -> GSI 21 (level, low) -> IRQ 21
[    1.234634] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.234677] scsi2 : sata_nv
[    1.234717] scsi3 : sata_nv
[    2.232382] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.232410] sd 2:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    2.232444] sd 2:0:0:0: [sda] Write Protect is off
[    2.232447] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.232465] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.232564]  sda: sda1 sda2 < sda5 sda6 >
[    2.269693] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.412376] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.412399] sd 3:0:0:0: [sdb] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    2.412429] sd 3:0:0:0: [sdb] Write Protect is off
[    2.412432] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.412448] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.412532]  sdb: sdb1
[    2.423082] sd 3:0:0:0: [sdb] Attached SCSI disk
[    7.834697] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    7.836479] sd 6:0:0:0: [sdc] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[    7.837225] sd 6:0:0:0: [sdc] Write Protect is off
[    7.837228] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[    7.837230] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    7.840225] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    7.840227]  sdc:
[    7.987225] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    7.987229] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  116.297823] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  116.299371] sd 7:0:0:0: [sdc] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[  116.300367] sd 7:0:0:0: [sdc] Write Protect is off
[  116.300369] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  116.300372] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.303367] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.303370]  sdc:
[  116.780354] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.780359] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

fdisk -l /dev/sda
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a076b8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6789    54525952    7  HPFS/NTFS
/dev/sda2            6790       12161    43150590    5  Extended
/dev/sda5            6790       12035    42138463+  83  Linux
/dev/sda6           12036       12161     1012063+  82  Linux swap / Solaris

```

ls /dev (when system boot hangs)
sdc = usb flash drive for log capture
```
brw-rw----    1 0        0          8,  16 sdb
brw-rw----    1 0        0          8,   0 sda
brw-rw----    1 0        0          8,  32 sdc

```

lshw (when system is booted with 1 hdd)
```
sylux
    description: Notebook
    product: Aurora m9700
    vendor: alienware
    version: AB040
    serial: W830DA AB040
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=339C7DB0-2E52-6498-206C-0003252AB754
  *-core
       description: Motherboard
       product: Aurora m9700
       vendor: alienware
       physical id: 0
       version: AB040
       serial: W830DA AB040
       slot: W830DA AB040
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: W830D318 (01/25/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-44
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.4.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:10 ioport:ec00(size=32) ioport:5000(size=64) ioport:6000(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:febfe000-febfefff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:febffc00-febffcff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:d800(size=256) ioport:d400(size=256) memory:febfc000-febfcfff
     *-communication UNCLAIMED
          description: Modem
          product: CK804 AC'97 Modem
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0 maxlatency=5 mingnt=2
          resources: ioport:e400(size=256) ioport:e080(size=128) memory:febfd000-febfdfff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi5
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-cdrom
             description: DVD writer
             product: DVD RW AD-5540A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.J0
             serial: [Optiarc DVD RW AD-5540A 1.J0 Oct12,2006
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:e000(size=8) ioport:dc00(size=4) ioport:d080(size=8) ioport:d000(size=4) ioport:cc00(size=16) memory:febfb000-febfbfff
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:08.0
          logical name: scsi2
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:c880(size=8) ioport:c800(size=4) ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=16) memory:febfa000-febfafff
        *-disk
             description: ATA Disk
             product: ST910021AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.04
             serial: 3MH0CDTC
             size: 93GiB (100GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=5a076b8a
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: caf6d36e-ba0b-d440-b533-78615356f732
                size: 51GiB
                capacity: 52GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-01-20 03:00:26 filesystem=ntfs state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 41GiB
                capacity: 41GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 40GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 988MiB
                   capabilities: nofs
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: memory:f5e00000-f5ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:f5ffe800-f5ffefff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 6.1
             bus info: pci@0000:01:06.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master
             configuration: driver=sdhci-pci latency=64
             resources: irq:17 memory:f5fff400-f5fff4ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 6.2
             bus info: pci@0000:01:06.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=ricoh-mmc latency=0
             resources: irq:4 memory:f5fff800-f5fff8ff
        *-generic:2 UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 6.3
             bus info: pci@0000:01:06.3
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
             resources: memory:f5fffc00-f5fffcff
        *-multimedia
             description: Multimedia controller
             product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 8
             bus info: pci@0000:01:08.0
             version: d1
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84
             resources: irq:18 memory:f5ffe000-f5ffe7ff
        *-network DISABLED
             description: interface
             product: AGN300 802.11 a/b/g True MIMO Wireless Card
             vendor: Airgo Networks Inc
             physical id: a
             bus info: pci@0000:01:0a.0
             logical name: wmaster0
             version: 01
             serial: 06:04:f7:01:06:05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical
             configuration: driver=agnx-pci latency=248 maxlatency=255 mingnt=24
             resources: irq:19 memory:f5fc0000-f5fdffff memory:f5f00000-f5f7ffff
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:8000(size=4096) memory:f6000000-f67fffff ioport:9df00000(size=33554432)
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:9000(size=4096) memory:f6800000-f68fffff
        *-network
             description: Ethernet interface
             product: 88E8055 PCI-E Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: 0
             bus info: pci@0000:05:00.0
             logical name: eth0
             version: 12
             serial: 00:03:25:2a:b7:54
             size: 1GB/s
             capacity: 1GB/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
             resources: irq:28 memory:f68fc000-f68fffff ioport:9800(size=256) memory:f68c0000-f68dffff(prefetchable)
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:a000(size=4096) memory:f6900000-fa9fffff ioport:9ff00000(size=536870912)
        *-display
             description: VGA compatible controller
             product: G71 [GeForce Go 7900 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:06:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:17 memory:f9000000-f9ffffff memory:a0000000-afffffff(prefetchable) memory:f8000000-f8ffffff ioport:ac00(size=128) memory:fa9e0000-fa9fffff(prefetchable)
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:27 ioport:b000(size=4096) memory:faa00000-feafffff ioport:bff00000(size=536870912)
        *-display
             description: VGA compatible controller
             product: G71 [GeForce Go 7900 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:07:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fc000000-fcffffff ioport:bc00(size=128) memory:feae0000-feafffff(prefetchable)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: f
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: Windows FAT volume
             vendor: MSWIN4.1
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             logical name: /media/usb0
             version: FAT32
             serial: 1a8d-3956
             size: 7711MiB
             capacity: 7712MiB
             capabilities: fat initialized
             configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,errors=remount-ro signature=2c6b7369 state=mounted

```

lspci (when system is booted with 1 hdd)
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:04.1 Modem: nVidia Corporation CK804 AC'97 Modem (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
01:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
01:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
01:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
01:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0a.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7900 GS] (rev a1)
07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7900 GS] (rev a1)

```

cat /proc/partitions (when boot hangs)
```
major minor  #blocks  name

   8        0   97685784 sda
   8       16   97685784 sdb
 252        0  195371520 dm-0
 252        1   54525952 dm-1
   8       32    7897088 sdc

```

cat /proc/scsi/scsi (when system boot hangs)
```
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST910021AS       Rev: 3.04
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST910021AS       Rev: 3.04
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: Optiarc  Model: DVD RW AD-5540A  Rev: 1.J0
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: Ut165    Model: USB2FlashStorage Rev: 0.00
  Type:   Direct-Access                    ANSI  SCSI revision: 02

```

Thanks for your help!

---

### Post by Ginsu543 on 2009-11-04
If you haven't done so already, try removing dmraid from your system (sudo apt-get remove dmraid in Terminal or through Synaptic). I too could not boot Karmic if I had my second WD Raptor connected, but once I removed dmraid, Karmic boots normally with all my drives plugged in. It worked for me, it might work for you.

---

### Post by colalord on 2009-11-04
> Ginsu543  	
Re: Boot failure while 2nd SATA HDD is connected.

If you haven't done so already, try removing dmraid from your system (sudo apt-get remove dmraid in Terminal or through Synaptic). I too could not boot Karmic if I had my second WD Raptor connected, but once I removed dmraid, Karmic boots normally with all my drives plugged in. It worked for me, it might work for you. 

You know, I don't know how to thank you enough.  I did as you said and removed dmraid.  Go figure the system worked as it was supposed to.  I was able to boot with both hdd's connected with no problems.  Thank you again  Ginsu543 for helping with my problem.

---

