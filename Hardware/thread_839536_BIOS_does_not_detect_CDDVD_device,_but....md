---
title: "BIOS does not detect CD/DVD device, but..."
date: 2008-06-24
forum: Hardware
---

### Post by Fhernd on 2008-06-24
Hi!

My laptop Toshiba does not work fine, it has the next problem:

When I enter in the BIOS program (pressing F2) in the main module 'BIOS Main', the CD/DVD device does not appear, check the next image link:

**[BIOS Main]("http://softvaina.googlepages.com/BIOS.Main.jpg")**

Then, I go to BIOS Boot module, and the CD/DVD device appears in the boot device list, check the next image link:
[B][URL="http://softvaina.googlepages.com/BIOS.Boot.jpg"]
BIOS Boot[/URL][/B]

Finally, I try to boot from CD/DVD device and it works (check this **[image]("http://softvaina.googlepages.com/BootMenu.jpg")**).

In the Operating System (Ubuntu) environment, the CD/DVD device does not appear, and it does not work.


Laptop features:

Brand/Model: TOSHIBA Satellite A205-S4639
H.D.D.: 160GB + 120GB
RAM: 3GB DDR2
Video: NVIDIA GeForce Go 7300
Optical Disk Drive: PIONEER DVD-RW DVR-K17LF


Note: I upgraded the BIOS, but the problem persists.


**[SIZE="4"]What is happening?[/SIZE]**

---

### Post by logos34 on 2008-06-24
seems there's problem with the drive not being recognized in vista either (some fix involving filter thresholds in the registry).  There's no firmware upgrade listed on Pioneer site (I can't even find the model).

Youmight want to post your 

sudo lshw -C disk

---

### Post by Fhernd on 2008-06-24
In the Windows XP operating system, the device (CD/DVD) does not appear (same problem with Ubuntu SO). :(

---

### Post by logos34 on 2008-06-24
what does lshw show (if anything?

how did you get ubuntu on it (netinstall?) *nm, forgot you could boot from it

---

### Post by Fhernd on 2008-06-24
> **logos34 said:**
> what does lshw show (if anything?

how did you get ubuntu on it (netinstall?) *nm, forgot you could boot from it

lshw shows this:
```
laptop                    
    description: Computer
    product: Satellite A205
    vendor: TOSHIBA
    version: PSAFCU-00F009
    serial: 37101857Q
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific cpus=2 uuid=275735E0-CE1A-11DB-A70E-00A0D170DEB7
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: Intel Corporation
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 5.20 (10/25/2007)
          size: 104KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          slot: U2E1
          size: 1733MHz
          capacity: 2048MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 4MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: M1
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1733MHz
          capacity: 1733MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
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
                product: G72M [Quadro NVS 110M/GeForce Go 7300]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:a0:d1:70:de:b7
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.26.26 latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:0b:0a:2b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:07:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:07:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:07:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:07:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7 module=sdhci
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB3D04E5JK753E
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ec160575
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/System
                   version: 3.1
                   serial: aca85692-625f-824c-8ac3-6b557e6b1100
                   size: 42GiB
                   capacity: 42GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-14 16:09:31 filesystem=ntfs label=System mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 34GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 760MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: W95 FAT32 partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /media/MEDIA
                      capacity: 34GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
           *-disk:1
                description: ATA Disk
                product: TOSHIBA MK1637GS
                vendor: Toshiba
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: DL03
                serial: 276GF52AS
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=236ebfe8
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/Jhon
                   version: 3.1
                   serial: f44022ac-6501-5046-b075-ac77f1d12ae7
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-03-24 05:11:13 filesystem=ntfs label=Jhon mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

More...

Now, when I try to boot from the Ubuntu LiveCD, the ***sdc0*** special file appears in ***/dev/***.

And if I try to boot a LiveCD based on Windows (e.g. BartePE, Active@ Boot Disk, Hiren's BootCD, etc.), the CD/DVD appears in the explorer.

:(

---

### Post by logos34 on 2008-06-24
ok, so lshw shows no cdrom (as I suspected, but thought I'd double check)

is there a '/dev/scd0 /media/cdrom0' .... or the like in /etc/fstab?

But the fact that it's not appearing under lshw means linux can't even see it.  

Maybe someone else has the answer (like maybe blacklisting or adding ata modules so the drive is recognized at boot). not sure. but the fact that even in windows it doesn't appear (except if it's a boot cd/iso of some sort), and doesn;'t show in one of the bios screens seems to indicate a deeper problem (hardware? firmware?)

---

### Post by Fhernd on 2008-06-24
> **logos34 said:**
> ok, so lshw shows no cdrom (as I suspected, but thought I'd double check)

is there a '/dev/scd0 /media/cdrom0' .... or the like in /etc/fstab?

But the fact that it's not appearing under lshw means linux can't even see it.  

Maybe someone else has the answer (like maybe blacklisting or adding ata modules so the drive is recognized at boot). not sure. but the fact that even in windows it doesn't appear (except if it's a boot cd/iso of some sort), and doesn;'t show in one of the bios screens seems to indicate a deeper problem (hardware? firmware?)

This shows */dev/fstab*:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=3c82f784-7320-40b6-951d-a8b2a20aa197 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=425aa6de-8f47-33bb-dcc5-c10efcf95757 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/System ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Jhon ntfs-3g defaults,locale=en_US.UTF-8 0 0
```


Rare, rare, rare problem, is Truth?.. :confused:

---

### Post by logos34 on 2008-06-24
wish i had the answer.

---

### Post by brons2 on 2008-06-24
There is a firmware update for the Pioneer drive on the Toshiba support site.

---

### Post by Fhernd on 2008-06-24
> **brons2 said:**
> There is a firmware update for the Pioneer drive on the Toshiba support site.

**brons2**, where I can find exactly the firmware for PIONEER DVD-RW DVR-K17LF?

Thanks.

---

### Post by brons2 on 2008-06-24
Sorry about that, the firmware update is for a different DVD model, a Toshiba made one. 

I have the same one that you do on my Toshiba, maybe that's what triggered something in my mind.  Sorry about that.

---

### Post by Fhernd on 2008-06-25
Is possible to reset the BIOS as the BIOS of desktop computer (using jumpers)?

---

### Post by logos34 on 2008-06-25
yeah, find the 2- or 3-pin reset/clear header on the board.  or else remove the CMOS battery for ~30 sec.  That just clears any user profiles/saved settings; it won't won't rollback the Bios version (not that you want to)

---

### Post by Fhernd on 2008-06-25
Or Can I to put manually the CD/DVD drivers at OS loading (similar way to LiveCD charge the drivers) ???

---

### Post by Fhernd on 2008-06-30
Hi!

The problem has automatically disappeared.

Saturday on morning I turned on my laptop, then the Ubuntu's Desktop has ready, I went to Computer, inside I saw the CD/DVD drive.

*Resuscitated*

Rare, NO?


So long!

---

