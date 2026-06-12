---
title: "Use of CPU &amp; Memory Resource"
date: 2008-07-21
forum: General Help
---

### Post by moody_mark on 2008-07-21
Hi, I got a old PC which I installed kubuntu onto. Im trying to convince the wife that linux is better but until I can get things running as fast as they were on Windows XP, no amount of arguing will convince her (I even tried the "theres nearly no virus risk with linux" but that didnt really swing it)

Can you tell me;

1. Which terminal commands can I use to query my hardware specs? 2. Are there any ways I can get a bit more responsiveness out of the PC

Thanks

---

### Post by hyper_ch on 2008-07-21
> **moody_mark said:**
> 1. Which terminal commands can I use to query my hardware specs?
```

lshw

```

---

### Post by Heinzelotto on 2008-07-21
To increase performance PC you could try Xubuntu, which is made for low-end hardware, rather than kubuntu.

---

### Post by PmDematagoda on 2008-07-21
Or, if you want to improve performance on Kubuntu, you can try these things:-
1) Compile a custom kernel that is tailor-made for the PC your are using it on.

2) Disable unnecessary applications and services.

3) Try and use as many light applications that won't put too much load on the PC.

---

### Post by moody_mark on 2008-07-21
Thanks... so the ```
 lshw 
``` output is as below. Is this a bit under spec for KDE do you think?

```
marge
    description: Desktop Computer
    product: Deskpro
    vendor: Compaq
    serial: 8052DYSZ085X
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=9FEE6EC0-7BDD-D411-815F-B2DB73545F25
  *-core
       description: Motherboard
       product: 0684h
       vendor: Compaq
       physical id: 0
       serial: 8052DYSZ085X
       slot: Line I/O: MIC
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686P2 v2.04 (08/25/2000)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.8.6
          slot: XU1
          size: 733MHz
          capacity: 1GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: burst internal write-through
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 256KiB
             capacity: 4MiB
             capabilities: burst internal write-through
     *-memory:0
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          capacity: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             product: HYS64V16300GU-7.5.
             vendor: JEDEC ID:C1 49 4E 46 49 4E 45 4F
             physical id: 0
             serial: DDF40F07
             slot: XMM1
             size: 128MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             vendor: JEDEC ID:00 00 00 00 00 00 00 00
             physical id: 1
             serial: 00000000
             slot: XMM2
             size: 128MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             product: 71V32635AT8-H
             vendor: JEDEC ID:AD FF FF FF FF FF FF FF
             physical id: 2
             serial: 52110117
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 22
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: XU15
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82815 Chipset Graphics Controller (CGC)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:02:a5:27:51:f4
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.2.4 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD800BB-00FJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 13.0
                serial: WD-WMAJ94814814
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d7b798bd
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 58e7c5ea-a811-4ac3-8b7d-6175d814f3ef
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-17 21:57:27 filesystem=ext3 modified=2008-07-20 21:18:19 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-20 14:36:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1466MiB
                   capacity: 1466MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: A05.
                serial: 692934854146
                size: 8063MiB (8455MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8a38cbfe
              *-volume
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: 5433-394b
                   size: 8054MiB
                   capacity: 8054MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
           *-cdrom
                description: CD-R/CD-RW writer
                product: LTR-32123S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: XS0X
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
                                        
```

---

### Post by matthewboh on 2008-07-21
I always show the time for the first web page to come up or the time for a document to come up.  XP is actually pretty good for getting you to the desktop, but then can take forever to be able to use it.

You have 512MB - should be plenty to run.  For example, I'm running a Centrino M 1400Mhz with 1GB and it takes about 30 seconds to get to my desktop

---

### Post by moody_mark on 2008-07-21
> **matthewboh said:**
> For example, I'm running a Centrino M 1400Mhz with 1GB and it takes about 30 seconds to get to my desktop

See this is what im wondering, i only have an old CPU;

 ```
         product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.8.6
          slot: XU1
          size: 733MHz
          capacity: 1GHz
          width: 32 bits
          clock: 133MHz
```

My RAM utilisation is around 450MB I think last time I checked. (whats the best command for RAM utilisation - "top" perhaps?)

---

### Post by PmDematagoda on 2008-07-21
If you just want to see how much of RAM has been used, is free or cached without any specific information, then the command you will want is:-
```
free -m
```

---

### Post by matthewboh on 2008-07-21
I went back to look at your original post and saw that your wife isn't happy with the speed.  What are you comparing it to?  A faster machine?  How fast is fast and how slow is slow?  Does it take 10 minutes to boot or 35 seconds?  Does the wife really want a brand new machine and even if it got down to 10 seconds - that would still be too slow?

Here's one thread about the boot process that might help you...

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by moody_mark on 2008-07-21
> **matthewboh said:**
> What are you comparing it to?

On the same machine previously we were running windows XP professional. In fact all I did was slip in another HDD and install ubuntu on that. So we can now dual boot. The Kubuntu has the newer 80GB disc, the XP runs on an older 10GB disc.

The speed is not bootup speed, thats about the same. Its opening up applications and general responsiveness from the applications thats all.

So I ran the command above "free -m" and I got the following results

Total - 502
Used - 457

This is with the machine just sitting there with a idle KDE desktop and only the terminal window open. Is there a command to list which process is munching up all the memory?

---

### Post by PmDematagoda on 2008-07-21
Actually, used does not always mean the amount of RAM used by processes, can you please post the entire output of free -m, perhaps that may clear things up.

---

### Post by moody_mark on 2008-07-21
This is the output of free -m

```
marge@Marge:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           502        495          6          0         22        259
-/+ buffers/cache:        214        287
Swap:         1466         36       1430
```

---

