---
title: "Ubuntu won't read Micro SDHC in SD adapter."
date: 2012-03-31
forum: Hardware
---

### Post by Th3Blaze on 2012-03-31
The drive appears to be the problem as according to Disk Utility, the drive is unformatted, so the Micro SDHC card won't be read at all. When I attempt to format the drive, the error that appears is : ```
Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found
```

The output of lshw:
```






mary@Mercury:~$ sudo lshw
mercury                   
    description: Laptop
    product: Satellite C660 (*)
    vendor: TOSHIBA
    version: PSC0QE-04H00CEN
    serial: 4B116373K
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=laptop family=ABCDEFGHIJKLMNOPQRTUVWXYZ sku=* uuid=C8DE6856-5754-11E0-BD02-B870F454FFB8
  *-core
       description: Motherboard
       product: PWWAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 123456789AB
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: 1.60
          date: 03/14/11
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU        P6200  @ 2.13GHz
          vendor: Intel Corp.
          physical id: d
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: CPU
          size: 933MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm popcnt lahf_lm arat cpufreq
          configuration: cores=2 enabledcores=2 id=4 threads=2
        *-cache:0
             description: L3 cache
             physical id: e
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: f
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L2 cache
             physical id: 10
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 94304672
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: DIMM2
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
             resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:6050(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:d2605000-d260500f
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
             resources: irq:16 memory:d2608000-d26083ff
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
             resources: irq:43 memory:d2600000-d2603fff
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
             resources: irq:16 ioport:4000(size=8192) memory:d1e00000-d25fffff ioport:d0400000(size=9437184)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 05
                serial: b8:70:f4:54:ff:b8
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
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
             resources: irq:17 ioport:2000(size=8192) memory:d1500000-d1dfffff ioport:d0d00000(size=8388608)
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 01
                serial: 7c:4f:b5:5f:8e:e8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic-pae firmware=N/A ip=192.168.0.185 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:2000(size=256) memory:d1500000-d1503fff
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
             resources: irq:23 memory:d2607000-d26073ff
        *-pci:2
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
             logical name: scsi1
             logical name: scsi4
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:6048(size=8) ioport:605c(size=4) ioport:6040(size=8) ioport:6058(size=4) ioport:6020(size=32) memory:d2608800-d2608fff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK6465GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: GH10
                serial: 31QDD2UVB
                size: 596GiB (640GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00029ff5
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: adeff431-455a-4d83-8beb-7587b3509449
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2012-03-31 15:59:10 filesystem=ext3 modified=2012-03-31 16:25:50 mounted=2012-03-31 16:02:27 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 498GiB
                   capacity: 498GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 487GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT30N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TN08
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
             resources: memory:d2604000-d26040ff ioport:efa0(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d2606000-d2606fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@1:1.3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: Smart Battery
       vendor: TOSHIBA
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
       capacity: 10mWh
       configuration: voltage=0.0V

```


Output of df :
```
mary@Mercury:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6            502993192  24194032 453248568   6% /
udev                   1949828         4   1949824   1% /dev
tmpfs                   782736       924    781812   1% /run
none                      5120         0      5120   0% /run/lock
none                   1956836       184   1956652   1% /run/shm

```

Output of lsusb :
```
mary@Mercury:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 015: ID 05ac:129e Apple, Inc. iPod Touch 4.Gen

```

Output of fdisk:
```
mary@Mercury:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029ff5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *  1045463040  1250263039   102400000   83  Linux
/dev/sda2            2046  1045463039   522730497    5  Extended
/dev/sda5            2048    23437311    11717632   82  Linux swap / Solaris
/dev/sda6        23439360  1045463039   511011840   83  Linux

Partition table entries are not in disk order

```

All I know is that the device name is sdb , and i think that ```
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
``` is the (Micro SDHC to ) SD adapter.

Can you please share any knowledge you have in order to resolve the matter, much appreciated.

Thanks in Advance :)

---

