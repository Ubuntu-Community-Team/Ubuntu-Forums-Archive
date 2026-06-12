---
title: "Finding the temperatures of"
date: 2011-10-28
forum: Hardware
---

### Post by Lars Noodén on 2011-10-28
What specific hardware components do these sensors map to?  

$ sensors
nouveau-pci-0200
Adapter: PCI adapter
temp1: +81.0°C (high = +100.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Master : 1519 RPM (min = 1500 RPM)
TC0D: +50.5°C
TC0H: +50.0°C
TC0P: +49.8°C
TH0P: +52.8°C
TN0D: +80.5°C
TN0P: +64.5°C
TW0P: +62.8°C
Tm0P: +128.0°C

---

### Post by Lars Noodén on 2011-10-31
Bump.

Then man page for [sensors](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sensors.1.html) does not provide any clue.

---

### Post by trundlenut on 2011-10-31
What hardware do you have?

---

### Post by Lars Noodén on 2011-10-31
> **trundlenut said:**
> What hardware do you have?

MacBookPro8,2
Macmini3,1

---

### Post by trundlenut on 2011-10-31
What does "sudo lspci" and "sudo lshw" output if you run the two commands in a terminal?

---

### Post by Lars Noodén on 2011-10-31
$ cat /tmp/lshw.txt 
xubuntu
    description: Lunch Box Computer
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=lunchbox family=Macmini sku=System SKU# uuid=978369DC-54FA-F24C-82C8-B1B5307A6A7F
  *-core
       description: Motherboard
       product: Mac-F22C86C8
       vendor: Apple Inc.
       physical id: 0
       serial: Base Board Serial#
       slot: Part Component
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 2261MHz
          capacity: 2261MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-cache
             description: L1 cache
             physical id: 2
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
     *-cache:0
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 3
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1596MHz
          capacity: 1596MHz
          clock: 266MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-cache
             description: L1 cache
             physical id: 5
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-cache:1
          description: L1 cache
          physical id: 4
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 6
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             vendor: Samsung
             physical id: 0
             serial: 0x655E4E32
             slot: DIMM0
             size: 2GiB
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             vendor: Samsung
             physical id: 1
             serial: 0x655E4E34
             slot: DIMM0
             size: 2GiB
             clock: 1067MHz (0.9ns)
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: e
          version: MM31.88Z.00AD.B00.0907171535
          date: 07/17/09
          size: 1MiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
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
             version: b3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:2000(size=256)
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
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:15 ioport:2180(size=64) ioport:2140(size=64) ioport:2100(size=64)
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
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
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
             resources: memory:d3400000-d347ffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:18 memory:d3488000-d3488fff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:d3489200-d34892ff
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:17 memory:d3487000-d3487fff
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:19 memory:d3489100-d34891ff
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
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:22 memory:d3480000-d3483fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d3300000-d33fffff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 60:fb:42:f5:06:2a
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.42 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:44 memory:d3486000-d3486fff ioport:21e0(size=8) memory:d3489000-d34890ff memory:d3489300-d348930f
        *-ide
             description: IDE interface
             product: MCP79 SATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi0
             logical name: scsi1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:43 ioport:21d8(size=8) ioport:21ec(size=4) ioport:21d0(size=8) ioport:21e8(size=4) ioport:21c0(size=16) memory:d3484000-d3485fff
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2160B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0081
                serial: K67HTA1286KH
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0 UNCLAIMED
                   description: EFI GPT partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   capacity: 200MiB
                   capabilities: primary nofs
              *-volume:1
                   description: Darwin/OS X HFS+ partition
                   vendor: Mac OS X (journaled)
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 4
                   serial: e465335c-9fc6-d3ab-0000-0000000b6000
                   size: 22GiB
                   capacity: 22GiB
                   capabilities: primary journaled bootable osx hfsplus initialized
                   configuration: boot=osx checked=2011-09-24 17:26:50 created=2011-09-24 07:26:50 filesystem=hfsplus lastmountedby=HFSJ modified=2011-10-31 14:39:23 state=clean
              *-volume:2
                   description: Darwin/OS X boot partition
                   vendor: Mac OS X (journaled)
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 4
                   serial: 45390906-da86-50b5-0000-000000005000
                   size: 619MiB
                   capacity: 619MiB
                   capabilities: primary boot nofs journaled bootable osx hfsplus initialized
                   configuration: boot=osx checked=2011-09-24 17:51:06 created=2011-09-24 07:51:06 filesystem=hfsplus lastmountedby=HFSJ modified=2011-09-24 17:51:22 state=clean
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /
                   version: 1.0
                   serial: 2b440b21-ba15-4180-b3f6-8af8b0322921
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-26 14:26:11 filesystem=ext4 lastmountpoint=/ modified=2011-10-05 18:09:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-10-31 14:40:03 state=mounted
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVRTS08
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: Q81F
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi normal_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:d2000000-d30fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: C79 [GeForce 9400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:23 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:1000(size=128) memory:d3000000-d301ffff
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:d3200000-d32fffff
           *-network
                description: Network controller
                product: BCM4321 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 05
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:23 memory:d3200000-d3203fff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:d3100000-d31fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW643 PCI Express1394b Controller (PHY/Link)
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 07
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:42 memory:d3100000-d3100fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:b0:f8:d9:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by Lars Noodén on 2011-10-31
$ cat /tmp/lspci.txt 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)

---

### Post by trundlenut on 2011-10-31
So you have a Nvidia MCP79 chipset on your mobo and GeForce 9400M video chip.  The mobo is a Mac-F22C86C8.  Unfortunately a quick spot of googling does not reveal anything helpful about this combination.

---

