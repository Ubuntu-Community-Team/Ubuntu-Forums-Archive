---
title: "Help with wireless &amp; taskbar problem (Ubuntu 10.10 on Acer 4820TG)"
date: 2011-06-20
forum: Hardware
---

### Post by ashzoomerintrack on 2011-06-20
Hi guys,
It feels great to be back on ubuntu. Was using kubuntu for 3 years but eventually came back home to gnome :)

I have installed Ubuntu 10.10 on my laptop and most of the stuff is working. Now there are 2 things which are not working:

1. Broadcom Wireless
When I was on kubuntu it was working out of the box by using keyboard Fn+F3. Same keys were also used to start bluetooth. Bluetooth is working but wireless is not.

2. I have an external AOC2243FWK display and whenever i connect display since boot time. The taskbar applets get wrong or non orderly positions on the other hand, if I boot without connecting monitor and then when I plug in monitor and configure display settings. Everything on taskbar is fine. Why is this weird behaviour with taskbar???

For the hardware problem, I am posting lspci, iwconfig & lshw for quick look

lspci
```
ashish@ashish-Aspire-4820TG:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev ff)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] (rev ff)
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

iwconfig
```
ashish@ashish-Aspire-4820TG:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.



```

lshw
```

ashish@ashish-Aspire-4820TG:~$ sudo lshw
ashish-aspire-4820tg      
    description: Notebook
    product: Aspire 4820TG
    vendor: Acer
    version: V1.19
    serial: LXPSE02338045154AF2500
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=ECAA16AD-5382-4E50-9FB6-60EB698FCC96
  *-core
       description: Motherboard
       product: ZQ1B
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: 045IZQMBQTF00190
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.19 (09/08/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: M471B2873FHS-CH9
             physical id: 0
             serial: 75067677
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 1
             serial: 00000000
             slot: DIMM1
             width: 8 bits
             clock: 1067MHz (0.9ns)
        *-bank:2
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: M471B5673FH0-CH9
             physical id: 2
             serial: 473DDC8D
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 3
             serial: 00000000
             slot: DIMM3
             width: 8 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 2a
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          slot: CPU
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 2b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 2d
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 2e
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 2c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0
             description: Unassigned class
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 1
             bus info: pci@0000:00:01.0
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: driver=pcieport latency=255 maxlatency=255 mingnt=255
             resources: irq:40 ioport:3000(size=4096) memory:dc400000-dc4fffff ioport:d0000000(size=134217728)
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4050(size=8)
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
             resources: memory:dc506100-dc50610f
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
             resources: irq:16 memory:dc505c00-dc505fff
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
             resources: irq:44 memory:dc500000-dc503fff
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
             resources: irq:41 ioport:2000(size=4096) memory:db400000-dc3fffff ioport:d8400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 60:eb:69:8f:cc:96
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:48 memory:db400000-db43ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:da400000-db3fffff ioport:d9400000(size=16777216)
           *-network UNCLAIMED
                description: Network controller
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:da400000-da403fff
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
             resources: irq:23 memory:dc505800-dc505bff
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
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:4048(size=8) ioport:405c(size=4) ioport:4040(size=8) ioport:4058(size=4) ioport:4020(size=32) memory:dc505000-dc5057ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX71A6093228
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=14d3a3f7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8e6a-9a91
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-12-31 04:45:15 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 960d77e2-6f01-a845-be3c-6745c47e578c
                   size: 130GiB
                   capacity: 130GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-12-31 04:45:29 filesystem=ntfs state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 5a952de5-6aed-43c0-a1b3-234cff47f7ea
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-19 13:16:20 filesystem=ext4 lastmountpoint=/&#65533;&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;O@U&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;}&#366;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-06-19 13:28:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-20 22:21:24 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 146GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 77GiB
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GU10N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AP04
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
             resources: memory:dc506000-dc5060ff ioport:4000(size=32)
        *-generic:1
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
             resources: irq:21 memory:dc504000-dc504fff
     *-generic:0
          description: Unassigned class
          product: Illegal Vendor ID
          vendor: Illegal Vendor ID
          physical id: 1
          bus info: pci@0000:01:00.0
          version: ff
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master vga_palette cap_list rom
          configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
          resources: irq:45 memory:d0000000-d7ffffff memory:dc400000-dc41ffff ioport:3000(size=256) memory:dc440000-dc45ffff
     *-generic:1
          description: Unassigned class
          product: Illegal Vendor ID
          vendor: Illegal Vendor ID
          physical id: 0.1
          bus info: pci@0000:01:00.1
          version: ff
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master vga_palette cap_list
          configuration: driver=HDA Intel latency=255 maxlatency=255 mingnt=255
          resources: irq:47 memory:dc420000-dc423fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 2
          bus info: usb@1:1.4
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: USB Storage FFF1
             vendor: ZTE
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             version: 2.31
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

```

From my plain observation 3 pieces of hardware are unrecognised :(

Need your help on this from you guys

---

### Post by ashzoomerintrack on 2011-06-21
UPDATE:1
I removed the proprietory Broadcom driver and reinstalled it. Voila the wireless adapter is working now but problem is bluetooth cannot be started now :)

P.S. In kubuntu 10.10 i used to press Fn+F3 once to start wireless network and Fn+F3 twice to start bluetooth. Its not working here

Please help to solve the taskbar problem

---

### Post by gshukla on 2011-07-02
Hi I have the same laptop and same problem. Internet would work nicely without any settings in Windows but it wont work in 10.04Lts. Tried many things simply no solution.

Please help I am new to ubuntu and tried whatever i could find on net.

---

### Post by ashzoomerintrack on 2011-07-15
Hi gshukla,
Please tell me who is your Internet Service provider and what kind of connection you use.. I can help you with INTERNET coz have been connected since Ubuntu 6.06LTS version... Cheers!

---

