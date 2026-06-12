---
title: "atax softreset failed"
date: 2011-04-30
forum: Hardware
---

### Post by martijntje on 2011-04-30
I get this about two out of three times when trying to boot: 

atax: softreset failed

It happens with either ata1 or ata3 usually. When this happens, the HD light comes on and stays on for about a full two minutes. At some point it gives up and goes to a recovery console.

The other times it just boots.

What can I do? System configuration is as follows:

```
martijntje
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 870 Extreme3
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.60
          date: 09/14/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1090T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1090T Processor
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=6 enabledcores=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 667 MHz (1,5 ns)
             product: 996969000000000000
             vendor: Manufacturer02
             physical id: 2
             serial: 00000000
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM Synchronous 667 MHz (1,5 ns)
             product: 996969000000000000
             vendor: Manufacturer03
             physical id: 3
             serial: 00000000
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port B)
             vendor: ATI Technologies Inc
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fc000000-fe9fffff ioport:d4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF104 [GeForce GTX 460]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:19 memory:fc000000-fdffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:e800(size=128) memory:fe980000-fe9fffff
           *-multimedia
                description: Audio device
                product: GF104 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:fe97c000-fe97ffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port E)
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fbe00000-fbefffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fbefe000-fbefffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) ioport:d3f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: 00:25:22:8d:83:1e
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:c800(size=256) memory:d3fff000-d3ffffff memory:d3ff8000-d3ffbfff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:44 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fbdffc00-fbdfffff
           *-disk:0
                description: ATA Disk
                product: OCZ-VERTEX3
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 2.02
                serial: OCZ-0R6Z497295WPU446
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000da7b8
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 8d8ba9c6-cea5-4090-b066-cbbd94c3ad2c
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-29 19:05:59 filesystem=ext4 lastmountpoint=/ modified=2011-04-29 19:31:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered,discard mounted=2011-04-30 09:26:38 state=mounted
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 1AJ1
                serial: S246J9CB142141
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b30fb
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: fab5e09f-6d09-44c6-8963-dfb314129120
                   size: 1863GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-16 18:17:56 filesystem=ext4 lastmountpoint=/var modified=2011-04-30 09:26:38 mounted=2011-04-30 09:26:38 state=clean
           *-disk:2
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdc
                version: 1AJ1
                serial: S246J9CB142142
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007aa7f
              *-volume
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdc1
                   capacity: 931GiB
                   capabilities: primary multi
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfe000-fbdfefff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff800-fbdff8ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfd000-fbdfdfff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff400-fbdff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: BD RW BD-5300S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fbdf8000-fbdfbfff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfc000-fbdfcfff
        *-pci:4
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:fbf00000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:fbfff800-fbffffff ioport:d800(size=256)
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdf7000-fbdf7fff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff000-fbdff0ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
```

---

### Post by prshah on 2011-04-30
> **martijntje said:**
> 
atax: softreset failed

This usually indicates a hard disk problem (either logical or physical, eg bad sectors).

First, ensure the the ata devices referred to are not CDROM (eg, eject and remove any optical disks in your system).

Then, boot to the recovery terminal, and give the command ```
sudo touch /forcefsck
``` then reboot; it will trigger a disk check.

Logical errors (Eg lost clusters) should be fixed with the standard disk check. If you are still getting these messages, please run a check for bad sectors, and/or ensure that your power supply (SMPS) is powerful enough to handle all the devices you have.

Please post back with more details if you want particulars on how to do this.

---

### Post by martijntje on 2011-05-27
I'm pretty sure that this is *not* a problem with the disc. It is brand new, and the error does not occur on every boot.

There is no disc in my blu-ray drive and the power supply is more than capable of providing the necessary power.

---

