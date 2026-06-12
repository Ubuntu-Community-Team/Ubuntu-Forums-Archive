---
title: "Can someone know whats a hard drive controller"
date: 2011-03-22
forum: Hardware
---

### Post by jao_madn on 2011-03-22
Hi

I would like to ask some clarification about a hard drive controller and its function.

I have an lshw and dmidecode resuly below this msg and maybe someone knows what the hard drive controller of this system..or does it include below.

lshw result:
    description: Notebook
    product: dynabook SS S20 12L/2
    vendor: TOSHIBA
    version: PPS2012L2G63KZ
    serial: Z5090443H
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=A4502F80-71C7-11DA-8020-B0EDA5090443
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$0000012f
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.60 (10/25/2005)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing vesa cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu:0 DISABLED
          description: CPU [empty]
          vendor: Intel Corporation
          physical id: 4
          slot: IC1050
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KiB
             capacity: 64KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 2MiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 1280MiB
        *-bank:0
             description: SDRAM Synchronous
             physical id: 0
             slot: System 0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MiB
             width: 64 bits
     *-cpu:1
          product: Intel(R) Pentium(R) M processor 1.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cff80000-cfffffff ioport:cff8(size=8) memory:b0000000-bfffffff memory:cff40000-cff7ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:24000000-2407ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:cfe00000-cfefffff
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth7
                version: 15
                serial: 00:0e:7b:4d:70:9f
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:41 memory:cfefc000-cfefffff ioport:be00(size=256)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:afe0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:af80(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:28c0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:af60(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:24080000-240803ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:cfd00000-cfdfffff ioport:20000000(size=67108864)
           *-network
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: wlan7
                version: 01
                serial: 00:11:f5:c9:c7:8d
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:cfdf0000-cfdfffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:21 memory:cfd00000-cfd00fff ioport:1000(size=256) ioport:1400(size=256) memory:20000000-23ffffff memory:28000000-2bffffff
           *-generic
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: b.4
                bus info: pci@0000:02:0b.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:23 memory:cfd01000-cfd010ff memory:cfd01100-cfd011ff memory:cfd01200-cfd012ff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:2000(size=256) ioport:2880(size=64) memory:24080400-240805ff memory:24080600-240806ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2800(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:af30(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3006GA
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BZ10
                serial: Y5PA1284T
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000934ce
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1509df41-cb6f-47f0-82fd-9478a0625cfc
                   size: 7269MiB
                   capacity: 7269MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-18 05:16:38 filesystem=ext4 lastmountpoint=/ï¿½ï¿½',cmï¿½xï¿½ï¿½ï¿½lYï¿½@ï¿½ï¿½ï¿½ïï¿½ï¿½l!ï¿½xï¿½ï¿½ï¿½0ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½cmï¿½ ï¿½Xï¿½ï¿½ï¿½yo!ï¿½ï¿½d modified=2011-03-07 17:25:59 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-22 06:04:50 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 376MiB
                   capacity: 376MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 376MiB
                      capabilities: nofs
     *-scsi
          physical id: 2
          bus info: usb@1:8
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 3824MiB (4009MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/2727-5847
                version: FAT32
                serial: 2727-5847
                size: 3823MiB
                capacity: 3823MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-battery
       description: Lithium Ion Battery
       product: 35P24R
       vendor: TOSHIBA
       physical id: 1
       version: 10/19/05
       serial: 0000002698
       slot: 1st Battery
       configuration: voltage=10.8V

DMIDECODE result:
# dmidecode 2.9
SMBIOS 2.3 present.
39 structures occupying 1190 bytes.
Table at 0x000EC000.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: TOSHIBA
    Version: Version 1.60
    Release Date: 10/25/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        VLB is supported
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer: TOSHIBA
    Product Name: dynabook SS S20 12L/2
    Version: PPS2012L2G63KZ
    Serial Number: Z5090443H
    UUID: A4502F80-71C7-11DA-8020-B0EDA5090443
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: TOSHIBA
    Product Name: Portable PC
    Version: Version A0
    Serial Number: $$0000012f

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: TOSHIBA
    Type: Notebook
    Lock: Not Present
    Version: Version 1.0
    Serial Number: 00000000
    Asset Tag: 0000000000
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
    Socket Designation: IC1050
    Type: Central Processor
    Family: Pentium M
    Manufacturer: Intel Corporation
    ID: D8 06 00 00 00 00 00 00
    Signature: Type 0, Family 6, Model 13, Stepping 8
    Flags: None
    Version:  
    Voltage: 1.0 V
    External Clock: 100 MHz
    Max Speed: 1200 MHz
    Current Speed: 1200 MHz
    Status: Unpopulated
    Upgrade: None
    L1 Cache Handle: 0x0012
    L2 Cache Handle: 0x0013
    L3 Cache Handle: Not Provided

Handle 0x0009, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: Other
    Current Interleave: Other
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        Other
        DIMM
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x000A
        0x000B
    Enabled Error Correcting Capabilities:
        None

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: Soldering
    Bank Connections: 0
    Current Speed: 5 ns
    Type: Other SDRAM
    Installed Size: 256 MB (Single-bank Connection)
    Enabled Size: 256 MB (Single-bank Connection)
    Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: SO-DIMM
    Bank Connections: 2
    Current Speed: 5 ns
    Type: Other DIMM SDRAM
    Installed Size: 256 MB (Single-bank Connection)
    Enabled Size: 256 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0012, DMI type 7, 19 bytes
Cache Information
    Socket Designation: CPU Internal
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: 1 ns
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0013, DMI type 7, 19 bytes
Cache Information
    Socket Designation: CPU Internal
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 2048 KB
    Maximum Size: 2048 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: 1 ns
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: EXTERNAL MONITOR PORT
    External Connector Type: DB-15 female
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: BUILT-IN MODEM PORT
    External Connector Type: RJ-11
    Port Type: Modem Port

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: BUILT-IN LAN PORT
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: INFRARED PORT
    External Connector Type: Infrared
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: USB PORT
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: USB PORT
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: HEADPHONE JACK
    External Connector Type: Mini Jack (headphones)
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: DOCKING INTERFACE PORT
    External Connector Type: Other
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator:  
    Internal Connector Type: None
    External Reference Designator: WIRELESS LAN
    External Connector Type: Other
    Port Type: Other

Handle 0x0037, DMI type 9, 13 bytes
System Slot Information
    Designation: PCMCIA0
    Type: 32-bit PC Card (PCMCIA)
    Current Usage: In Use
    Length: Other
    ID: Adapter 1, Socket 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PC Card-16 is supported
        Cardbus is supported
        Hot-plug devices are supported

Handle 0x0038, DMI type 9, 13 bytes
System Slot Information
    Designation: SD CARD
    Type: Other
    Current Usage: In Use
    Length: Other
    Characteristics:
        3.3 V is provided
        Hot-plug devices are supported

Handle 0x0058, DMI type 10, 16 bytes
On Board Device 1 Information
    Type: Other
    Status: Enabled
    Description: MODEM
On Board Device 2 Information
    Type: Other
    Status: Enabled
    Description: USB
On Board Device 3 Information
    Type: Video
    Status: Enabled
    Description: VIDEO
On Board Device 4 Information
    Type: Ethernet
    Status: Enabled
    Description: ETHERNET
On Board Device 5 Information
    Type: Sound
    Status: Enabled
    Description: SOUND
On Board Device 6 Information
    Type: Other
    Status: Enabled
    Description: WIRELESS LAN

Handle 0x0059, DMI type 11, 5 bytes
OEM Strings
    String 1: PPR20N-03404E,PPR20N-03404E111/S3A2222D003

Handle 0x0069, DMI type 12, 5 bytes
System Configuration Options
    Option 1: TOSHIBA

Handle 0x0080, DMI type 15, 23 bytes
System Event Log
    Area Length: 124 bytes
    Header Start Offset: 0x0000
    Data Start Offset: 0x0000
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0003
    Status: Valid, Not Full
    Change Token: 0x00000000
    Header Format: No Header
    Supported Log Type Descriptors: 0

Handle 0x0081, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 1280 MB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0082, DMI type 17, 23 bytes
Memory Device
    Array Handle: 0x0081
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 256 MB
    Form Factor: Other
    Set: Unknown
    Locator: System 0
    Bank Locator: CSA 0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown

Handle 0x0083, DMI type 17, 23 bytes
Memory Device
    Array Handle: 0x0081
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 256 MB
    Form Factor: SODIMM
    Set: Unknown
    Locator: DIMM 1
    Bank Locator: CSA 2 & 3
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown

Handle 0x0090, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000A03FF
    Range Size: 641 kB
    Physical Array Handle: 0x0081
    Partition Width: 0

Handle 0x0091, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000100000
    Ending Address: 0x0001F8003FF
    Range Size: 515073 kB
    Physical Array Handle: 0x0081
    Partition Width: 0

Handle 0x00A0, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000A03FF
    Range Size: 641 kB
    Physical Device Handle: 0x0082
    Memory Array Mapped Address Handle: 0x0090
    Partition Row Position: 1

Handle 0x00A1, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000100003FF
    Range Size: 262145 kB
    Physical Device Handle: 0x0082
    Memory Array Mapped Address Handle: 0x0091
    Partition Row Position: 1

Handle 0x00A2, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00010000000
    Ending Address: 0x000200003FF
    Range Size: 262145 kB
    Physical Device Handle: 0x0083
    Memory Array Mapped Address Handle: 0x0091
    Partition Row Position: 1

Handle 0x00B0, DMI type 21, 7 bytes
Built-in Pointing Device
    Type: Touch Pad
    Interface: PS/2
    Buttons: 2

Handle 0x00B1, DMI type 22, 26 bytes
Portable Battery
    Location: 1st Battery
    Manufacturer: TOSHIBA
    Manufacture Date: 10/19/05
    Serial Number: 0000002698
    Name: 35P24R
    Chemistry: Lithium Ion
    Design Capacity: 0 mWh
    Design Voltage: 10800 mV
    SBDS Version: Not Specified
    Maximum Error: Unknown
    OEM-specific Information: 0x00000000

Handle 0x00B7, DMI type 24, 5 bytes
Hardware Security
    Power-On Password Status: Disabled
    Keyboard Password Status: Disabled
    Administrator Password Status: Disabled
    Front Panel Reset Status: Disabled

Handle 0x00D0, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x00E0, DMI type 136, 6 bytes
OEM-specific Type
    Header and Data:
        88 06 E0 00 5A 5A

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

---

### Post by dandnsmith on 2011-03-22
That system looks as if it may have 2 HDDs:
1) description: ATA Disk
product: TOSHIBA MK3006GA
vendor: Toshiba
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: BZ10
serial: Y5PA1284T
size: 27GiB (30GB)

2) description: SCSI Disk
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sdb
size: 3824MiB (4009MB)

Possibly from that you can get the info you want.
The second looks so small - could it possibly be a special, like an SSD card?

The controller is:

description: IDE interface
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
logical name: scsi0

I'm not sure what exactly the controller does for you - a lot of the functionality got moved into the onboard electronics of the individual drive as the drives got more sophisticated

---

### Post by rmemm on 2011-03-22
My vote is:

description: IDE interface
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
logical name: scsi0
version: 03
width: 32 bits
clock: 33MHz
capabilities: ide bus_master emulated
configuration: driver=ata_piix latency=0
resources: irq:18 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:af30(size=16)
*-disk

Rob

---

### Post by grahammechanical on 2011-03-22
Here is a link if you want to understand further.

[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)

Regards.

---

