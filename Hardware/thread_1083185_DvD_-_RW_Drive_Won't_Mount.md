---
title: "DvD - RW Drive Won't Mount"
date: 2009-02-28
forum: Hardware
---

### Post by unplugged23 on 2009-02-28
Hey there,

Earlier today I was having a problem mounting blank dvd's in my dvd drive. I realised it was a just a dvd drive and not a dvd - rw drive after a while, So i replaced it with a dvd - rw drive. This drive won't mount blank dvd roms, or pre recorded ones like movies, or data roms. Any help? :confused:

---

### Post by taurus on 2009-02-28
Both DVD & DVD-RW burner can read DVD just fine unless you have a CD and try to read a DVD with it.

Is it PATA or SATA?  Have you looked in the BIOS to see if it even detects your new DVD drive?

---

### Post by unplugged23 on 2009-02-28
I know the drive is detected, because I can see it in the Places < computer. However when i try to mount it by double clicking it says "Unable to mount location, no media in drive." I am not sure how to determine weather it is Pata or Sata. Thanks a lot for the reposnse! :P

---

### Post by taurus on 2009-02-28
Besides the power cable on the back, if you see another skinny cable connect to the drive (usually black), then it's SATA.  But if you see a large ribbon like the old fashion harddrive, then it's PATA.

However, if you know the model and brand of the drive, you can look it up.  

Run this command from a terminal and see if your DVD is on the list.

```
sudo lshw
```

---

### Post by unplugged23 on 2009-02-28
Ok thanks, I have a pata drive. Here is the output of the code you gave me: 

```
 description: Mini Tower Computer
    product: Dimension 4600
    vendor: Dell Computer Corporation
    serial: 6MLRX21
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=hardware-failure-fw chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4D00-104C-8052-B6C04F583231
  *-core
       description: Motherboard
       product: 02Y832
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN4811135801F1.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A02 (05/07/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2800MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 420]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=serial latency=64
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: 00:07:e9:78:48:53
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-75AU
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 18.2
                serial: WD-WMA6R4404045
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=92bc92bc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/sda1
                   version: 1.0
                   serial: 2c3fba6c-f6c3-4456-a641-bbd84f2a72de
                   size: 776MiB
                   capacity: 776MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-05 20:58:35 filesystem=ext3 modified=2003-05-06 19:00:35 mount.fstype=ext3 mount.options=rw,errors=continue,data=ordered mounted=2003-05-06 19:00:35 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/sda2
                   version: 1.0
                   serial: c89f8696-18f4-46c3-b33f-db6a5e41f4e3
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-19 16:28:27 filesystem=ext3 modified=2003-05-06 19:00:35 mount.fstype=ext3 mount.options=rw,errors=continue,data=ordered mounted=2003-05-06 19:00:35 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.16
                serial: 3JV6N2NS
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ea1aa9c7
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 239f45d6-2d27-4d50-a400-72b0e9ddb51b
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2003-05-06 19:53:10 filesystem=ext3 modified=2003-05-06 19:00:33 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2003-05-06 19:00:33 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   version: 1
                   serial: 11e0e02e-7a39-4ce5-b684-2dc07d13773e
                   size: 2133MiB
                   capacity: 2133MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom:0
                description: CD-R/CD-RW writer
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=ready
           *-cdrom:1
                description: DVD writer
                product: CD/DVDW TS-H552L
                vendor: TSSTcorp
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0614
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             size: 1912MiB (2004MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/disk
                version: FAT16
                serial: 1014-f030
                size: 1911MiB
                capacity: 1911MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:3
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: iPod
             vendor: Apple
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 1.62
             serial: YM848A3U3QZ2
             size: 7601MiB (7971MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
                size: 7601MiB (7971MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=20202020
              *-volume UNCLAIMED
                   description: W95 FAT32 partition
                   physical id: 1
                   capacity: 950MiB
                   capabilities: primary
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:68:13:d8:99:dc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by taurus on 2009-02-28
> **unplugged23 said:**
> Ok thanks, I have a pata drive. Here is the output of the code you gave me: 

[CODE] 
           *-cdrom:0
                **[COLOR="Red"]description: CD-R/CD-RW writer[/COLOR]**
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=ready
           *-cdrom:1
                [B][COLOR="Red"]description: DVD writer
                product: CD/DVDW TS-H552L
                vendor: TSSTcorp[/COLOR][/B]
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0614
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc


You have one CD and one DVD drives.  Are you sure you insert the DVD into the right drive?

Looks like your DVD-RW is the Toshiba-Samsung drive-TSSTcorp.

---

### Post by unplugged23 on 2009-02-28
Yes, I've been inserting the DvD's into the right drive. :P

---

### Post by unplugged23 on 2009-03-01
Bump :(

---

### Post by unplugged23 on 2009-03-01
It's not recognizing any CD media either. Do you think it could be beneficial to download and install the driver? Doesn't Ubuntu have a built in feature for this? How can I use this? I'd like to give it a try. :P :confused:

Thanks for any help!

---

### Post by unplugged23 on 2009-03-03
Bump

---

### Post by unplugged23 on 2009-03-04
Well, I took my CD - RW drive out of the top bay, and added a new dvd - rw drive, and it works fine. So I guess the only thing you can really assume at this point is that its just a hardware problem with the drive :( What would have caused this so suddenly?

---

### Post by Decommissioner on 2009-10-07
Hello, I am experiencing problems similar with this as well.

Only, I was in the middle of burning an iso using brasero, and it failed. The dvd-rw is partially written, and now my system doesn't want to detect it. I've tried using brasero, k3b, and gnomebaker, and they all have trouble detecting the dvd in my dvd drive.

---

### Post by MASTERFANG on 2009-10-07
well i guess try using another DVD-RW. may be there could be problem in your DVD-rw.
i am not sure..but try writing with any other DVD-RW.

---

