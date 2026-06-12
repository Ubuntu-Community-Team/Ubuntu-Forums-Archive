---
title: "hardware upgrade suggestions?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by ericalejandrocasas on 2009-05-20
hello
i want to upgrade my computer, but i really don't know what to do with it this is what i currently have

eric-desktop              
    description: Desktop Computer
    product: P4M900T-M
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4M900T-M
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014 (03/17/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU 1
          size: 1200MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
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
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
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
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-system UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 mingnt=2
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64
           *-disk
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: P22O
                serial: PVF904Z5S7X72N
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00550055
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 89f27d52-ec15-4040-8d14-a8ecb4788a08
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-04-26 01:52:47 filesystem=ext3 modified=2009-05-20 11:39:16 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-20 11:36:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2580MiB
                   capacity: 2580MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2580MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H62N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:19:21:99:04:50
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=189.183.22.39 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0 module=snd_hda_intel
     *-scsi
          physical id: 3
          bus info: usb@5:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:66:d2:3c:e7:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


any suggestions?
thanks in advance!

---

### Post by Psyphre on 2009-05-20
whoa, information overload.
I think it would be more helpful to list your hardware parts, eg motherboard,how much ram you have, what graphics card , what CPU you have.

---

### Post by DLG102282 on 2009-05-20
I agree a more simpler system specs would help greatly.

---

### Post by khelben1979 on 2009-05-20
> **DLG102282 said:**
> I agree a more simpler system specs would help greatly.

Indeed.

---

### Post by ericalejandrocasas on 2009-05-21
haha, sorry, i guess youre right..so i have this:
motherboard ECS P4M900T-M
disk space (available) 129gb
intel(R) Pentium(R) Dual CPU E2160 @ 1.80 GHz
memory  1gb
DVD-RAM writer

and well thats pretty much it...yes...sad...i know

---

### Post by Psyphre on 2009-05-21
> **ericalejandrocasas said:**
> haha, sorry, i guess youre right..so i have this:
motherboard ECS P4M900T-M
disk space (available) 129gb
intel(R) Pentium(R) Dual CPU E2160 @ 1.80 GHz
memory  1gb
DVD-RAM writer

and well thats pretty much it...yes...sad...i know

Since you've got 129gb free that means youve got plenty of space left. No need to upgrade that.

What graphics card do you have?

Also what do you use your computer for, so that we can help suggest what you need to upgrade.

---

### Post by ericalejandrocasas on 2009-05-21
I don't think this has a graphics card, and well I just got this thing, but I wanna really upgrade it as much as I can, I just hope its not that expensive

---

### Post by Psyphre on 2009-05-21
Well you can upgrade lots of things, RAM, CPU, add a graphics card etc.

It depends what you want to do.If you let us know what you do with your computer it will be help us only upgrade what you need and not waste money on unnecessary things.

One thing that I would recommend you upgrade is RAM. Its always helpful to have more ram regardless of what you do. I'd have 2gb of RAM rather than just 1.

If you like to play games,the your defintely going to need a graphics card.

---

### Post by ericalejandrocasas on 2009-05-21
thanks!

but i do have a question, what graphics card should i get? i mean, I've never had one running under linux (ubuntu 9.04) would i have to install special software for a specific card? or what would you recomend i get, of course, nothing over 1 billion dollars :)

---

### Post by Psyphre on 2009-05-22
well if your not into playing games then  you dont really need a great graphics card.You might only want it for fancy compiz effects. I'd recommend nVidia personally as its supposedly better supported in linux - at least from common opinion and my own personal experience.

I've got a 7900 which is hardly cutting edge, but its cheap and plays my counterstrike and CnC3 perfect. I'd suggest you look into the 8000 series range. Maybe get an nvidia 8600. My brother has a Gainward nVidia 8600 which is a fantastic card and relativelty cheap.

I would also look into replacing that CPU of yours as 1.8ghz would be a bit too slow for me personally. Did you say it was dual core? They're reasonably cheap these days, the one I'm using is a duo core 2.4ghz (E6600) which really is a good balance between performance and cost.

Finally look into upgrading your ram to 2gb. Infact this is probably the first thing I'd do as RAM is cheap nowadays.

But as I said, without you telling me what exactly you want to do with your pc (heavy gaming or mainly just browsing web/email etc) then its difficult to tell you what you need or dont need to upgrade.

edit: For the graphics card you'll need to install the drivers for it. For me it detected the card and gave me the option to install the drivers automatically. Pretty simple.

---

### Post by Sef on 2009-05-22
> edit: For the graphics card you'll need to install the drivers for it. For me it detected the card and gave me the option to install the drivers automatically.

Not quite correct.  Your graphics card will be detected and drivers will be supplied.   However, they are open source drivers which are just fine as long as you don't want 3D effects.  If you want 3D effects, then you have to install the proprietary drivers.   Usually your card is detected, and you can easily install them.  (System > Administration > Hardware Drivers)

---

### Post by khelben1979 on 2009-05-22
> **ericalejandrocasas said:**
> thanks!

but i do have a question, what graphics card should i get? i mean, I've never had one running under linux (ubuntu 9.04) would i have to install special software for a specific card? or what would you recomend i get, of course, nothing over 1 billion dollars :)

I would suggest that you take a look [at this page]("http://www.tomshardware.com/charts/gaming-graphics-charts-2009/3DMark06-v1.1.0-3DMark-Score,1067.html") from Tom's hardware to get a view of what you can get for your money.

ATi have always worked good with Linux the times I have tested it, although nVidia have been way easier to install historically.

---

### Post by Psyphre on 2009-05-22
> **Sef said:**
> Not quite correct.  Your graphics card will be detected and drivers will be supplied.   However, they are open source drivers which are just fine as long as you don't want 3D effects.  If you want 3D effects, then you have to install the proprietary drivers.   Usually your card is detected, and you can easily install them.  (System > Administration > Hardware Drivers)

Thats what I meant, my graphics card was detected and ubuntu offered to download and install the proprietary drivers. Sorry if I was unclear.

---

### Post by ericalejandrocasas on 2009-05-22
thanks alot guys! ill give it some of the upgrades you mentioned and keep you updated.
thanks again!

---

### Post by Psyphre on 2009-05-22
> **ericalejandrocasas said:**
> thanks alot guys! ill give it some of the upgrades you mentioned and keep you updated.
thanks again!

No problem. If your unsure about something, let us know what exactly your thinking of buying before actualy buying it. I'd hate to see you make easy mistakes such as getting the wrong type of ram for your motherboard. A friend of mine has done that b4. Ended up being nice paper weights :) 

Good luck

---

