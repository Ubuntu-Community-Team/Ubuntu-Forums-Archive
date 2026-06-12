---
title: "Natty flickering screen on DV6"
date: 2011-06-20
forum: Hardware
---

### Post by rachel1.0 on 2011-06-20
Hi people. I've been using Ubuntu for quite a while now (and spreading it to my family and friends) and I've never had too many problems with it. I've been able to fix and workaround sound issues and drivers that made the whole OS crash.

Anyway, I've got a DV6 2138ca, which I've bought in sept 2010, so, I've had Ubuntu 10.04 and then 10.10 installed in it with no major problems. I took a while to upgrade to natty because I wanted a clean install and needed to back up some stuff and was kinda putting that off. Finally, last thursday (jun 16) I formatted and installed it with no problems.

But friday (17) I was playing Minecraft (with Sun Java VM) and had empathy and Firefox open too, when it just went insane, the screen started flickering showing only the wallpaper and then my windows. It wasn't frozen, because I could go to TTY1 and even kill processes, but the X was crazy. It happened two more times that day (all with Minecraft open, that's why I think it's relevant) and so far it hasn't happened again (though I didn't use it during the weekend).

Here's a video of the problem (or the TLDR version) [http://www.youtube.com/watch?v=iJ5t7R6QFA8](http://www.youtube.com/watch?v=iJ5t7R6QFA8).

Anyway, I'm at a loss, really don't want to downgrade back, though Maverick worked perfectly... If anyone has ideas...

Here's my lshw result:

```
rachel-laptop
    description: Notebook
    product: HP Pavilion dv6 Notebook PC (WA788UAR#ABA)
    vendor: Hewlett-Packard
    version: 049D210000241210000020000
    serial: 4CA0057V4P
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=WA788UAR#ABA uuid=434E4630-3035-3756-3450-C80AA9076614
  *-core
       description: Motherboard
       product: 3658
       vendor: Hewlett-Packard
       physical id: 0
       version: 32.25
       serial: 4CA0057V4P
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.1C
          date: 05/17/2010
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          slot: CPU
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=5 threads=4
        *-cache:0
             description: L3 cache
             physical id: 17
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 19
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 1a
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 5.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 5.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 5.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 5.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 5.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 5.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 5.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 5.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 5.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 5.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 5.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 5.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 5.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 5.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 5.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 5.10
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 18
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CH9
             vendor: Samsung
             physical id: 0
             serial: 67478F05
             slot: Bottom - Slot 1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CH9
             vendor: Samsung
             physical id: 1
             serial: 67478FB1
             slot: Bottom - Slot 2
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
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
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d6406100-d640610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d6405c00-d6405fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:d6400000-d6403fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:d5400000-d63fffff ioport:d0400000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: c4:17:fe:71:db:04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:d5400000-d5403fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:d4400000-d53fffff ioport:d1400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: c8:0a:a9:07:66:14
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:3000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:d3400000-d43fffff ioport:d2400000(size=16777216)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:d6405800-d6405bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:5048(size=8) ioport:505c(size=4) ioport:5040(size=8) ioport:5058(size=4) ioport:5020(size=32) memory:d6405000-d64057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS72505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PC4O
                serial: 100127PCK400VLGMPWUJ
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=373599ca
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /seven-swap
                   version: 3.1
                   serial: a4e4-0573
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-09-03 04:37:41 filesystem=ntfs label=Reservado pelo Sistema mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /seven
                   version: 3.1
                   serial: b0213b64-200d-424a-9e3a-247e41b48a4b
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-09-03 04:38:11 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 1cfdd48c-8760-406a-a7e4-a6e51fb9c1f6
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-16 20:35:26 filesystem=ext4 lastmountpoint=/ modified=2011-06-16 20:45:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-17 13:05:33 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 365GiB
                   capacity: 365GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /data/ntfs
                      capacity: 99GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /data/ext4
                      capacity: 263GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2141MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7586H
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KH03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6406000-d64060ff ioport:5000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:19 memory:d6404000-d6404fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: EV06047
       vendor: SDI-KTY
       physical id: 1
       slot: In the back
       capacity: 4400mWh
       configuration: voltage=10.8V
```

---

