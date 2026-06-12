---
title: "64 bits or 32 bits"
date: 2016-10-05
forum: Hardware
---

### Post by arunomi2 on 2016-10-05
When I use "sudo lshw" I get that the width of my motherboard is 32 bits and my cpu is 64 bits,
Can I use a 64bit os on this computer?

I ran a live usb with 64 bit lubuntu and the installation worked OK but when I try to boot the comp after the installation I get a kernel panic .

Mvh Sean

---

### Post by frostschutz on 2016-10-05
Not sure what you mean by "width of motherboard is 32 bits". You can't put a 64bit CPU on a 32bit motherboard in the first place.

If the live usb 64bit works fine then you should be fine with 64bit.

Feel free to actually provide any information (output of lshw you are referring to - details about the kernel panic you got)

---

### Post by Arunomi on 2016-10-05
When I run "sudo lshw" I get this print out:
```
arunomi-hp-xw4600         
    description: Mini Tower Computer
    product: HP xw4600 Workstation (RV724AV)
    vendor: Hewlett-Packard
    serial: CZC8375B81
   ** width: 64 bits**
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=mini-tower family=103C_53335X power-on_password=disabled sku=RV724AV uuid=82C4818C-BE86-DD11-BBD8-64174A040022

```
```
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Extreme CPU Q6850  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Extreme CPU Q6850  @ 3.00GHz
          slot: XU1 PROCESSOR
          size: 3GHz
          capacity: 3GHz
          **width: 64 bits**
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority dtherm cpufreq
          configuration: cores=4 enabledcores=4 threads=4

```

The width on the cpu i recon is that it has supports 64bit. but the width in the top box is it what the motherbord can handel or whats installed on this pc?

ps. this print outs are not from that pc. the pc im having problems are a hp dc7600 small form.

I installed a 64bit lubuntu on this pc and the installation went almost fine, in the end it just gave a error message that some applications hadent installed proporly but that you could install them when you booted in to the system.
when I booted i just got a blank screen with a underline line in the left top corner. so i went to bed to try again the next day.
the next day i got a kernal panic.

so I figuerd that the installation went wrong so I did a reinstall and this time it when fine but when i boot I just get a blank screen with a underline line in the top left corner.
And if i press the powerbutton i get the lubuntu shutdown screen and the pc shuts down

---

### Post by Bucky Ball on 2016-10-05
AMD64bit ISO. Download, create bootable install media, install.

```
width: 64 bits
          clock: 1333MHz
          capabilities: x86-64
```

---

### Post by QIII on 2016-10-05
Hello!

If that information is produced by a different computer, it is of no value in assessing your problem.  A veteranarian cannot determine what is wrong with your horse by looking at your neighbor's horse.

Please provide information from the machine in question.

Thanks.

---

### Post by Arunomi on 2016-10-05
So heres lshw from the computer in question.

and i used the live usb with lubuntu 64 to boot in to without installing.

but when i install and boot from the installation i get the problems mentiond above.

---

### Post by Dragonbite on 2016-10-05
While the live portion may be working, verify the media is good when trying to install. 

I've had systems that look like they installed properly, or threw an error during install, that when I ran, it threw it's ugly head and I ended up re-downloading and putting on the USB and trying again.

---

### Post by mörgæs on 2016-10-05
Do you have two user names in Ubuntuforum? 

Please post the exact error messages you get. Are you using Lubuntu 16.04.0 or 16.04.1?

---

### Post by Yellow Pasque on 2016-10-05
```
lubuntu
    description: Low Profile Desktop Computer
    product: HP Compaq dc7600 Small Form Factor (EC837ET#UUW)
    vendor: Hewlett-Packard
    serial: CZC6391RJL
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=low-profile family=103C_53307F sku=EC837ET#UUW uuid=6061DCF4-A64E-DB11-BBDA-716AB9020018
  *-core
       description: Motherboard
       product: 09F8h
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC6391RJL
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786D1 v01.03
          date: 05/18/2005
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 CPU 3.00GHz
          slot: XU1 PROCESSOR
          size: 2400MHz
          capacity: 3GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: Cache L2
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
             configuration: level=2
     *-cpu:1 DISABLED
          description: CPU [empty]
          vendor: Intel
          physical id: 6
          slot: XU1 PROCESSOR 2
     *-memory:0
          description: System Memory
          physical id: 36
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
             physical id: 0
             serial: 14F41503
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
             physical id: 1
             serial: 26EF1503
             slot: XMM2
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
             physical id: 2
             serial: 10F31503
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 64T32000HU3.7A
             vendor: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
             physical id: 3
             serial: 25EF1503
             slot: XMM4
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 37
          slot: System board or motherboard
          capacity: 1MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 1MiB
             width: 2 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
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
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0400000-e047ffff ioport:10c0(size=8) memory:d0000000-dfffffff memory:e0480000-e04bffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:27 memory:e04c0000-e04c3fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f4000000-f41fffff ioport:f4200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:e0500000-e07fffff ioport:f4400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:3f:00.0
                logical name: enp63s0
                version: 01
                serial: 00:18:71:6a:b9:02
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5752-v3.10 ip=192.168.1.81 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:26 memory:e0500000-e050ffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1000(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-31-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1020(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-31-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1040(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-31-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1060(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-31-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: 2.4G RX
                   vendor: DaKai
                   physical id: 1
                   bus info: usb@5:1
                   version: 3.11
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:e04c4000-e04c43ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: DataTraveler 112
                   vendor: Kingston
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi4
                   version: 1.00
                   serial: 0013729940C4FB11E516148F
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdc
                      size: 14GiB (15GB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=4e0b04b8
                    *-volume
                         description: Windows FAT volume
                         vendor: THREES
                         physical id: 1
                         bus info: scsi@4:0.0.0,1
                         logical name: /dev/sdc1
                         logical name: /media/lubuntu/KINGSTON
                         version: FAT32
                         serial: 40b6-655a
                         size: 14GiB
                         capacity: 14GiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=KINGSTON mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
              *-usb:1
                   description: Mass storage device
                   product: Flash Disk
                   vendor: CBM
                   physical id: 8
                   bus info: usb@1:8
                   logical name: scsi5
                   version: 1.00
                   serial: 211625019ED28404
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sdb
                      logical name: /cdrom
                      size: 2022MiB (2120MB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 mount.fstype=iso9660 mount.options=ro,noatime sectorsize=512 signature=473bb8b2 state=mounted
                    *-volume
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 2
                         bus info: scsi@5:0.0.0,2
                         logical name: /dev/sdb2
                         version: FAT12
                         serial: 0f7b-9366
                         size: 15EiB
                         capabilities: primary boot fat initialized
                         configuration: FATs=2 filesystem=fat
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:10a0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:10d8(size=8) ioport:10f0(size=4) ioport:10e0(size=8) ioport:10f4(size=4) ioport:10b0(size=16)
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDR8164B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0B10
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 4
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3808110AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: H
             serial: 4LR4PSRK
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=c05423fa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 4a968267-c883-40d8-8260-379936459512
                size: 71GiB
                capacity: 71GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-10-05 10:16:39 filesystem=ext4 lastmountpoint=/ modified=2016-10-05 11:19:09 mounted=2016-10-05 11:19:10 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 2860MiB
                capacity: 2860MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2860MiB
                   capabilities: nofs
```

---

### Post by Yellow Pasque on 2016-10-05
The memory controller is 32 bits. This is expected on an NM10 chipset. It means you are limited to 4GB of RAM. 

> Can I use a 64bit os on this computer?

Yes, but it's probably not a good idea on a system with 1GB of RAM. Any benefit you get from a 64bit OS is likely to be erased by the limited amount of RAM you have.

---

