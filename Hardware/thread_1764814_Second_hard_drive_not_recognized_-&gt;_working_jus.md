---
title: "Second hard drive not recognized -&gt; working just before clean install"
date: 2011-05-22
forum: Hardware
---

### Post by mark0495 on 2011-05-22
Hi,

I just got a laptop, some years old from someone I know. It's an Acer Aspire 5310. When I got it, there was Windows Vista on it. There were two disk drives on there: the drive with the system files, and a big drive called DATA. I wanted to put Kubuntu 11.04 on there, and I did. I chose the "use full drive" option in the installation, assuming that would also include the second "DATA" drive. 
After the installation, the hard disk drive DATA just vanished; I can't find it in Kubuntu, fdisk -l doesn't detect it, neither does any partitioning boot disc I have here at home. 
There was one, however, that detected a second hard drive, but when I tried to access it, it said "Can't read drive parameters" and wouldn't let me access it. 
My question is, obviously, if there might be a way to restore the hard disk; I don't think a clean Kubuntu installation can completely corrupt a hard disk, or can it?

Here are my specs according to lshw:
```
    description: Notebook
    version: V1.40
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=63DA13BD-8BE0-09F3-3EEC-001B382218AA
  *-core
       description: Motherboard
       product: Acadia
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAH30Y0097290F6F41601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.40
          date: 06/29/2007
          size: 97KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
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
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0300000-d037ffff ioport:5088(size=8) memory:c0000000-cfffffff memory:d0400000-d043ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0380000-d03fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:d0440000-d0443fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:d0000000-d00fffff ioport:40400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:22:18:aa
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5787m-v3.22 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:d0000000-d000ffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:d0100000-d01fffff ioport:40600000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:1c:26:05:02:71
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.56+Broadcom,11/02/2005, 4.10.4 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: irq:19 memory:d0100000-d0103fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0644000-d06443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d0200000-d02fffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: memory:d0200000-d020007f
           *-generic
                description: SD Host controller
                product: ENE PCI SmartMedia / xD Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:20 memory:d0200400-d02004ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
                resources: memory:d0200800-d020087f
           *-memory:2
                description: FLASH memory
                product: ENE PCI Secure Digital / MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:20 memory:d0200100-d02001ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5090(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T20N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WP03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:5478(size=8) ioport:5470(size=4) ioport:5468(size=8) ioport:545c(size=4) ioport:5440(size=16) memory:d0644400-d06447ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8037GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: DL25
                serial: 67QUF14CS
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b330d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cf440fe0-5a77-4386-96d1-c499d0dda4a0
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-19 15:48:42 filesystem=ext4 lastmountpoint=/ modified=2011-05-19 16:27:30 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-22 13:39:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1013MiB
                   capacity: 1013MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1013MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5420(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

```

This is the fdisk -l output (translated from Dutch by me):

```
Hard disk drive /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track(?), 9729 cilinders
Unit = cilinders of 16065 * 512 = 8225280 bytes
Sector (logic/fysical): 512 bytes / 512 bytes
input/output (minimal/optimal): 512 bytes / 512 bytes
Drive-ID: 0x000b330d

 Drive      Boot     Begin       End     Blocks       ID  System
/dev/sda1   *           1        9601    77111296   83  Linux
/dev/sda2            9601        9730     1037313    5  Extended
/dev/sda5            9601        9730     1037312   82  Linux swap
```

If I need to post more of this, please tell me ;)

Thanks in advance,
Mark

---

### Post by IcarusR on 2011-05-22
Are you sure there are two hard drives in the laptop ?
Possibly one drive had been partitioned in to two partitions one smaller one for OS & the larger one for data & labelled as such.

Can you see more than one drive in the BIOS ?

Try launching gparted from terminal & see what shows there.

Try booting from live cd & check fdisk & gparted.

---

### Post by mark0495 on 2011-05-22
I think that the partition story has to be right. I never really knew that you could set up partitions to show up as letters in Windows, but I'm also not so much of an expert. Thing is, I never really paid attention to how big the two drives/partitions were. I can remember that the one with the system on it got full very quickly. Also, on the fact sheet below my keyboard, there's nothing about a second HDD. 

It didn't show up in the BIOS either, and the gparted and fdisk commands gave the same output on a live disc. I guess we have a conclusion, then :) 

Thanks very much :D
Mark

---

