---
title: "External [and internal] ssd"
date: 2015-02-06
forum: Hardware
---

### Post by shantiq on 2015-02-06
i am told that if i install Ubuntu on one of those ssd drives [http://www.amazon.co.uk/dp/B008OE0S56/ref=dra_a_rv_ss_hn_it_P1400_1000?tag=dradisplay0bb-21&ascsubtag=ee339965f10fc0f50e6ae9d2a6fed6c5_S](http://www.amazon.co.uk/dp/B008OE0S56/ref=dra_a_rv_ss_hn_it_P1400_1000?tag=dradisplay0bb-21&ascsubtag=ee339965f10fc0f50e6ae9d2a6fed6c5_S) it is way faster than on a normal HDD drive


Now i know nothing about this area of computing; so if i bought one of these and then used a live usb to install Ubuntu onto the external ssd [i have a usb 3.0 port]  and then asked the bios to always boot from the ssd and use the HDD as merely storage space    would i then have a much faster system ?


PS    my computer is ten years old a packard bell


would the bios "see" the ssd?


PS2     would installing an internal ssd be even faster   and where does it go?    in a PCI slot?


what is the best course of action here please

PS3    what size would you go for/   which models would you suggest?






thanx in advance    shan

---

### Post by kerry_s on 2015-02-06
whats all the specs on the system?

yes, ssd is faster than hdd, no moving parts. 
will it be fast enough for you to even notice a difference, not by itself. it takes many parts in your pc to work together.
but hey, every bit helps. might not be what you expect, but it'll be something.

internal ssd is the way to go.

---

### Post by shantiq on 2015-02-06
>>>>

```
shantiq@shantiq-00000000000000000000000:~$ sudo lshw[sudo] password for shantiq: 
shantiq-00000000000000000000000
    description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc500000-fe6fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe680000-fe6fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe67c000-fe67ffff
        *-pci:1
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 3
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 memory:fe700000-fe7fffff
           *-usb
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fe7ff000-fe7fffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-network:0
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:03:01.0
                logical name: eth1
                version: 10
                serial: 00:0a:cd:26:64:71
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=82.20.25.138 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
                resources: irq:9 ioport:8800(size=256) memory:fe8ffc00-fe8ffcff memory:fe8c0000-fe8dffff
           *-network:1
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8ff800-fe8ff8ff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:03:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8ff000-fe8ff7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/ modified=2015-02-06 16:27:52 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-02-06 16:27:52 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage



```

---

### Post by kerry_s on 2015-02-06
it could help a bit.
your cpu is fairly fast, but it's a single core.
ya got 2.5gb memory, so thats good.

basically it's old school, ssd's are cheap now so why not. i just did mine not to long ago, just grabbed a 60gb ssd off amazon when they had xmas sales, it was like 50% off, $25 some dollars.
i got a quad core atom 1.6ghz, 2gb ram. i do feel it does help with some lagginess, but over all not much different than the hdd. i put my ssd in place of the dvd drive, which barely worked anyways, left my hdd in it's place as storage.

---

### Post by shantiq on 2015-02-06
ok so i am thnking either of:

[http://www.amazon.co.uk/Poppstar-Solid-State-Drive-Kit/dp/B00GYZRGIE/ref=sr_1_17?s=computers&ie=UTF8&qid=1423249369&sr=1-17&keywords=ssd+samsung](http://www.amazon.co.uk/Poppstar-Solid-State-Drive-Kit/dp/B00GYZRGIE/ref=sr_1_17?s=computers&ie=UTF8&qid=1423249369&sr=1-17&keywords=ssd+samsung)
[http://www.amazon.co.uk/Samsung-120GB-Basic-Solid-State/dp/B00E3W15P0/ref=sr_1_3?s=computers&ie=UTF8&qid=1423249369&sr=1-3&keywords=ssd+samsung](http://www.amazon.co.uk/Samsung-120GB-Basic-Solid-State/dp/B00E3W15P0/ref=sr_1_3?s=computers&ie=UTF8&qid=1423249369&sr=1-3&keywords=ssd+samsung)

as excellent reviews



anyone other suggestions?

PS    how is it installed what is needed?   where does it go?   guess i too could whip out the dvd drive as i now use an external BR drive
PS2  is my ten-year-old bios going to "see" this


thanx for input



shan

---

### Post by kerry_s on 2015-02-06
do you have sata connections inside ? i was thinking yours has the old big wires.
you may need to get like an adapter.
[http://www.amazon.co.uk/mSATA-SSD-IDE-3-5-Adapter/dp/B00J3XT7E0/ref=sr_1_4?s=computers&ie=UTF8&qid=1423251208&sr=1-4&keywords=ssd+samsung+ide](http://www.amazon.co.uk/mSATA-SSD-IDE-3-5-Adapter/dp/B00J3XT7E0/ref=sr_1_4?s=computers&ie=UTF8&qid=1423251208&sr=1-4&keywords=ssd+samsung+ide)

you should look inside the box, see whats there. if you don't have sata already, i wouldn't bother. better to save up for a better pc, yours is at that age where things are going to start failing anyways.

---

### Post by shantiq on 2015-02-07
looks like i have sata   or is that something else?

see


```
*-ide:0             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             **configuration: driver=sata**_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             **configuration: driver=sata**_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
```

---

### Post by kerry_s on 2015-02-07
> description: IDE interface

just saying you should look inside & be sure before ordering anything.

---

### Post by shantiq on 2015-02-07
ok thanx for that kerry    will av a look

---

### Post by gordintoronto on 2015-02-07
I don't think you will get much of a performance boost; the rest of the computer is pretty slow. For just over twice as much money, you could get an i3-4330 processor with appropriate motherboard and memory, and it will fly compared to your current system.

---

### Post by shantiq on 2015-02-08
ok gordon this makes sense. is that easy to change on the inside?   basically i want this machine to be brought forward in time without having to fully replace it
i have already added    nvidia card for graphics so it plays 1080p    i have an external lexicon soundcard and external BR drive and recently added usb 3.0 ports [altho speed increase is not baffling]
so not 2005 but more modern   could you show online where to look for these higher spec hardwares if you have the time  [not myself a great techie] and basic instructions

could i even use [this]("http://www.amazon.co.uk/Intel-Q6600-Core2-2-4GHz-Processor/dp/B000LRMR26/ref=sr_1_1?ie=UTF8&qid=1423383627&sr=8-1&keywords=intel+quad+core") ? or is the [one]("http://www.amazon.co.uk/Intel-1150-i3-4330-Box-CPU/dp/B00EF1G9ZU/ref=sr_1_1?ie=UTF8&qid=1423386162&sr=8-1&keywords=i3-4330") you suggested better  are there limits or can i change almost everything just keep the box ::]]


thanx   shan

---

### Post by efflandt on 2015-02-08
Your PC seems to be only a bit newer than my early Athlon64 3200+ from 2004. So I suspect is has a wide ribbon cable for its internal drive(s) (now called PATA as opposed to SATA drives). And I am not even sure if you have USB 2.0 much less USB 3.0 (even my PC from 2010 does not have USB 3.0). So a SATA SSD might not work internally without a different controller and older USB might not be that fast externally.

It was not until I tried an SSD in a laptop from 2006 that I realized that its internal SATA1 5400 RPM drive was no faster than a USB 2.0 hard drive. The SSD on SATA1 was 4X faster than the 5400 RPM drive, about the same as the SATA2 7200 RPM drive in my desktop. With the SSD on SATA2 it was another 2X faster than on the SATA1 laptop, or 8X faster than portable USB 2.0 drive. The SSD is 80 GB from before Ubuntu 11.04 was released, Model=INTEL SSDSA2M080G2GC, so newer drives with suitable interface may be faster.

---

