---
title: "Which harddisks fit a given computer"
date: 2010-03-08
forum: Hardware
---

### Post by ThomasDenmark on 2010-03-08
How do I know which harddisks are compatible with a given computer?

So far in my chaotic IT life, it has been trial and error, but now I would really like to know. 

I guess it should be possible to do with the unix tool lshw, which simply prints misc. data about the hardware. Below I have pasted the information about "ide" which I think is what I need. 

```
         *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:5a000000-5a0003ff

```How do I tell from this, which types of harddisks will fit the computer?

Thomas

---

### Post by wojox on 2010-03-08
Look at:

```
*-disk
```

---

### Post by cascade9 on 2010-03-08
ICH4M is just the mobile variant of ICH4, which appeared with the 845 series chipsets, which should all have 48-bit LBA, so it should do 137GB + HDD sizes. Should. If it doesnt, your limited to HDDs smaller tha 137GB. 

You should (again, LOL) be able to hook up any IDE HDD to that controller and get the full HDD size. Being an 'M' series (moblie) I would guess that its from a laptop, and most of them only take 2.5'' drives.

In theory, all 845 chipset motherboards will be fine with 48bit LBA, but no doubt there is some hardware manufacturer who has an 845 chipset board around that fails to work. 48bit LBA hit in 2002, ICH4 in mid 2003 so its more likely that it will do 48bit LBA, but really....I'd check the manufacturers site. 

*admits to being a hardware monkey......if that wasnt already obvious*

---

### Post by ThomasDenmark on 2010-03-09
vojox: The problem with looking at the *-disk is that there may not be a harddisk in the computer. Also, I do not think that you can tell from the current harddisk type, which range of other harddisk types the motherboard supports. 

cascade9: Wow, thanks for giving such a thorough answer, on this particular lshw extract. This just shows me how little insight I have, I did not even know that chipset could be a limiting factor for the size of the drive. 

What I still don't understand is: Is ATA66, ATA100 and ATA133 just about the transfer speed? Will an ATA133 hd work for an ATA100 controller? How do I know the transfer speeds that the chipset supports? Please correct me, if I have got it wrong.

Thomas

---

### Post by cascade9 on 2010-03-09
> **ThomasDenmark said:**
> cascade9: Wow, thanks for giving such a thorough answer, on this particular lshw extract. This just shows me how little insight I have, I did not even know that chipset could be a limiting factor for the size of the drive. 

What I still don't understand is: Is ATA66, ATA100 and ATA133 just about the transfer speed? Will an ATA133 hd work for an ATA100 controller? How do I know the transfer speeds that the chipset supports? Please correct me, if I have got it wrong.

Thomas

Its not so much the chipset as the controller/BIOS. Just with that partitcular controller, its part of the chipset. If you ran a later add-on PCI/PCIe card, or have a different controller intergrated into the motherboard, you could very well run a hdd that the chipset controller doesnt support. 

ATA66/100/133 isnt just about the transfer speeds.....but near enough in the real world. An ATA 133 drive should work fine in ATA 66/100 controllers, and vice vesa. For that matter, it should even work fine in an ATA 33 controller, or even a PIO controler (but then its going to be as slow as a wet week, and max HDD size is 2.1 GB so you really dont want that).

---

### Post by ThomasDenmark on 2010-03-09
Great. 

So now just one last question. How do I see if my disk controller supports e.g. ATA133. Because if not, then I might choose an ATA100 over an ATA133, if it is cheaper. 

Thomas

---

### Post by cascade9 on 2010-03-09
I *think* that the ICH4-M only supports ATA100, (I know it does that at a minimum). If you tell me what model motherboard/computer/laptop you have, I can probably find out pretty easily. 

I wouldnt really worry about ATA 133- it never was that much faster than ATA 100. IIRC when it came out only maxtor released drives under that specification. Hitachi does them as well these days, but I really wouldnt worry about it that much to be hoenst.

---

### Post by ThomasDenmark on 2010-03-09
This was an attempt for me to learn how to decipher the information that I get from lshw, and use that to know which hd's would work. However, since you are not able to tell, then I am probably not going to learn that either :)

But besides this thread being a "learn how to tell from lshw" experiment, I actually am about to buy a larger hd for my laptop, and if you can tell me whether it supports ATA133, I would appreciate that. 

The computer that I have is an Acer TravelMate C300, and below is the entire lshw result.

```

velle-laptop
    description: Computer
    product: TravelMate C300
    vendor: Acer
    version: -1
    serial: LXT280E253451024F0M000
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=3CCC5840-4FE3-11D9-B9E7-DA5870A6AD03
  *-core
       description: Motherboard
       product: TravelMate C300
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXT280E253451024F0M000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.11 (11/01/04)
          size: 111KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: U1
          size: 1500MHz
          capacity: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1280MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:50000000-59ffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:10 memory:e0216000-e0216fff ioport:3000(size=256) ioport:3400(size=256) memory:50000000-53ffffff(prefetchable) memory:5c000000-5fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:10 memory:e0217000-e0217fff ioport:3800(size=256) ioport:3c00(size=256) memory:54000000-57ffffff(prefetchable) memory:60000000-63ffffff
              *-pccard UNCLAIMED
                   description: SmartCardBus Reader
                   vendor: O2Micro
                   physical id: 0
                   version: V1.0
                   slot: Socket 1
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:10 memory:e0215000-e02157ff memory:e0210000-e0213fff
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5705M Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 03
                serial: 00:0a:e4:a2:11:fc
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.07 ip=84.238.87.119 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
                resources: irq:11 memory:e0200000-e020ffff memory:58000000-5800ffff(prefetchable)
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@0000:02:06.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:96:be:84
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
                resources: irq:11 memory:e0214000-e0214fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
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
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:5a000000-5a0003ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB4O
                serial: SB044GGJK8JZ5V
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a292a292
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home/velle/mountpoint
                   version: FAT32
                   serial: 2629-16f0
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,errors=remount-ro state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2196MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 37GiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 51GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
           *-cdrom
                description: DVD writer
                product: DVD-RW DVR-K14RA
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:10 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

```Thomas

---

### Post by cascade9 on 2010-03-09
LOl, sorry if I ruined your experiment. I'm far more of a hardware person than software to be honest, I just read your original  lshw output, say 'ICH4-M' and tookit from there. 

I actually dont know of any software that can tell you things like max installable HDD sizes. It would be a very handy tool. 

As for ATA133- I'm (pretty) sure it doesnt support that. The drive will work, btu you wont get ATA133 transfers. As an aside, if I did things my 'normal' way I could well have been wrong about what your computer even supports. If you check the acer sepifications it says this- 

> Core Logic ChipsetIntel Almador-M / ICH3-M [http://support.acer.com/acerpanam/notebook/0000/Acer/TravelMate620/TravelMate620sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/TravelMate620/TravelMate620sp2.shtml)

ICH3-M is a whole series earlier than the ICH4-M. ICH3-M would have a much smaller chance of supporting 137GB + HDDs. Your laptop has a 830 chipset with a newer ICH4-M southbridge (which normally appeared only on 845 chipsets). 

As an aside, that info page if wooful. Awful. Nasty. 

> Hard Disk Drive20GB Ultra ATA/100 or higherThat tells us virtually nothing. No max hdd size, no interface max speed, etc. Annoying. But that is typical of 'corporate' info pages I've found. Not much you can do about it......

---

### Post by ThomasDenmark on 2010-03-09
I bugged up! Sorry. 

I have had two Acer TravelMates. One 620 and now a C300. I accidentally, by habit or smth. wrote 620 in the previous post by me. I then clicked edit and changed it to C300. But you obviously read the post before I got the fix the error, sorry :(

That is why you got incoherent information. 

Thomas

---

### Post by cascade9 on 2010-03-09
Not a problem. I've done similar things in the past. I even made the mistake of putting '845 chipset' before, when I should have put '855' (mobile version of the 845). 

The L300 makes more sense. It still hasnt got max hdd size, or max interface speed, but it does have the right ICH version (which inst specifided, but I know that the 855/ICH4-M is a standard configuration)- 

> Core Logic ChipsetIntel 855GM
Hard Disk Drive40GB to 80GB Ultra ATA/100

[http://support.acer.com/acerpanam/notebook/0000/Acer/TravelMateC300/TravelMateC300sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/TravelMateC300/TravelMateC300sp2.shtml)

I'd still bet on it only supporting ATA 100. So not much else changes. ;) 

BTW, after a bit of a look around, I dont think that any Intel southbridge supported ATA 133.

---

### Post by ThomasDenmark on 2010-03-09
Thank you very much for your help. I learned a lot, and now I know what to buy :)

Thomas

---

### Post by cascade9 on 2010-03-09
Glad it helped, good luck with your new HDD. :)

---

