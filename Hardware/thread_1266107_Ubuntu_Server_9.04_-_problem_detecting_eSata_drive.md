---
title: "Ubuntu Server 9.04 - problem detecting eSata drive in Thecus raid enclosure"
date: 2009-09-14
forum: Hardware
---

### Post by duhd on 2009-09-14
I have last week purchased new HW for my home-server. 1st is a Zotac mainboard with an Intel Atom CPU on it. Board was chosen because it has eSata port on it. I have also purchased a Thecus N2050 enclosure that has a Silicon Image 4723 Steel Vine RAID-Controller onboard supporting Raid0 and 1. 

When i connect the Thecus containing two SATA drives (500 GB drives) they do not show up in fdisk. After checking dmesg i can see that kernel reports failed to identify (among others)

I have researched kernel-trap and ATA mailing lists but have not enough knowledge to understand the specifics on the error. Suggestions have been made to replace cable (done), use different startup paramaters to boot (done) as well as checking newer kernel versions (done)

I have searched all forums and i am completely lost. I have tried different boot-params, vanilla kernel (2.6.31) and have now reverted back to Ubuntu Server 9.04 with 2.6.28-15 kernel on it.

Any help would be highly appreciated.

dmesg:
```

[  905.750155] ata3: exception Emask 0x10 SAct 0x0 SErr 0x4150000 action 0xe frozen
[  905.750193] ata3: irq_stat 0x00000040, connection status changed
[  905.750217] ata3: SError: { PHYRdyChg CommWake Dispar DevExch }
[  905.750245] ata3: hard resetting link
[  915.800023] ata3: softreset failed (device not ready)
[  915.800072] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  915.800078] ata3: link online but device misclassified, retrying
[  915.800084] ata3: hard resetting link
[  916.730034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  916.730082] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  921.730026] ata3: hard resetting link
[  922.260034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  922.260083] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  922.260092] ata3: limiting SATA link speed to 1.5 Gbps
[  927.260030] ata3: hard resetting link
[  927.790028] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  927.790075] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  932.790025] ata3: hard resetting link
[  933.320029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  933.320052] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  933.320079] ata3: irq_stat 0x08000000, interface fatal error
[  933.320106] ata3: hard resetting link
[  934.250026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  934.250068] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  939.250026] ata3: hard resetting link
[  939.780026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  939.780068] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  939.780074] ata3: limiting SATA link speed to 1.5 Gbps
[  944.780025] ata3: hard resetting link
[  945.310029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  945.310069] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  950.310027] ata3: hard resetting link
[  950.840027] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  950.840048] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t3
[  950.840076] ata3: irq_stat 0x08000000, interface fatal error
[  950.840102] ata3: EH complete

```

lspci:
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)

```

lshw:
```
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: To be filled by O.E.M.
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080015 (05/08/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1600MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
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
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
             product: CM2X1024-6400
             vendor: Corsair
             physical id: 0
             serial: 20202020
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 2048MHz (0.5ns)
        *-bank:1
             description: [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
             product: CM2X1024-6400
             vendor: Corsair
             physical id: 2
             serial: 20202020
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 2048MHz (0.5ns)
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:01:2e:27:3c:19
             size: 1GB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.10 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
        *-ide
             description: IDE interface
             product: MCP79 SATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi3
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
           *-disk
                description: ATA Disk
                product: ST3320620AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RV012NT
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e29c5
              *-volume:0
                   description: Linux LVM Physical Volume partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   serial: naJAh6-LApQ-cBid-6PuB-RyJJ-0jzs-c46Pyq
                   size: 297GiB
                   capacity: 297GiB
                   capabilities: primary bootable multi lvm2
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 243MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver

```

---

### Post by duhd on 2009-09-15
*bump*

---

### Post by duhd on 2009-09-19
bump again.
Have not found anything that can help me. Is there anyone that has insight into these types of problems

rgds,
DuhD

---

### Post by duhd on 2009-09-27
*bump*

Is there anyone that has had a similar problem?? 

rgds
duhd

---

### Post by sammiam on 2010-04-07
I purchased a Zotac GeForce 9300-ITX-WIFI board and have the same problem.. my internal sata is set up as fake raid, and works just fine.  When booting, the BIOS sees only 1 of my esata drives (I have an enclosure that splits the drive into 1 raid0 and 1 raid 1 drive). however, UBUNTU 9.10 does not see the esata drives.

---

