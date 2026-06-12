---
title: "ram suggested to comfortably run ubuntu"
date: 2012-06-27
forum: Hardware
---

### Post by godfreezone on 2012-06-27
I have just dumped windows for ubuntu.
I have 2 questions:

1. can someone recommend a program which will tell me what kind of ram i need to buy
2. and recommend how much I should run (currently only got 2gig and experiencing an annoying slowing of machine under what i would have thought not very testing conditions)

thx,
Godfrey

---

### Post by Yellow Pasque on 2012-06-28
I don't think there's a magic program that spits out your type of memory. Just post what type of system it is (or google for the specs yourself). If still confused, post output of lshw:
```
sudo apt-get install lshw
sudo lshw
```


2GB is a good chunk of memory unless you're doing heavy multitasking or running a VM. When you start experiencing slowness, check the free command to see if all of your RAM is being used:
```
free -m
```

---

### Post by mojo risin on 2012-06-28
Wow 2 GB of RAM should be really enough to run your Laptop. I have got only 512mb RAM (and I could still run Lucid lynx on it when i had it)
However if your laptop is easy to open yu can do so and have a look at the ram. There are so many different kind of ram cards that this I think is the best to do to get the best use of it.

---

### Post by godfreezone on 2012-06-28
thanks Mojo, what do you make of this?
I isolated the relevants pieces of text and read them but feel none the wiser; perhaps you could peg the exact line that gives sufficient description that I could then relay to vendor in order to buy a couple of gig of ram, perhaps upgrading to 8 gig, depending on stick sizes

but then again, perhaps i am wasting money, as you suggest (?)
thx for your time in posting  a reply mate; much appreciated and have a nice day/night
Godfrey

 ```
sudo lshw
description: Low Profile Desktop Computer
    product: 8813B46 (NONE)
    vendor: LENOVO
    version: ThinkCentre M55
    serial: L3D9755
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=low-profile cpus=2 family=NONE keyboard_password=disabled power-on_password=disabled sku=NONE uuid=8062D97A-9FAF-DC11-AE4F-D023FFC1B40C
  *-core
       description: Motherboard
       product: LENOVO
       vendor: LENOVO
       physical id: 0
       version: NONE
       serial: NONE
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 2JKT49AUS
          date: 12/12/2008
          size: 117KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot edd acpi usb ls120boot smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: LGA775/PSC/TJS
          size: 2133MHz
          capacity: 3600MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
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
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 0
             serial: 821A2093umber
             slot: J6G1
             size: 1GiB
             width: 40968 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 1
             serial: Serial Number
             slot: J6G2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 2
             serial: 821A2073umber
             slot: J6H1
             size: 1GiB
             width: 41992 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [empty]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 3
             serial: Serial Number
             slot: J6H2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
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
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:d0000000-d00fffff memory:c0000000-cfffffff ioport:30e0(size=8)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3000(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d0504000-d05043ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:d0300000-d0303fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:80200000-803fffff ioport:80400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:d0100000-d01fffff ioport:80000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:6b:61:0c:f9
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v2.04 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:d0100000-d010ffff
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3020(size=32)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:3040(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3060(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d0504400-d05047ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d0200000-d02fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:21 memory:d0204000-d02047ff memory:d0200000-d0203fff
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30b0(size=16) ioport:30a0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DH16A1S
                vendor: ATAPI
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: HL62
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: P22O
                serial: PVE341Z9S52G0M
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009aedd
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3703eb1d-9da9-48f2-8a07-0d2d7204cfff
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-15 00:24:01 filesystem=ext4 lastmountpoint=/ modified=2012-06-15 00:41:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-06-29 08:37:40 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 2037MiB
                   capacity: 2037MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2037MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0504800-d05048ff ioport:3080(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:3410(size=8) ioport:3404(size=4) ioport:3408(size=8) ioport:3400(size=4) ioport:30d0(size=16) ioport:30c0(size=16)
     *-scsi:0
          physical id: 2
          bus info: usb@2:6
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 29GiB (32GB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/584F-D009
                version: FAT32
                serial: 584f-d009
                size: 29GiB
                capacity: 29GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1001,gid=1001,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@1:1
          logical name: scsi7
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/sr1
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000001000
                   size: 33MiB
                   capacity: 33MiB
                   capabilities: hfsplus initialized
                   configuration: checked=2011-10-14 22:17:25 created=2011-10-14 11:17:25 filesystem=hfsplus lastmountedby=LSDf modified=2011-10-14 22:17:26 state=unclean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
godfreysown@Godfreysown:~$
```

---

### Post by oldfred on 2012-06-28
Please use code tags for any long data post which you can easily add by highlighting your data and thing clicking on the # in the edit panel above your post.

My laptop with 1.5GB very occasionally stalls for a few seconds (using swap) when I open a lot of larger programs at once. I thought it was partially because I run 64 bit when I really should use the 32 bit version. But I want the same version as I use on my Desktop, so I live with it.

If editing videos there is not enough RAM, otherwise your 2GB should be ok. 4GB used to be the current sweet spot, but with memory prices so low many new systems have a lot more.

---

### Post by godfreezone on 2012-06-28
Apologies to Temujin and Mojo,
that last output post from sudo lshw was for Temujin,  not Mojo

Godfree

---

### Post by godfreezone on 2012-06-28
Temujin,
Here is the output from free -m
 sudo lshw
godfreysown               
    description: Low Profile Desktop Computer
    product: 8813B46 (NONE)
    vendor: LENOVO
    version: ThinkCentre M55
    serial: L3D9755
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=low-profile cpus=2 family=NONE keyboard_password=disabled power-on_password=disabled sku=NONE uuid=8062D97A-9FAF-DC11-AE4F-D023FFC1B40C
  *-core
       description: Motherboard
       product: LENOVO
       vendor: LENOVO
       physical id: 0
       version: NONE
       serial: NONE
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 2JKT49AUS
          date: 12/12/2008
          size: 117KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot edd acpi usb ls120boot smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: LGA775/PSC/TJS
          size: 2133MHz
          capacity: 3600MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
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
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 0
             serial: 821A2093umber
             slot: J6G1
             size: 1GiB
             width: 40968 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 1
             serial: Serial Number
             slot: J6G2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 2
             serial: 821A2073umber
             slot: J6H1
             size: 1GiB
             width: 41992 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [empty]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 3
             serial: Serial Number
             slot: J6H2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
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
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:d0000000-d00fffff memory:c0000000-cfffffff ioport:30e0(size=8)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3000(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d0504000-d05043ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:d0300000-d0303fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:80200000-803fffff ioport:80400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:d0100000-d01fffff ioport:80000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:6b:61:0c:f9
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v2.04 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:d0100000-d010ffff
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3020(size=32)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:3040(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3060(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d0504400-d05047ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d0200000-d02fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:21 memory:d0204000-d02047ff memory:d0200000-d0203fff
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30b0(size=16) ioport:30a0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DH16A1S
                vendor: ATAPI
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: HL62
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: P22O
                serial: PVE341Z9S52G0M
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009aedd
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3703eb1d-9da9-48f2-8a07-0d2d7204cfff
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-15 00:24:01 filesystem=ext4 lastmountpoint=/ modified=2012-06-15 00:41:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-06-29 08:37:40 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 2037MiB
                   capacity: 2037MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2037MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0504800-d05048ff ioport:3080(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:3410(size=8) ioport:3404(size=4) ioport:3408(size=8) ioport:3400(size=4) ioport:30d0(size=16) ioport:30c0(size=16)
     *-scsi:0
          physical id: 2
          bus info: usb@2:6
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 29GiB (32GB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/584F-D009
                version: FAT32
                serial: 584f-d009
                size: 29GiB
                capacity: 29GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1001,gid=1001,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@1:1
          logical name: scsi7
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/sr1
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000001000
                   size: 33MiB
                   capacity: 33MiB
                   capabilities: hfsplus initialized
                   configuration: checked=2011-10-14 22:17:25 created=2011-10-14 11:17:25 filesystem=hfsplus lastmountedby=LSDf modified=2011-10-14 22:17:26 state=unclean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
godfreysown@Godfreysown:~$ 

What maketh thee of it?
M

> **Temüjin said:**
> I don't think there's a magic program that spits out your type of memory. Just post what type of system it is (or google for the specs yourself). If still confused, post output of lshw:
```
sudo apt-get install lshw
sudo lshw
```
2GB is a good chunk of memory unless you're doing heavy multitasking or running a VM. When you start experiencing slowness, check the free command to see if all of your RAM is being used:
```
free -m
```

---

### Post by godfreezone on 2012-06-28
With apologies Oldfred,
due notice taken and thank you.
Godfree

---

### Post by godfreezone on 2012-06-28
```
> **oldfred said:**
> Please use code tags for any long data post which you can easily add by highlighting your data and thing clicking on the # in the edit panel above your post.

My laptop with 1.5GB very occasionally stalls for a few seconds (using swap) when I open a lot of larger programs at once. I thought it was partially because I run 64 bit when I really should use the 32 bit version. But I want the same version as I use on my Desktop, so I live with it.

If editing videos there is not enough RAM, otherwise your 2GB should be ok. 4GB used to be the current sweet spot, but with memory prices so low many new systems have a lot more.

```

Like this you mean Fred?
Godfree
ps tx for input re my orignal question: think i will grab me a bit extra after following advice offered above and lifting top of machine, removing a stick and taking it to nice man at shop to get exact RAM type

---

### Post by oldfred on 2012-06-28
It looks like you have two empty slots.

```
*-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 0
             serial: 821A2093umber
             slot: J6G1
             size: 1GiB
             width: 40968 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous [COLOR=Red][empty][/COLOR]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 1
             serial: Serial Number
             slot: J6G2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 4D332037385432383633445A532D43453620
             vendor: Samsung
             physical id: 2
             serial: 821A2073umber
             slot: J6H1
             size: 1GiB
             width: 41992 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [COLOR=Red][empty][/COLOR]
             product: Part Number Part Number Part Number
             vendor: 48spaces
             physical id: 3
             serial: Serial Number
             slot: J6H2
```

---

### Post by Yellow Pasque on 2012-06-29
You don't need to take out RAM or take it to a shop. It is DDR2-667 [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611+600006098+600006065&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=147&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611+600006098+600006065&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=147&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=)

You still haven't posted free -m output. Buying new RAM will be a waste of money unless you know it is lack of RAM slowing your system.

---

### Post by godfreezone on 2012-06-29
```

```> **Temüjin said:**
> You don't need to take out RAM or take it to a shop. It is DDR2-667 [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611+600006098+600006065&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=147&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007611+600006098+600006065&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=147&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=)

You still haven't posted free -m output. Buying new RAM will be a waste of money unless you know it is lack of RAM slowing your system.```

```

yes i did, but i'll do it again; thx for taking the time to follow it up but i have worked it out, without going to shop

```

```godfreysown@Godfreysown:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1777        226          0         86       1097
-/+ buffers/cache:        593       1410
Swap:         2036          0       2036```

```

---

### Post by oldfred on 2012-06-29
If you are not using swap you have enough memory for what you are running.

Linux caches recent tasks in RAM since you or system often go back and reuse them. It then frees older task if it needs RAM for something new and only uses swap when it runs out of RAM for current tasks. Or RAM normally shows a high usage. Use of swap says more RAM will help. You are not showing any swap usage currently.

---

### Post by godfreezone on 2012-06-29
Sweet. Okay, so, now I've got the guy who sold me computer coming over tuesday with 2x1gig sticks to double the ram to 4gig.
But it is so cheap that I think i'll get it anyhow and then have enough resources for the next 3 years or so.
An interesting and informative exercise Fred. 
Regs, 
G

> **oldfred said:**
> If you are not using swap you have enough memory for what you are running.

. You are not showing any swap usage currently.

---

### Post by oldfred on 2012-06-29
I agree on the extra RAM, since Linux is caching apps in RAM, more RAM is more cache so you should find system generally faster.

---

