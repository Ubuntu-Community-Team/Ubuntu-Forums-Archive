---
title: "DS-8D3SH CD/DVD Burner"
date: 2013-06-15
forum: Hardware
---

### Post by fvisconti on 2013-06-15
This may be a continuation of [http://ubuntuforums.org/archive/index.php/t-1916289.html](http://ubuntuforums.org/archive/index.php/t-1916289.html).

I have a less than 1 year old Dell Latitude laptop with teh PLDS DS-8D3SH CD/DVD writer.  I have been burning CD's and DVD's without a problem in windows but when I installed Ubuntu, It only sees it as a CD-ROM.  


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)09:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)09:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)09:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)stratfordv-latitude-e5520     description: Laptop    product: Latitude E5520 ()    vendor: Winbond Electronics    version: 01    serial: H6QC4S1    width: 64 bits    capabilities: smbios-2.6 dmi-2.6 vsyscall32    configuration: boot=normal chassis=laptop uuid=44454C4C-3600-1051-8043-C8C04F345331  *-core       description: Motherboard       product: 03PH4G       vendor: Winbond Electronics       physical id: 0       version: A01       serial: /H6QC4S1/CN7590023301CR/     *-firmware          description: BIOS          vendor: Winbond Electronics          physical id: 0          version: A12          date: 03/10/2013          size: 64KiB          capacity: 1984KiB          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi biosbootspecification     *-cpu          description: CPU          product: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz          vendor: Intel Corp.          physical id: 4          bus info: cpu@0          version: Intel(R) Core(TM) i5-2520M CPU @ 2.50GH          serial: To Be Filled By O.E.M.          slot: CPU 1          size: 800MHz          capacity: 4GHz          width: 64 bits          clock: 100MHz          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq          configuration: cores=2 enabledcores=2 threads=4        *-cache:0             description: L1 cache             physical id: 5             slot: L1-Cache             size: 32KiB             capacity: 32KiB             capabilities: internal write-back unified        *-cache:1             description: L2 cache             physical id: 6             slot: L2-Cache             size: 256KiB             capacity: 256KiB             capabilities: internal varies unified        *-cache:2             description: L3 cache             physical id: 7             slot: L3-Cache             size: 3MiB             capacity: 3MiB             capabilities: internal varies unified     *-memory          description: System Memory          physical id: 28          slot: System board or motherboard          size: 4GiB        *-bank:0             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)             product: 8JTF25664HZ-1G4M1             vendor: Micron             physical id: 0             serial: E85BFFC2             slot: ChannelA-DIMM0             size: 2GiB             width: 64 bits             clock: 1333MHz (0.8ns)        *-bank:1             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)             product: 8JTF25664HZ-1G4M1             vendor: Micron             physical id: 1             serial: E85BFFC3             slot: ChannelB-DIMM0             size: 2GiB             width: 64 bits             clock: 1333MHz (0.8ns)     *-pci          description: Host bridge          product: 2nd Generation Core Processor Family DRAM Controller          vendor: Intel Corporation          physical id: 100          bus info: pci@0000:00:00.0          version: 09          width: 32 bits          clock: 33MHz          configuration: driver=agpgart-intel          resources: irq:0        *-display             description: VGA compatible controller             product: 2nd Generation Core Processor Family Integrated Graphics Controller             vendor: Intel Corporation             physical id: 2             bus info: pci@0000:00:02.0             version: 09             width: 64 bits             clock: 33MHz             capabilities: msi pm vga_controller bus_master cap_list rom             configuration: driver=i915 latency=0             resources: irq:43 memory:e1c00000-e1ffffff memory:d0000000-dfffffff ioport:7000(size=64)        *-communication             description: Communication controller             product: 6 Series/C200 Series Chipset Family MEI Controller #1             vendor: Intel Corporation             physical id: 16             bus info: pci@0000:00:16.0             version: 04             width: 64 bits             clock: 33MHz             capabilities: pm msi bus_master cap_list             configuration: driver=mei latency=0             resources: irq:44 memory:e3d80000-e3d8000f        *-usb:0             description: USB controller             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2             vendor: Intel Corporation             physical id: 1a             bus info: pci@0000:00:1a.0             version: 04             width: 32 bits             clock: 33MHz             capabilities: pm debug ehci bus_master cap_list             configuration: driver=ehci_hcd latency=0             resources: irq:16 memory:e3d50000-e3d503ff        *-multimedia             description: Audio device             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller             vendor: Intel Corporation             physical id: 1b             bus info: pci@0000:00:1b.0             version: 04             width: 64 bits             clock: 33MHz             capabilities: pm msi pciexpress bus_master cap_list             configuration: driver=snd_hda_intel latency=0             resources: irq:45 memory:e3d40000-e3d43fff        *-pci:0             description: PCI bridge             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1             vendor: Intel Corporation             physical id: 1c             bus info: pci@0000:00:1c.0             version: b4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list             configuration: driver=pcieport             resources: irq:16        *-pci:1             description: PCI bridge             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2             vendor: Intel Corporation             physical id: 1c.1             bus info: pci@0000:00:1c.1             version: b4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list             configuration: driver=pcieport             resources: irq:17 memory:e3c00000-e3cfffff           *-network                description: Wireless interface                product: BCM4313 802.11b/g/n Wireless LAN Controller                vendor: Broadcom Corporation                physical id: 0                bus info: pci@0000:02:00.0                logical name: eth1                version: 01                serial: 9c:b7:0d:95:03:ab                width: 64 bits                clock: 33MHz                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=10.0.0.12 latency=0 multicast=yes wireless=IEEE 802.11abg                resources: irq:17 memory:e3c00000-e3c03fff        *-pci:2             description: PCI bridge             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3             vendor: Intel Corporation             physical id: 1c.2             bus info: pci@0000:00:1c.2             version: b4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list             configuration: driver=pcieport             resources: irq:18 ioport:6000(size=4096) memory:e3100000-e3afffff ioport:e1100000(size=10485760)        *-pci:3             description: PCI bridge             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6             vendor: Intel Corporation             physical id: 1c.5             bus info: pci@0000:00:1c.5             version: b4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list             configuration: driver=pcieport             resources: irq:17 memory:e3b00000-e3bfffff           *-firewire                description: FireWire (IEEE 1394)                product: 1394 OHCI Compliant Host Controller                vendor: O2 Micro, Inc.                physical id: 0                bus info: pci@0000:09:00.0                version: 05                width: 32 bits                clock: 33MHz                capabilities: pm msi pciexpress ohci bus_master cap_list                configuration: driver=firewire_ohci latency=0                resources: irq:17 memory:e3b30000-e3b30fff           *-generic                description: SD Host controller                product: Integrated MMC/SD controller                vendor: O2 Micro, Inc.                physical id: 0.1                bus info: pci@0000:09:00.1                version: 05                width: 32 bits                clock: 33MHz                capabilities: pm msi pciexpress bus_master cap_list                configuration: driver=sdhci-pci latency=0                resources: irq:18 memory:e3b20000-e3b201ff           *-storage UNCLAIMED                description: Mass storage controller                product: O2 Flash Memory Card                vendor: O2 Micro, Inc.                physical id: 0.2                bus info: pci@0000:09:00.2                version: 05                width: 32 bits                clock: 33MHz                capabilities: storage pm msi pciexpress bus_master cap_list                configuration: latency=0                resources: memory:e3b10000-e3b103ff memory:e3b00000-e3b003ff        *-pci:4             description: PCI bridge             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7             vendor: Intel Corporation             physical id: 1c.6             bus info: pci@0000:00:1c.6             version: b4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list             configuration: driver=pcieport             resources: irq:18 ioport:2000(size=16384) memory:e2000000-e30fffff ioport:e0000000(size=17825792)           *-network                description: Ethernet interface                product: NetXtreme BCM5761 Gigabit Ethernet PCIe                vendor: Broadcom Corporation                physical id: 0                bus info: pci@0000:0a:00.0                logical name: eth0                version: 10                serial: d0:67:e5:46:95:89                capacity: 1Gbit/s                width: 64 bits                clock: 33MHz                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5761-v3.78 latency=0 link=no multicast=yes port=twisted pair                resources: irq:46 memory:e2010000-e201ffff memory:e2000000-e200ffff        *-usb:1             description: USB controller             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1             vendor: Intel Corporation             physical id: 1d             bus info: pci@0000:00:1d.0             version: 04             width: 32 bits             clock: 33MHz             capabilities: pm debug ehci bus_master cap_list             configuration: driver=ehci_hcd latency=0             resources: irq:17 memory:e3d30000-e3d303ff        *-isa             description: ISA bridge             product: HM65 Express Chipset Family LPC Controller             vendor: Intel Corporation             physical id: 1f             bus info: pci@0000:00:1f.0             version: 04             width: 32 bits             clock: 33MHz             capabilities: isa bus_master cap_list             configuration: latency=0        *-storage             description: SATA controller             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller             vendor: Intel Corporation             physical id: 1f.2             bus info: pci@0000:00:1f.2             logical name: scsi0             logical name: scsi1             version: 04             width: 32 bits             clock: 66MHz             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated             configuration: driver=ahci latency=0             resources: irq:42 ioport:70b0(size=8) ioport:70a0(size=4) ioport:7090(size=8) ioport:7080(size=4) ioport:7060(size=32) memory:e3d20000-e3d207ff           *-disk                description: ATA Disk                product: ST320LT009-9WC14                vendor: Seagate                physical id: 0                bus info: scsi@0:0.0.0                logical name: /dev/sda                version: 1001                serial: W0Q36CKK                size: 298GiB (320GB)                capabilities: partitioned partitioned:dos                configuration: ansiversion=5 signature=00040456              *-volume:0                   description: EXT4 volume                   vendor: Linux                   physical id: 1                   bus info: scsi@0:0.0.0,1                   logical name: /dev/sda1                   logical name: /                   version: 1.0                   serial: 1e6d393d-ae94-4983-83a4-e70974a40e66                   size: 294GiB                   capacity: 294GiB                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                   configuration: created=2013-06-14 17:04:29 filesystem=ext4 lastmountpoint=/ modified=2013-06-14 17:37:39 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-06-14 22:17:51 state=mounted              *-volume:1                   description: Extended partition                   physical id: 2                   bus info: scsi@0:0.0.0,2                   logical name: /dev/sda2                   size: 3993MiB                   capacity: 3993MiB                   capabilities: primary extended partitioned partitioned:extended                 *-logicalvolume                      description: Linux swap / Solaris partition                      physical id: 5                      logical name: /dev/sda5                      capacity: 3993MiB                      capabilities: nofs           *-cdrom                description: DVD reader                product: DVD-ROM DS-8D3SH                vendor: PLDS                physical id: 1                bus info: scsi@1:0.0.0                logical name: /dev/cdrom                logical name: /dev/dvd                logical name: /dev/sr0                version: HD15                capabilities: removable audio dvd                configuration: ansiversion=5 status=nodisc        *-serial UNCLAIMED             description: SMBus             product: 6 Series/C200 Series Chipset Family SMBus Controller             vendor: Intel Corporation             physical id: 1f.3             bus info: pci@0000:00:1f.3             version: 04             width: 64 bits             clock: 33MHz             configuration: latency=0             resources: memory:e3d10000-e3d100ff ioport:7040(size=32)  *-battery       product: DELL 2VYF521       vendor: Sanyo       physical id: 1       version: 01/09/2012       serial: 09BF       slot: Sys. Battery Bay       capacity: 62160mWh       configuration: voltage=11.1Vcd-drive version 0.83 x86_64-pc-linux-gnu
Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
The driver selected is GNU/Linux
The default device for this driver is /dev/cdrom


Drivers available...
  GNU/Linux ioctl and MMC driver     
  cdrdao (TOC) disk image driver     
  bin/cuesheet disk image driver     
  Nero NRG disk image driver         


CD-ROM drive supports MMC 3


                       Drive: /dev/cdrom
Vendor                      : PLDS    
Model                       : DVD-ROM DS-8D3SH
Revision                    : HD15
Profile List Feature
	Read only DVD


Core Feature


Morphing Feature
	Operational Change Request/Notification supported
	Synchronous GET EVENT/STATUS NOTIFICATION supported


Removable Medium Feature
	Tray type loading mechanism
	can eject the medium or magazine via the normal START/STOP command
	can be locked into the Logical Unit


Random Readable Feature


Multi-Read Feature


CD Read Feature
	C2 Error pointers are supported
	CD-Text is supported


DVD Read Feature


DVD+RW Feature


DVD+R Feature


DVD+R Double Layer Feature


Initiator- and Device-directed Power Management Feature


CD Audio External Play Feature
	SCAN command is supported
	audio channels can be muted separately
	audio channels can have separate volume levels
	256 volume levels can be set


Ability to respond to all commands within a specific time Feature


Ability to perform DVD CSS/CPPM authentication via RPC Feature
	CSS version 1
	
Ability to read and write using Initiator requested performance parameters Feature


The Logical Unit Unique Identifier Feature
	209190007871


Vendor-specific code 10b Feature


Vendor-specific code ffdf Feature


Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No


Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : No


Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : Yes
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : Yes


Writing....
  Can write CD-RW                         : No
  Can write DVD-R                         : No
  Can write DVD-RAM                       : No
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No


It is absolutely a burner.  Not sure why linux thinks it isn't

---

