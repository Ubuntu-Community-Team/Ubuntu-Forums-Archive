---
title: "cdrom drive not detected"
date: 2009-03-12
forum: Hardware
---

### Post by basilwatson on 2009-03-12
hi all 

I have just changed the mobo, to a intel dg5ec and it doesnt recognise the cdrom drive.

here are the outputs from lsw, etc

I cant dsee it in the bios either ,,( i will check again ..) 

anyway ,,,,,
s-desktop                 
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=52BA77B0-DB33-11DD-B23A-0013D4D9C9BF
  *-core
       description: Motherboard
       product: DG35EC
       vendor: Intel Corporation
       physical id: 0
       version: AAE29266-207
       serial: BTEC902000Y2
       slot: Base Board Chassis Location
s-desktop                 
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=52BA77B0-DB33-11DD-B23A-0013D4D9C9BF
  *-core
       description: Motherboard
       product: DG35EC
       vendor: Intel Corporation
       physical id: 0
       version: AAE29266-207
       serial: BTEC902000Y2
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: LGA 775
          size: 1596MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: ECG3510M.86A.0106.2008.0730.1746 (07/30/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x0000000000000000
             physical id: 0
             serial: 0x00000010
             slot: J1MY
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x0000000000000000
             physical id: 1
             serial: 0x00000010
             slot: J2MY
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 2
             serial: NO DIMM
             slot: J3MY
        *-bank:3
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J4MY
     *-pci
          description: Host bridge
          product: 82G35 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G35 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-network
             description: Ethernet interface
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth2
             version: 02
             serial: 00:1c:c0:af:ae:4d
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-0 ip=192.168.0.9 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: scsi4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress msi bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-disk:0
                   description: ATA Disk
                   product: ST380021A
                   vendor: Seagate
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sda
                   version: 3.19
                   serial: 3HV2RP22
                   size: 74GiB (80GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=2d082d07
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@4:0.0.0,1
                      logical name: /dev/sda1
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: fbac9c37-9990-4591-89f7-537e3bfe9898
                      size: 71GiB
                      capacity: 71GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-12-30 16:43:20 filesystem=ext3 modified=2009-03-13 00:07:48 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-12 20:41:37 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: scsi@4:0.0.0,2
                      logical name: /dev/sda2
                      size: 2949MiB
                      capacity: 2949MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sda5
                         capacity: 2949MiB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6L250R0
                   vendor: Maxtor
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/sdb
                   version: BAH4
                   serial: L59EX7ZH
                   size: 233GiB (251GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=0001adee
                 *-volume
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@4:0.1.0,1
                      logical name: /dev/sdb1
                      logical name: /media/disk
                      version: 1.0
                      serial: b7481e45-8795-4747-b58d-2dd5893a1182
                      size: 233GiB
                      capacity: 233GiB
                      capabilities: primary multi journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-09-11 12:55:54 filesystem=ext3 modified=2009-03-13 11:16:20 mount.fstype=ext3 mount.options=rw,nosuid,nodev,errors=continue,data=ordered mounted=2009-03-13 11:16:20 state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 5
                bus info: pci@0000:05:05.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
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
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
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
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
     *-scsi
          physical id: 1
          bus info: usb@7:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:c8:41:68:05:fa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

thanks in advance any ideas ?

Stephen

ps ubuntu 8.10

Just double checked , the CDrom is not being picked up in the BIOS ,  on optical drive detected .. Also the cdrom  is trying to spin up , then crashing , eject / open close working ok 

?????????????


Help...

---

### Post by basilwatson on 2009-03-13
bump ,,,is this a bug??  i really don't want to buy a sata drive if I can help it ,,,and I have tried 2 DVD drives I know work...

so its either bios , or ubuntu or combination 

Stephen

---

