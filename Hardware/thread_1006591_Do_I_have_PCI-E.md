---
title: "Do I have PCI-E?"
date: 2008-12-09
forum: Hardware
---

### Post by bunny_basher on 2008-12-09
Hello, here is my lshw...

description: Mini Tower Computer
    product: Dell DV051
    vendor: Dell Inc.
    serial: B5K002J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-3500-104B-8030-C2C04F30324A
  *-core
       description: Motherboard
       product: 0JC474
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN708215A401FV.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A03 (10/08/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Microprocessor
          size: 3066MHz
          capacity: 4GHz
          width: 64 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: FFFFFFFFFFFFFFFF
             physical id: 0
             serial: FFFFFFFF
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: NT512T64U88A0BY-37
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: 4C712479
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-multimedia
                description: Multimedia audio controller
                product: CM8738
                vendor: C-Media Electronics Inc
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=C-Media PCI latency=64 maxlatency=24 mingnt=2 module=snd_cmipci
           *-network:0
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:03:02.0
                logical name: wifi0
                version: 01
                serial: 00:18:e7:1d:cc:ae
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.159 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 04
                serial: 00:13:20:aa:d2:51
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H12N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: UL01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-ide:1
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST3160828AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 8.03
                serial: 5MT36C5N
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=29286e57
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 1eaa48ab-802f-b444-b695-cf151881da32
                   size: 75GiB
                   capacity: 75GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-08 21:28:28 filesystem=ntfs state=clean
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: 3bfa6d28-f960-4cb5-bec2-915b99ae94ae
                   size: 70GiB
                   capacity: 73GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-03-08 00:19:00 filesystem=ext3 modified=2008-08-05 20:59:19 mounted=2008-08-05 20:19:44 state=clean
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: a3f2c468-62db-4484-bee9-1f6b2247a9ae
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@4:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 975MiB (1022MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/RIDISC
                version: FAT32
                serial: c450-51b0
                size: 975MiB
                capacity: 975MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:8a:90:fa:9b:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Cheers,
Marcus

---

### Post by nick09 on 2008-12-09
Open up your case and compare them to these:
[http://upload.wikimedia.org/wikipedia/commons/f/fc/PCIExpress.jpg](http://upload.wikimedia.org/wikipedia/commons/f/fc/PCIExpress.jpg)

The bottom slot in the example is a regular PCI slot so that is not what you are looking for. If you have a PCI-E slot, it should say what it is on the motherboard.

---

### Post by Therion on 2008-12-09
Currently, no.  You have an Intel integrated graphics chipset.

---

### Post by nick09 on 2008-12-09
He is asking if he has PCI-E slots not what his graphics card is. The fastest way is to open the case and to take a look.

---

### Post by bunny_basher on 2008-12-09
I have a Dell PC so not very up-grade-able lol

Does this bit mean i do have PCI-e though..

*-pci:0
description: PCI bridge
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pci **[COLOR="Red"]pciexpress[/COLOR] **msi pm bus_master cap_list
configuration: driver=pcieport-driver
*-pci:1
description: PCI bridge
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 04
width: 32 bits
clock: 33MHz
capabilities: pci **[COLOR="red"]pciexpress[/COLOR]** msi pm bus_master cap_list
configuration: driver=pcieport-driver

I know it sounds noobish but i want a yes from the Pro's before I go out and buy a card!

Thanks alot,
Marcus

---

### Post by MonkeyPaw on 2008-12-09
It looks like you're running the 915/910 chipset, which I think was Intel's first budget PCIe chipset. However, that doesn't necessarily mean you have an x16 slot for a graphics upgrade. As others have said, open the case and look inside. The slot nearest the CPU should be about as long as the white PCI slots below, but a PCIe slot will be a different color and offset from the PCI slots. If you're still not sure, take a pic of the inside and post it here. :)

---

### Post by DGortze380 on 2008-12-09
> **bunny_basher said:**
> I have a Dell PC so not very up-grade-able lol

Does this bit mean i do have PCI-e though..

*-pci:0
description: PCI bridge
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pci **[COLOR="Red"]pciexpress[/COLOR] **msi pm bus_master cap_list
configuration: driver=pcieport-driver
*-pci:1
description: PCI bridge
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 04
width: 32 bits
clock: 33MHz
capabilities: pci **[COLOR="red"]pciexpress[/COLOR]** msi pm bus_master cap_list
configuration: driver=pcieport-driver

I know it sounds noobish but i want a yes from the Pro's before I go out and buy a card!

Thanks alot,
Marcus

There are a number of PCIe slots, there's a v2 now if I'm not mistaken. It appears you you have SOME KIND of PCIe. Whether it's PCI Expressx2, PCI Expressx16 or some other variant I don't know. You'll have to open the case and see.

---

### Post by jimartin8219 on 2008-12-09
Have you called Dell and talked to them?  They should be able to tell you.

---

### Post by bunny_basher on 2008-12-11
[CENTER]I rekon this is where the fun ends, to me (noob) it looks like normal PCI.[/CENTER]
[COLOR="Red"][CENTER]**[SIZE="4"]PLEASE TELL ME I'M WRONG![/SIZE]**[/CENTER][/COLOR]
[IMG]http://i258.photobucket.com/albums/hh246/Bunny_Baher/2.png[/IMG]

[IMG]http://i258.photobucket.com/albums/hh246/Bunny_Baher/1-1.png[/IMG]
Is that PCI or PCI-e? If it is PCI-e then what type?

Thanks....... alot :D

Marcus

---

### Post by DGortze380 on 2008-12-11
the black one is PCIx1 or 2 I forget but not 16

---

### Post by nick09 on 2008-12-11
> **DGortze380 said:**
> the black one is PCIx1 or 2 I forget but not 16

The black one is PCI-Ex1. There is not many but there is two cards on newegg:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069620108&Configurator=&Subcategory=48&description=&Ntk=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069620108&Configurator=&Subcategory=48&description=&Ntk=&SpeTabStoreType=&srchInDesc=)

Also if I were you, I'd take a can of air and clean that case out.

---

### Post by MonkeyPaw on 2008-12-11
Yeah, that much dust there tells me it's probably a lot worse where your fans are. An yeah, you can get an x1 PCIe video card. It won't be terribly fast, but any ATI or nVidia product should put Intel's graphics to shame.

---

### Post by FoxIII on 2008-12-11
If it has a green slot with a 'clip' type thing at the end, then yes. Otherwise, probably not.

---

### Post by nick09 on 2008-12-12
> **FoxIII said:**
> If it has a green slot with a 'clip' type thing at the end, then yes. Otherwise, probably not.

What he has is PCI-E. A simple clip does not matter. Go to wikipedia and compare his black slot to the PCI-E slots.

---

### Post by bunny_basher on 2008-12-12
Thanks, I do hoover my case out every month, I am renovating my house at the moment though so there is alot of dust! I knew a comment would come up when i was taking the pictures!

Thanks alot,
Marcus

---

### Post by nick09 on 2008-12-12
Ah so that's the reason why. You will need a low Profile card if your case is small(width-wise if the case is standing up like a tower). By just what the two pictures you provide you can't use the the more costly card. Though I don't know if you got another expansion by next to the black PCI-E slot.

---

