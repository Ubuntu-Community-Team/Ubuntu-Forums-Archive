---
title: "Strange SATA drives and BIOS error - possibly a faulty MOBO?"
date: 2014-11-22
forum: Hardware
---

### Post by macbreak on 2014-11-22
Hey guys.

I am a well seasoned PC/Mac/Linux bloke, but I must confess, this has me totally stumped. Here is a document I type up, containing the symptom which I am experiencing with my Acer X3950 PC:

Attempted diagnosis of Acer X3950 PC errors, and symptoms thereof.


Hardware in this error report:

# Acer X3950 PC

# Toshiba **DT01ABA200** HDD

# Seagate **ST3000DM001** HDD

# WD **WD3200AVJS - 63B6A0 **HDD

# [SIZE=2][COLOR=#111111][FONT=Arial]XFX ATX 550 Power Supply - P1550SXXB9[/FONT][/COLOR][/SIZE]

First error is that my 2TB Toshiba drive (which has worked since June 2014) stopped spinning, and BIOS would not see it, except for "0MB". I had to boot Ubuntu live USB (with 2TB Toshiba connected to power but not data) and then re-connect data JUST before telling Ubuntu to boot. Once Ubuntu was part way through the boot process, Toshiba drive would suddenly spin up, and Ubuntu could see it.Once Ubuntu booted, "hdparm -I /dev/<toshiba_drive>" would only show corrupt model number and serial number.Performing a warm reboot back into Windows (IE: just a reboot, no shutdown) would allow Windows to now see the drive, and, when rebooting again and going into BIOS, it now appears and lists the full capacity and model number. If I now re-reboot back into Ubuntu from live USB, "hdparm -I /dev/<toshiba_drive>" would now show ALL info AND serial/model numbers, with no apparent faults.I have a Seagate drive which is brand new and has never been connected to the PC. It will not power up AT ALL, unless jumpers on the rear are shorted out, as shown in the photo of the jumpers (attached).I have a WD 320GB drive, which ALWAYS spins up and the PC ALWAYS powers up and boots Windows on this drive, unless the 2TB Toshiba *or* the 3TB Seagate are also attached (the Seagate has to be connected WITHOUT the jumpers shorted, in order for this fault condition to exhibit itself).PSU has been replaced with an XFX 550W model, same symptoms. Sata cable has been swapped, same symptoms.Very odd indeed. Also, last night, the Windows 10 installation which is installed on the WD 320GB (working) drive, kept complaining of drive corruption and that it needed to repair and reboot. Is this a faulty motherboard?

Also, none of the Num/Scroll/Caps lock LEDs will light up, when booted to an OS, when I press the correspnding key(s). They will toggle on/off as normal, when in BIOS mode. Is this indicative of a logic/controller failure of some kind? 


Please see below - here is my "sudo dmidecode" from May 2014 - please IGNORE the attached SATA devices, as these drives were upgraded to the ones I list in this post:

```
x3950    description: Desktop Computer
    product: Aspire X3950 (To Be Filled By O.E.M.)
    vendor: Acer
    serial: PTSE6E21530360154E3000
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=Acer Desktop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To Be Filled By O.E.M. uuid=1264E560-BB47-11DF-AFEC-90FBA6E68EE7
  *-core
       description: Motherboard
       product: Aspire X3950
       vendor: Acer
       physical id: 0
       serial: U02C103100908
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P01-A3
          date: 05/05/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 7GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: ACR256X64D3U1333C9
             vendor: Toshiba
             physical id: 0
             serial: 830E69BB
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4H1
             vendor: Micron
             physical id: 1
             serial: 31317526
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: ACR128X64D3U1333C9
             vendor: Toshiba
             physical id: 2
             serial: 5D0D696B
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4H1
             vendor: Micron
             physical id: 3
             serial: 3131756C
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:faf00000-fbffffff ioport:d6000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 430]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:dc00(size=128) memory:faf80000-faffffff
           *-multimedia
                description: Audio device
                product: GF108 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:faf7c000-faf7ffff
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:faefc000-faefc3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:faef8000-faefbfff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:e000(size=4096) memory:c0000000-c03fffff ioport:f9f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: 90:fb:a6:e6:8e:e7
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.74 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:e800(size=256) memory:f9fff000-f9ffffff memory:f9ff8000-f9ffbfff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:c0400000-c05fffff ioport:c0600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:c0800000-c09fffff ioport:c0a00000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:3000(size=4096) memory:c0c00000-c0dfffff ioport:c0e00000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:c1000000-c11fffff ioport:c1200000(size=2097152)
        *-pci:6
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:5000(size=4096) memory:c1400000-c15fffff ioport:c1600000(size=2097152)
        *-pci:7
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:6000(size=4096) memory:c1800000-c19fffff ioport:c1a00000(size=2097152)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:faef6000-faef63ff
        *-pci:8
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=32) memory:faef4000-faef47ff
           *-disk:0
                description: ATA Disk
                product: WDC WD5000AAKS-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAWF7698321
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=662c0165
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: eac05430-4826-9743-ba87-66020b65dbc6
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-12-10 03:21:18 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 047e1021-92eb-8144-bd94-b91d5fa61336
                   size: 329GiB
                   capacity: 329GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-12-10 03:21:33 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 130GiB
                   capacity: 130GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 18GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 111GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 73402c77-3d64-49d7-b118-d46df118c4ce
                   size: 6GiB
                   capacity: 6GiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: WDC WD10EADS-00M
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAV5M972195
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=728cd0fc
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: fed5-b850
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-05-28 02:37:41 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 52a604fe-5158-b54c-a86c-14c41cdde621
                   size: 244GiB
                   capacity: 244GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-28 02:37:54 filesystem=ntfs state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   version: 3.1
                   serial: 9c2c7bac-2f0d-2b41-83c0-7d1f8a5d1fb5
                   size: 687GiB
                   capacity: 687GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-28 02:38:07 filesystem=ntfs state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:faeff800-faeff8ff ioport:400(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@2:1.2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             size: 1912MiB (2004MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/983A-56F1
                version: FAT16
                serial: 983a-56f1
                size: 1910MiB
                capacity: 1910MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@2:1.4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdd
             size: 1920MiB (2013MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0001af87
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/2GBSD
                version: FAT32
                serial: c8f2-0c49
                size: 1917MiB
                capacity: 1918MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@2:1.5
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdf
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
# dmidecode 2.9
SMBIOS 2.6 present.
45 structures occupying 1942 bytes.
Table at 0x0009F400.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: P01-A3
    Release Date: 05/05/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.15


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Acer
    Product Name: Aspire X3950
    Version:         
    Serial Number: PTSE6E21530360154E3000
    UUID: 1264E560-BB47-11DF-AFEC-90FBA6E68EE7
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: Acer Desktop


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Acer
    Product Name: Aspire X3950
    Version:         
    Serial Number: U02C103100908
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0


Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Acer
    Type: Desktop
    Lock: Not Present
    Version:         
    Serial Number:                       
    Asset Tag:                       
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0


Handle 0x0004, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel            
    ID: 55 06 02 00 FF FB EB BF
    Version: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz     
    Voltage: 1.1 V
    External Clock: 133 MHz
    Max Speed: 3200 MHz
    Current Speed: 3200 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 2
    Core Enabled: 2
    Thread Count: 4
    Characteristics:
        64-bit capable


Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 128 KB
    Maximum Size: 128 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Instruction
    Associativity: 4-way Set-associative


Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative


Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 4096 KB
    Maximum Size: 4096 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative


Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 8192 MB
    Maximum Total Memory Size: 32768 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 4
        0x0009
        0x000A
        0x000B
        0x000C
    Enabled Error Correcting Capabilities:
        None


Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK


Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 2 3
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK


Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM2
    Bank Connections: 4 5
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Single-bank Connection)
    Enabled Size: 1024 MB (Single-bank Connection)
    Error Status: OK


Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM3
    Bank Connections: 6 7
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK


Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE1
    Type: x16 <OUT OF SPEC>
    Current Usage: In Use
    Length: Long
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE2
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Onboard Realtek HD Audio


Handle 0x0010, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Onboard Realtek GbE Lan


Handle 0x0011, DMI type 11, 5 bytes
OEM Strings
    String 1: Intel H57


Handle 0x0012, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: Single-bit ECC
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4


Handle 0x0013, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001BFFFFFFF
    Range Size: 7 GB
    Physical Array Handle: 0x0012
    Partition Width: 0


Handle 0x0014, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0012
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: 11
    Locator: DIMM0
    Bank Locator: BANK0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Toshiba       
    Serial Number: 830E69BB
    Asset Tag: 001031      
    Part Number: ACR256X64D3U1333C9


Handle 0x0015, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0014
    Memory Array Mapped Address Handle: 0x0013
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x0016, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0012
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: 11
    Locator: DIMM1
    Bank Locator: BANK1
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Micron        
    Serial Number: 31317526
    Asset Tag: 001117      
    Part Number: 8JTF25664AZ-1G4H1 


Handle 0x0017, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0016
    Memory Array Mapped Address Handle: 0x0013
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x0018, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0012
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 10
    Locator: DIMM2
    Bank Locator: BANK2
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Toshiba       
    Serial Number: 5D0D696B
    Asset Tag: 001031      
    Part Number: ACR128X64D3U1333C9


Handle 0x0019, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00100000000
    Ending Address: 0x0013FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0018
    Memory Array Mapped Address Handle: 0x0013
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x001A, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0012
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: 11
    Locator: DIMM3
    Bank Locator: BANK3
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Micron        
    Serial Number: 3131756C
    Asset Tag: 001117      
    Part Number: 8JTF25664AZ-1G4H1 


Handle 0x001B, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00140000000
    Ending Address: 0x001BFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x001A
    Memory Array Mapped Address Handle: 0x0013
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x001C, DMI type 24, 5 bytes
Hardware Security
    Power-On Password Status: Disabled
    Keyboard Password Status: Disabled
    Administrator Password Status: Disabled
    Front Panel Reset Status: Disabled


Handle 0x001D, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected


Handle 0x001E, DMI type 34, 11 bytes
Management Device
    Description: LM78-1
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port


Handle 0x001F, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: Unknown
    Status: Unknown
    Maximum Value: Unknown
    Minimum Value Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown


Handle 0x0020, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6


Handle 0x0021, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x001E
    Component Handle: 0x001E
    Threshold Handle: 0x001F


Handle 0x0022, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x001F
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating


Handle 0x0023, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6


Handle 0x0024, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x001E
    Component Handle: 0x0021
    Threshold Handle: 0x0022


Handle 0x0025, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x001F
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating


Handle 0x0026, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6


Handle 0x0027, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x001E
    Component Handle: 0x0024
    Threshold Handle: 0x0025


Handle 0x0028, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.
    Max Power Capacity: Unknown
    Status: Not Present
    Type: <OUT OF SPEC>
    Input Voltage Range Switching: <OUT OF SPEC>
    Plugged: Yes
    Hot Replaceable: No
    Cooling Device Handle: 0x0022


Handle 0x0029, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 29 00 01 87 00 FF FF FF FF
    Strings:
        Onboard Realtek HD Audio


Handle 0x002A, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 2A 00 01 85 00 FF FF FF FF
    Strings:
        Onboard Realtek GbE Lan


Handle 0x002B, DMI type 129, 8 bytes
OEM-specific Type
    Header and Data:
        81 08 2B 00 01 01 02 01
    Strings:
        Intel_ASF
        Intel_ASF_001


Handle 0x002C, DMI type 127, 4 bytes
End Of Table


Bus 002 Device 007: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 006: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 005: ID 0420:1307 Chips and Technologies Celly SIM Card Reader
Bus 002 Device 004: ID 05dc:a740 Lexar Media, Inc. 
Bus 002 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```





Here are photos of the three drives in question - the Toshiba is 6 months old, and the Seagate is brand new. The older, WD drive, is from and old DVR and works perfectly with no errors:

[URL="https://www.flickr.com/photos/22008695@N03/sets/72157649004076769/"]https://www.flickr.com/photos/22008695@N03/sets/72157649004076769/
[/URL]
Thank you so much

? No one ?

I thought this was your area, folks - come on, you're meant to be experts on PC hardware... :)

---

### Post by oldfred on 2014-11-24
It seems like your Toshiba drive is/has totally failed. If BIOS cannot see it, then no operating system can use it or attempt to read it.
If you have not fully backed up data, and do get it running, be sure all data is backed up.
And see if Smart Control shows anything. You can directly use Smart Control in Disks utility. Click on the advanced options tiny icon in upper right.

I did not even know SATA drives had any jumpers, have not paid attention, nor needed to use them.

---

### Post by macbreak on 2014-11-24
> **oldfred said:**
> It seems like your Toshiba drive is/has totally failed. If BIOS cannot see it, then no operating system can use it or attempt to read it.
If you have not fully backed up data, and do get it running, be sure all data is backed up.
And see if Smart Control shows anything. You can directly use Smart Control in Disks utility. Click on the advanced options tiny icon in upper right.

I did not even know SATA drives had any jumpers, have not paid attention, nor needed to use them.


I appreciate the fact you've replied, but you've basically given me a very vague, generic reply. I am also more than aware of the need to backup - the drive in question (Tosh) has been totally removed from the system, so my data is safe for now.

Here's what has been checked:

# Everything (yes, including SMART)

# Everything (yes, **again**... and again)


~ Yes, ***some ***SATA drives have jumpers - they are used for speed capping and/or serial port maintenance of the firmware (in some drives).

~ If you read my post again, thoroughly, you will see that I've mentioned the method by which the Toshiba functions normally again, therefore I AM able to access it. You will also be able to surmise, from this, that it would be VERY unlikely that the Toshiba drive is the cause of these problems, since I am attaching a brand new Seagate 3TB drive to the PC, and it also does not spin up or access, unless the jumper (in the photo - you did look at it, right?) is connected.


My problems have been described in **very** specific detail. With respect, and I thank you for replying, your answer could apply to ANYONE with ANY manner of hard disk fault. I do not feel your reply pertains to my specific situation, nor do I think it is - in any way - the right answer, but thanks anyhow :)


So... anyone else have an idea? Thank you, folks.

---

### Post by weatherman2 on 2014-11-24
Your post is a little dense.  You might try boiling it down a little so folks can drill in easier.

But bottom line: try the drives on different hardware - different motherboard, SATA enclosure, etc.  If the drives work perfectly on other hardware, you know the drives are fine; if the drives still don't work on other hardware you know the motherboard is probably not the issue.

---

### Post by oldfred on 2014-11-24
So the real issue is just the new 3TB drive?

Post this with 3TB plugged in. I assume BIOS does see it correctly?
Some old BIOS do not support large drives, or need BIOS updates to work with them.
Some vendors add proprietary bits to make a 3TB drive work with XP as XP does not support large drives nor work with gpt.

If you can mount 3TB drive post these:
sudo parted -l

For whatever drive is the 3TB drive, example below just uses sdb. If you have not installed gdisk install it first.
 sudo apt-get install gdisk
sudo gdisk -l /dev/sdb

---

### Post by macbreak on 2014-11-24
> **oldfred said:**
> So the real issue is just the new 3TB drive?



Nope, the real **issues **(plural) are precisely what I have documented in the initial post. It all started when my 2TB Toshiba wasn't spinning up. A friend then kindly gave me a brand new Seagate 3TB, which doesn't spin up even when ONLY connected to power, with the SATA disconnected... but **WILL **spin up when the aforementioned jumper position (seen here as [COLOR=#ff0000]**RED**[/COLOR]) is shorted, and will present itself as "807GB" in BIOS, but as 3TB in Windows/Ubuntu... but the jumper position isn't even a valid one - I accidentally put the jumper in the [COLOR=#ff0000]**RED **[/COLOR][COLOR=#000000]position[/COLOR]:

[IMG]https://farm8.staticflickr.com/7481/15666432370_a824f4eb80_b.jpg[/IMG]



Here's Seagate's jumper config illustration (NOTE - theirs is upside down, in relation to mine):

[IMG]http://support.seagate.com/kbimg/3178-1.gif[/IMG]


Also, as I've mentioned in the OP, Num/Scroll/Caps lock ***functions ***will work/toggle, but their indicator LEDs on two different PS/2 keyboards WILL NOT LIGHT, unless in BIOS mode, which is leading me to suspect something more than hard drives to blame for these multiple issues. It would seem a little too much of a coincidence for TWO hard drives not to work, when one of them (the Seagate 3TB) is brand spanking new.


There is no "boiling down" of these issues; I have ALL these issues and symptoms, and they ALL need diagnosing, in detail, in turn, otherwise we are just using guess work, or, worse, clutching at straws.


_Please take note, and pay very very close attention to the fact that I have mentioned the jumper setting which allows the Seagate drive to spin up and become seen by Win and Lin. To discount this very pertinent point, is entirely side-stepping a line of enquiry which may be half the solution. Yes, it's an undocumented jumper position as far as I can see, but please - do not skim over that point - the fact that the drive is visible WHEN it's shorted in the RED position, and the fact that the Toshiba drive IS accessible as documented in my initial post, using the method I described, leads me to the thoughts that the drives themselves are possibly NOT the cause of these strange errors_

Many thanks, again :)

---

### Post by oldfred on 2014-11-24
Please attach screenshots/photos not post in line.
You can easily attach with the paperclip icon in the advanced editor.
       [http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I would expect you may have to contact Seagate for what that setting may do. It may not be used offically, but perhaps they use it for some tests?

If BIOS is not seeing correctly that is not good. Is BIOS most current version from vendor?

---

### Post by macbreak on 2014-11-24
> **oldfred said:**
> Please attach screenshots/photos not post in line.
You can easily attach with the paperclip icon in the advanced editor.
       [http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I would expect you may have to contact Seagate for what that setting may do. It may not be used offically, but perhaps they use it for some tests?

If BIOS is not seeing correctly that is not good. Is BIOS most current version from vendor?


I am a professional photographer, and I use a fast mobile app to upload photos and screenshots to Flickr. I comment on forums using a laptop, connected standard ADSL with VERY slow upload, and so re-uploading photos which were taken/uploaded direct to Flickr albums via fast 3G, is not an option for me; I'll provide Flickr JPEG *links* next time, as I did in the first post.  I have no idea what Seagate deem this position to do, and I can't even entertain the tedium of a support call to them, to find out.

Yes, the latest BIOS for my 4 year old PC is May 2010. However, my 2TB Toshiba was working fine for 6 months... so explain that to me...

[ATTACH=CONFIG]258184[/ATTACH][ATTACH=CONFIG]258185[/ATTACH]

Look what I just found... HAS to help (my firmware is currently CC27) updating... :)

It appears that the Seagate drive had "PUIS" (Power Up In Standby) enabled from the factory, which means that the drive wouldn't spin up unless a specific command ([COLOR=#ff0000]**** I think this is the command**[/COLOR]) was seen on the sata bus.

I used this tool to check PUIS status, and then disabled it, and now the drive spins up first time, every time:

[http://www.hdat2.com](http://www.hdat2.com)


My investigations continue...


[COLOR=#ff0000][B]** "[FONT=arial]SET_FEATURES [/FONT][FONT=arial][B]required to spinup after power up"

More info here--- > [/B][/FONT][/B][/COLOR]http://lime-technology.com/forum/index.php?topic=2013.0

---

