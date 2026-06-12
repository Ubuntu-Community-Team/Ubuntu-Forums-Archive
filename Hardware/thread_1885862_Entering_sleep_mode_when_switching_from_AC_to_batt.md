---
title: "Entering sleep mode when switching from AC to battery mode"
date: 2011-11-24
forum: Hardware
---

### Post by Jun-01 on 2011-11-24
I ran Ubuntu from version 9.10 to 11.04 in my laptop. Currently using Mint 11 GNOME version.

The laptop always goes to sleep mode when switching from AC to battery power while using all the versions of Ubuntu and Mint cited above. I can resume without any apparent problems.

I suspect this strange behavior might be a power management bug caused by the Mobility Radeon HD 2400 that equips my mobo, as I have read many stories about unfortunate ATI card owners having problems with power management, OpenGL and etc. both with radeon and fglrx. Well, it's only a guess. Maybe this problem actually has nothing to do with the GPU.

I'm using the radeon module since 10.04, but also used fglrx in the past, when my GPU had a horrible performance with the open source drivers. But I can't tell if using the proprietary drivers results the same problem.

Does anyone know a solution/workaround to fix this unwanted behavior?

lshw output:
```

    description: Notebook
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=80D4549D-2766-0010-80D7-8ED45495C907
  *-core
       description: Motherboard
       product: U50SA1
       vendor: ECS
       physical id: 0
       version: N/A
       serial: 1234AA782E
     *-firmware
          description: BIOS
          vendor: ODM
          physical id: 0
          version: 1.04
          date: 07/08/2008
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: uPGA 479M
          size: 1GHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 2MiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: DIMM2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:9000(size=4096) memory:d8000000-d80fffff ioport:d0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 2400
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:40 memory:d0000000-d7ffffff ioport:9000(size=256) memory:d8000000-d800ffff memory:d8020000-d803ffff
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1080(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TMC0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:d8304000-d8304fff
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:d8305000-d8305fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:d8306000-d8306fff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:03:0d:a8:6a:a2
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 memory:d8307000-d830707f ioport:1000(size=128)
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:10c8(size=8) ioport:10bc(size=4) ioport:10c0(size=8) ioport:10b8(size=4) ioport:10a0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK2552GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: 48JLF0ALS
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8b66b50c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: f4a94ae2-6a2d-154c-b9cd-9f1bef49c414
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-26 15:03:08 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/80227696227690C0
                   version: 3.1
                   serial: b49f07d4-847c-a84a-90f7-afda45ff50b9
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-07-09 02:31:02 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2002MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 35GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:d8300000-d8303fff
     *-scsi
          physical id: 2
          bus info: usb@1:6
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
  *-battery
       physical id: 1
       slot: MAIN
       capacity: 48840mWh
       configuration: voltage=11.1V
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 2
       capabilities: outbound
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:5
       logical name: wlan1
       serial: 00:0d:09:30:d6:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 ip=172.16.253.31 link=yes multicast=yes wireless=IEEE 802.11bgn
```NOTE: The wireless adapter listed in the lshw output above is actually a USB one with better reception than my mobo's built-in wireless card. The built-in card is listed by lsusb as "Micro Star International RT2573"

---

### Post by BC59 on 2011-11-24
From 11.10 (and in 11.04 it was the same) System Settings-->Power you can change the settings to suspend or not and the time to do it, on battery or AC.

---

