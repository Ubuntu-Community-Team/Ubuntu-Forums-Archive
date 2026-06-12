---
title: "Acer Aspire Laptop Hardware problems"
date: 2011-04-04
forum: Hardware
---

### Post by dimaursu16 on 2011-04-04
Hi, everyone! 

I have an Acer Aspire 5050, and Ubuntu on it. My video card is ATI Radeon Xpress 1100, and here is what bothers me: 
1. when I want to play a game, the screen is flickering. 
2. I've tried to install ATI drivers, but when I run fglrxinfo(or whatever is the name of that command) it tells me "Segmentation fault".
 what is even strange than that, is that compiz runs very smooth, which I think can't   be done without video drivers. 
3. I think this problem is somehow related to a hardware problem
{I can't install windows, that's why I switched to Ubuntu (I'm very happy about that now)}
4. It may have something to do with the strange thing that in BIOS, the product name of my computer is YY-*and_ here_is_written_something* which I cant even call letters, they are more like a cloud, or dispersed points

Did you ever seen something like this? Can you give me some advice? 
(beside going to an Service Center, because I'm from Rep. of Moldova, and here I had once a problem with an "professional" which stolen half of my RAM)

here are my hardware specification:
```

PCI (sysfs)  
root-DD     /*I'm not logged in root, i just change my user name*/              
    description: Computer
    product: YY&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
    vendor: Acer, inc.
    version: Not Applicable
    serial: None
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific
  *-core
       description: Motherboard
       product: Prespa M
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: v1.3315 (11/14/07)
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology MK-36
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Engineering Sample
          slot: Socket M2/S1G1
          size: 800MHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff ioport:c8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:3
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:4
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:c0004000-c00041ff memory:64000000-6407ffff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB2D03E4GRR1TD
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ac7e5
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9ef35123-764c-48d8-b1fa-6004832e3e3c
                   size: 24GiB
                   capacity: 24GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-02 00:43:21 filesystem=ext4 lastmountpoint=/&#65533;<&#65533;G&#65533;&#65533;&#65533;&#65533;FF&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;&#65533;k-S&#65533;&#65533;&#65533;&#65533;!{W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-04-02 01:05:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-04-04 09:08:53 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 384MiB
                   capacity: 384MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 384MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/sda4
                   version: 1.0
                   serial: 7da65ea9-47d0-4c49-9c6b-fa01e9b80d9a
                   size: 86GiB
                   capacity: 86GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-13 17:50:13 filesystem=ext4 label=Data lastmountpoint=/media/sda4&#65533;&#65533;5'&#65533;&#65533;&#65533;&#65533;&#65533;&#448;&#65533;&#65533;&#65533;&#65533;&#65533;7H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;5' modified=2011-04-04 09:08:55 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-04-04 09:08:55 state=mounted
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0005000-c0005fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0006000-c0006fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0007000-c0007fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16) memory:fed00000-fed003ff
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PP02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:c0000000-c0003fff
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:c0200000-c02fffff memory:60000000-63ffffff
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 1
                bus info: pci@0000:08:01.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:23 memory:c0210000-c0210fff ioport:a400(size=256) ioport:a800(size=256) memory:60000000-63ffffff memory:68000000-6bffffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 1.1
                bus info: pci@0000:08:01.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: memory:c0211000-c021107f
           *-generic
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 1.2
                bus info: pci@0000:08:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=72 mingnt=32
                resources: irq:22 memory:c0211400-c02114ff
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 1.3
                bus info: pci@0000:08:01.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: memory:c0211800-c021187f
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 1.4
                bus info: pci@0000:08:01.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:22 memory:c0211100-c02111ff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:08:02.0
                logical name: eth0
                version: 10
                serial: 00:1b:24:3a:a3:10
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:20 ioport:a000(size=256) memory:c0211c00-c0211cff
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 4
                bus info: pci@0000:08:04.0
                logical name: wlan0
                version: 01
                serial: 00:16:cf:5b:d0:09
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:c0200000-c020ffff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

---

### Post by Kirboosy on 2011-04-04
It actually just might be the card in general. I used to have a laptop with a X1400 in it (slightly more powerful card than yours) and for the life of me it would not game well. It would run compiz great, but as soon as I fired up a game it would chug and do crazy things at times. Also my screen would randomly start flickering but if I set my power settings to "Blank Screen when closing laptop lid" and closed my laptop then reopened it everything would be fine again.

EDIT: I forgot to mention....I found that the 9 series ran best on the laptop because I never had any video issues with it until the 10 series of Ubuntu. I never rolled back to it after I upgraded to 10.04+ because I just dealt with it. I think its an xserver issue.

What games are you trying to run?

---

### Post by dimaursu16 on 2011-04-04
battle tanks(a very lightweight one)
and nexuiz

hmmm...interesting, will they fix this bug in 11.04?

---

### Post by Kirboosy on 2011-04-04
Probably not. The bug status that I filed on launchpad was never set to high. I don't have that computer anymore so I can't test the beta version and tell you. I think since its older hardware probably not.

---

### Post by dimaursu16 on 2011-04-04
still doesn't work

---

