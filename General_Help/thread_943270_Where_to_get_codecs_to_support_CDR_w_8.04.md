---
title: "Where to get codecs to support CDR w/ 8.04"
date: 2008-10-10
forum: General Help
---

### Post by TBerk on 2008-10-10
New install of 8.04 and I want to be able to burn CDs w/ the internal

HP CD Writer PLUS (8000 Series).

Secondary complication: the system isn't full time online, I can transfer files via USB from this system I'm posting with but can only really hook it up to the Internet in limited time frames. (Partly this is a wifi card not yet recognized and hard wired access is a logistical problem.)

Yesterday I was online with the new Ubuntu system and was able to run an update of what it thought were important files; including downloading an 8.04.1 ISO- but I cant burn it to CD from that system yet.

TBerk

---

### Post by Pro-reason on 2008-10-10
I'm not quite sure if I understand you.

If you want to burn discs, then make sure that Brasero is installed, and use that.

Are you saying that the drive is not recognised?  If you put (non-blank) discs in there, are they recognised?

---

### Post by sunbird on 2008-10-12
I'm having a strange problem. I've got 8.04 running on my laptop and it reads disks fine. It *used* to burn disks fine too, but has recently stopped recognizing that a CD-R is in the drive. I.e. I open brasero and put a blank CD-R in and it says 'please insert a disk.' 

It's not a hardware problem because burning works fine when booted into mac os. And I've also tried multiple blank disks. And the weirdest thing is that I used to burn disks fine. 

Ideas?

---

### Post by exploder on 2008-10-12
Try the 0.8.2 version of Brasero. You can get it here.

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

Post back your results.

---

### Post by sunbird on 2008-10-12
I downloaded and installed the new version of Brasero, no dice.

I think this may be a bigger issue.

When I put a CD in the drive and click on the CD drive on the left side of a nautilus window, nothing happens. But I can read from the drive just fine if I mount it manually, i.e, through

```

sudo mount /media/cdrom0

```

I can browse the contents just fine on terminal:

```

$ cd cdrom0
/media/cdrom0$ ls
autorun.inf  casper  dists  install  isolinux  md5sum.txt  pics  pool  preseed  README.diskdefines  ubuntu  umenu.exe  wubi.exe

```

But clicking on the CD/RW drive in nautilus still yields no results.

Here's the relevant line from fstab:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Pro-reason on 2008-10-12
Please post the output of the “lshw” command.  It may be convenient to dump to a file first:

```

sudo lshw > lshw.txt
gedit lshw.txt &

```

---

### Post by sunbird on 2008-10-13
Here ya' go:

```

    description: Computer
    product: MacBookPro3,1
    vendor: Apple Inc.
    version: 1.0
    serial: W873227RX91
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal uuid=9CFE245E-D0C8-BD45-A79F-54EA5FBD3D97
  *-core
       description: Motherboard
       product: Mac-F4238BC8
       vendor: Apple Inc.
       physical id: 0
       version: PVT
       serial: 1
       slot: Part Component
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          slot: U2E1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache:0
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 4
          bus info: cpu@1
          version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          slot: U2E1
          size: 2200MHz
          capacity: 2200MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 7
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache:1
          description: L1 cache
          physical id: 6
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 0x4D342037305432393533455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0xF611BC83
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: 0x4D342037305432393533455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 1
             serial: 0xF611BDAE
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: 10
          version: MBP31.88Z.0070.B02.0706181323 (06/18/07)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-19-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Bluetooth wireless interface
                   vendor: Apple Computer, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 19.65
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-19-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.24-19-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR5418 802.11abgn Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: wifi0
                version: 01
                serial: 00:1c:b3:b7:b2:97
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.101 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth0
                version: 13
                serial: 00:1b:63:98:23:4f
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-19-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-19-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-19-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: IR Receiver
                   vendor: Apple Computer, Inc.
                   physical id: 1
                   bus info: usb@5:1
                   version: 0.16
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=1.5MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Apple Internal Keyboard / Trackpad
                   vendor: Apple Computer
                   physical id: 2
                   bus info: usb@5:2
                   version: 0.16
                   capabilities: usb-2.00
                   configuration: maxpower=40mA speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.24-19-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=6 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Video
                   product: Built-in iSight
                   vendor: Apple Inc.
                   physical id: 4
                   bus info: usb@7:4
                   version: 1.45
                   serial: 407A023EB4F51D68 (03.01)
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB82AA2 IEEE-1394b Link Layer Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:0d:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=248 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD-R   UJ-857E
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: ZA0E
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: FUJITSU MHW2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0081
                serial: NZ0ST772P2FD
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0 UNCLAIMED
                   description: EFI GPT partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   capacity: 200MiB
                   capabilities: primary nofs
              *-volume:1
                   description: Primary partition
                   vendor: Mac OS X
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 4
                   serial: a42eeda1-c2a4-70bf-0000-00000037c000
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable osx hfsplus initialized
                   configuration: boot=osx checked=2008-03-26 01:11:21 created=2008-03-26 01:11:21 filesystem=hfsplus lastmountedby=10.0 modified=2008-10-10 06:26:58 state=clean
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /boot
                   version: 1.0
                   serial: 3867bf0e-7b5c-4739-9dad-d34996780a57
                   size: 190MiB
                   capacity: 190MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-07 08:35:16 filesystem=ext3 modified=2008-10-10 06:34:43 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-10-10 06:34:43 state=mounted
              *-volume:3
                   description: W95 FAT32 partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   serial: 62767b42-9554-403c-bbb2-d6558f3c3041
                   size: 96GiB
                   capacity: 96GiB
                   width: 256 bits
                   capabilities: primary bootable encrypted luks initialized
                   configuration: bits=256 cipher=aes filesystem=luks hash=sha1 mode=cbc-essiv:sha256 version=1
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: Unknown
       vendor: Unknown
       physical id: 1
       version: Unknown
       serial: Unknown
       slot: Unknown

```

I think the relevant bit is here:

```

        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD-R   UJ-857E
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: ZA0E
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open

```

---

### Post by Pro-reason on 2008-10-13
What error does Brasero give you when it fails to burn?

---

### Post by sunbird on 2008-10-13
Perhaps I wasn't clear, Brasero does not detect that a disk is in the drive. The upper portion of the burn dialog remains greyed out.

As I mentioned, this is not a issue with the drive being defective because the burner works fine in Mac OS (and, strangely, worked fine a couple of months ago in Ubuntu). 

I'm stumped and would love any help. :)

---

### Post by Pro-reason on 2008-10-13
I don't see an easy resolution for this.  It is something that should just work, and yet it doesn't.  It may be appropriate to report the problem at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/).

One last thing: what kernel are you using (do “uname -r”)?  Using a different kernel could affect the problem (as the kernel contains all the most essential drivers).

---

