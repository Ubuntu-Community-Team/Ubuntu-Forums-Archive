---
title: "What do I need to learn, to make my Xubuntu PC stable?"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by quigleydoor on 2007-03-27
My Xubuntu 6.06 PC freezes, locks up, or spontaneously reboots whenever I play audio or video.  For 2 to 30 seconds it will run great, and then it will die.  However, it is very stable as long as I don't play multimedia.  I cannot find any useful information in **/var/log** (though I am a beginner and don't know what to look for).

What do I need to learn, where do I start, to find the root cause?  I think IRQ settings may be at fault.  I tried to use **irqtune**, but it throws an error, so I can't use it:

```
probe: kernel has module support (CONFIG_MODULES) -- ERROR
probe: kernel has symbols -- ERROR
```

Here is **lshw** output, showing my hardware specs:

```
quigley-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.5
          size: 450MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 620 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: c8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:c8000000-cbffffff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE
             resources: ioport:d000-d00f irq:14
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD136AA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 12GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   product: IC35L040AVER07-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 38GB
              *-cdrom
                   product: Hewlett-Packard CD-Writer Plus 9300
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: b3
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=sis5595_smbus
        *-generic UNCLAIMED
             product: ACPI
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.1
             bus info: pci@00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
        *-usb
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c7800000-c7800fff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-multimedia
             description: Multimedia audio controller
             product: YMF-724F [DS-1 Audio Controller]
             vendor: Yamaha Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-XG PCI
             resources: iomemory:c7000000-c7007fff irq:10
        *-network
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 30
             serial: 00:10:5a:d1:8c:0a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=3c59x ip=192.168.2.5 multicast=yes
             resources: ioport:b800-b87f iomemory:c6800000-c680007f irq:9
        *-display
             description: VGA compatible controller
             product: GeForce 6200
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@00:0c.0
             version: a1
             size: 256MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia
             resources: iomemory:c5000000-c5ffffff iomemory:d0000000-dfffffff iomemory:c4000000-c4ffffff irq:11

```

---

### Post by quigleydoor on 2007-03-28
C'mon people, my hardware is really basic old x86 stuff.  I thought there would be an expert here.  Why is nobody responding to my post?

---

### Post by Jim March on 2007-03-28
Just a hunch but...have you tried finding some video that doesn't have an audio track, and trying that?  Or flat-out disabling audio?

I'm thinking your Yamaha-based audio hardware (or it's drivers) are what are killing you here.

I can't tell for sure but it looks like you've got a desktop computer of some sort.  In which case, a new PCI audio card is dirt cheap, $20 or $30 new.  Removing or disabling your current audio and swapping that out might be the fastest solution.

---

### Post by pxwpxw on 2007-03-28
Might be the memory size 255MB and cpu speed 450MHz contributing to the problem, 
just too much to handle. Does windows run the same audio/video without problems?

My PC is fairly ancient OK for browsing etc  and I am using it now with kubuntu, 
but a bit slow for desktop graphics, but I dont play audio or video so cant comment on that.

Part of my config below for comparison.
BTW you need to run lshw as superuser to get full info.
```

$ sudo lshw

oldibm
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: i815-ITE8712
       vendor: Giga-Byte Technology Co., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (12/07/2000)
          size: 128KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect 
socketedrom e3floppy2880 int5printscreen int9keyboard int14serial int17printer
 int10video acpi usb agp
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: Socket 370
          size: 700MHz
          capacity: 800MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge m
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 128KB
             capacity: 512KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 768MB
 

```

Also top will show you cpu and memory loadings:
```

$ top

```
In xubuntu desktop, Applications - System - Process Manager shows CPU%,V Memory size.

---

### Post by dmizer on 2007-03-28
what program are you using to play audio and/or video?

---

### Post by quigleydoor on 2007-03-29
> **dmizer said:**
> what program are you using to play audio and/or video?

Xfmedia, XMMS Music Player, and Realplayer 10 all exhibit this problem.

---

### Post by quigleydoor on 2007-03-29
> **pxwpxw said:**
> Might be the memory size 255MB and cpu speed 450MHz contributing to the problem, 
just too much to handle. Does windows run the same audio/video without problems?

This hardware used to be dual boot of BeOS R5 and Win98.  BeOS ran audio and video just fine, while Win98 would exhibit the same type of behavior occasionally.  The sound would enter a locked loop of <1sec (like the sound buffer was not being updated, but the sound card continued to play through the buffer), and the machine would lock up.

So I'm getting the same type of problem that I saw in Win98, but much more frequently.

> My PC is fairly ancient OK for browsing etc  and I am using it now with kubuntu, 
but a bit slow for desktop graphics, but I dont play audio or video so cant comment on that.

Yes, graphics and Firefox are pretty slow on mine too.  But consistently slow, meaning that the system never gets bogged down or thrashes.  Right now I am running **abcde** (**cdparanoia**, **lame** and **oggenc**) as well as **top**, while editing in Firefox, and I hardly notice any additional slowness.  %CPU is in the high 90s.

I have a large swap partition of 6GB on a dedicated IDE disk.  ~200MB is used.

> BTW you need to run lshw as superuser to get full info.

Thanks for the heads up.  Here it is:

```

quigley-desktop
    description: Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: dmi-2.0
  *-core
       description: Motherboard
       product: ME-99
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.XX
       serial: MB-1234567890
       slot: LPT
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS ME-99 ACPI BIOS Revision 1004.A (07/29/99)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video
     *-cpu
          description: CPU
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.5
          slot: PGA-370
          size: 433MHz
          capacity: 800MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-memory
          description: System memory
          product: DIMM SDRAM Memory Controller
          physical id: 5
          size: 320MB
          capacity: 1536MB
        *-bank:0
             description: DIMM SDRAM [empty]
             physical id: 0
             slot: DIMM1-2
             clock: 14MHz (70ns)
        *-bank:1
             description: DIMM SDRAM
             physical id: 1
             slot: DIMM2-1
             size: 64MB
             capacity: 64MB
             clock: 14MHz (70ns)
        *-bank:2
             description: DIMM SDRAM [empty]
             physical id: 2
             slot: DIMM2-2
             clock: 14MHz (70ns)
        *-bank:3
             description: FPM
             physical id: 3
             slot: DIMM3-1
             size: 128MB
             capacity: 128MB
             clock: 14MHz (70ns)
        *-bank:4
             description: FPM
             physical id: 4
             slot: DIMM3-2
             size: 128MB
             capacity: 128MB
             clock: 14MHz (70ns)
     *-cache:0 UNCLAIMED
          description: L1 cache
          physical id: c
          slot: L1 Cache
          size: 32KB
          capacity: 32KB
          capabilities: internal write-back
     *-cache:1 UNCLAIMED
          description: L2 cache
          physical id: d
          slot: L2 Cache
          size: 128KB
          capacity: 128KB
          capabilities: burst internal write-back
     *-pci
          description: Host bridge
          product: 620 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: c8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:c8000000-cbffffff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE
             resources: ioport:d000-d00f irq:14
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD136AA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 80.10A80
                   serial: WD-WM6780250474
                   size: 12GB
                   capacity: 12GB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume
                      description: Linux swap / Solaris partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 6502MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC35L040AVER07-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: ER4OA46A
                   serial: SXPTX2N6768
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 38GB
                      capabilities: primary
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: Hewlett-Packard CD-Writer Plus 9300
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.0b
                   serial: YM20349W7C
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: b3
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=sis5595_smbus
        *-generic UNCLAIMED
             product: ACPI
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.1
             bus info: pci@00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
        *-usb
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c7800000-c7800fff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-multimedia
             description: Multimedia audio controller
             product: YMF-724F [DS-1 Audio Controller]
             vendor: Yamaha Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-XG PCI
             resources: iomemory:c7000000-c7007fff irq:10
        *-network
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 30
             serial: 00:10:5a:d1:8c:0a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.2.5 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:b800-b87f iomemory:c6800000-c680007f irq:9
        *-display
             description: VGA compatible controller
             product: GeForce 6200
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@00:0c.0
             version: a1
             size: 256MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia
             resources: iomemory:c5000000-c5ffffff iomemory:d0000000-dfffffff iomemory:c4000000-c4ffffff irq:11

```

---

### Post by quigleydoor on 2007-03-29
> **Jim March said:**
> Just a hunch but...have you tried finding some video that doesn't have an audio track, and trying that?  Or flat-out disabling audio?

I'm thinking your Yamaha-based audio hardware (or it's drivers) are what are killing you here.

I can't tell for sure but it looks like you've got a desktop computer of some sort.  In which case, a new PCI audio card is dirt cheap, $20 or $30 new.  Removing or disabling your current audio and swapping that out might be the fastest solution.

This sounds like a good hunch.  As a shortcut I will just take out the sound card and see if video plays.

I don't know anything about sound card options.  What is a good choice for reliability?

If I get this old nag to work, it will be the internet radio device for my home office (as well as the print server and netshare with scheduled backups!).

---

### Post by him610 on 2007-03-29
You probably have used all of your available memory and have begun using your swap partition which is on your hard drive, and your hard drive being a hard drive is slower.

With just the bare XFCE interface up and no other applications running, from a terminal CLI, type free
In the results, you will probably see the you are probably already using around 170MB of memory which only leaves around 80MB for any applications you might be running before you begin to use  your swap.

Here are a couple of suggestions: 
1) Buy some more memory; 256MB is not enough for what you seem to want to do with it; 
2) USB memory sticks and SD memory with 1GB, 2GB, or even 4GB are all fairly cheap right now; there is a way to configure these external memory devices as cache memory. I don't know right off hand how to do it, but I saw a post on it a couple of weeks ago in one of the *buntu forums.

Good luck.

---

### Post by quigleydoor on 2007-04-01
I confirmed that I was able to play MPEG1 videos with no audio track, so at that point I was pretty sure that I needed to get a new sound card.  I picked up a Sound Blaster Audigy SE for 30 bucks, and now I can play sound files without crashing the OS.

Streaming audio is not working, but at least it is not crashing the OS.  That's a challenge for another weekend.

Thanks to all.

---

