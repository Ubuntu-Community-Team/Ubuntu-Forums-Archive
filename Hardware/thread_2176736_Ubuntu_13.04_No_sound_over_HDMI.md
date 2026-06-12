---
title: "Ubuntu 13.04 No sound over HDMI"
date: 2013-09-25
forum: Hardware
---

### Post by squid636 on 2013-09-25
I need some advice on how to get my sound working over HDMI. I have tried upgrading and downgrading the kernel. I have installed the fixes from the web that I have found and nothing seems to be working. I have some experience with Linux so I can post logs I just don't know what logs you need.  Thanks in advance.

Here is a link to the asla information.
[http://www.alsa-project.org/db/?f=f1d8fed0127d31edede22bb0f83d44f022e5e0b6]("http://www.alsa-project.org/db/?f=f1d8fed0127d31edede22bb0f83d44f022e5e0b6")

Output of lshw command:
```
server
    description: Desktop Computer
    product: GeForce 9300 Series ()
    vendor: EVGA
    version: 1
    serial: 1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0807-060504030201
  *-core
       description: Motherboard
       product: GeForce 9300 Series
       vendor: EVGA
       physical id: 0
       version: 1
       serial: 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 03/02/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13flop$
     *-cpu
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Pentium(R) Dual-Core
          slot: Socket 775
          size: 2500MHz
          capacity: 2500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge $
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DRAM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 3584 bits
        *-bank:1
             description: DIMM DRAM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 3 bits
        *-bank:2
             description: DIMM DRAM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 2GiB
             width: 3 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DRAM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 2GiB
             width: 771 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:11 ioport:ff00(size=64) ioport:1c00(size=64) ioport:1c80(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.3
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor
             description: Co-processor
             product: MCP79 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=nvidia latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:eff00000-eff7ffff
        *-usb:0
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:effff000-efffffff
        *-usb:1
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:efffe000-efffe0ff
        *-usb:2
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:efffd000-efffdfff
        *-usb:3
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:efffc000-efffc0ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:23 memory:efff0000-efff3fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:efe00000-efefffff
           *-network
                description: Wireless interface
           *-network
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: Ralink corp.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: wlan0
                version: 00
                serial: 00:0d:08:4c:06:53
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-19-generic firmware$
                resources: irq:18 memory:efef0000-efefffff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:1f:bc:03:92:99
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-$
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 dupl$
             resources: irq:41 memory:efffb000-efffbfff ioport:fc00(size=8) memory:efffa000-efffa0ff $
        *-storage
             description: SATA controller
             product: NVIDIA Corporation
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(si$
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
           *-network
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: Ralink corp.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: wlan0
                version: 00
                serial: 00:0d:08:4c:06:53
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-19-generic firmware$
                resources: irq:18 memory:efef0000-efefffff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:1f:bc:03:92:99
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-$
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 dupl$
             resources: irq:41 memory:efffb000-efffbfff ioport:fc00(size=8) memory:efffa000-efffa0ff $
        *-storage
             description: SATA controller
             product: NVIDIA Corporation
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(si$
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
           *-network
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: Ralink corp.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: wlan0
                version: 00
                serial: 00:0d:08:4c:06:53
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-19-generic firmware$
                resources: irq:18 memory:efef0000-efefffff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:1f:bc:03:92:99
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-$
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 dupl$
             resources: irq:41 memory:efffb000-efffbfff ioport:fc00(size=8) memory:efffa000-efffa0ff $
        *-storage
             description: SATA controller
             product: NVIDIA Corporation
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(si$
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
       *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:efd00000-efdfffff ioport:f2000000(size=1$
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:16 memory:efdfe000-efdfffff memory:f2000000-f200ffff
           *-ide
                description: IDE interface
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:$
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250823A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.03
             serial: 3ND28DHV
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000331ee
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /export/neo
                version: 1.0
                serial: 789b5ec1-d4bb-4548-a5b1-31f8b253acad
                size: 229GiB
                capacity: 229GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files d$
                configuration: created=2013-09-23 11:50:02 filesystem=ext4 lastmountpoint=/ modified=$
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3837MiB
                capacity: 3837MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3837MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72202
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: JKAO
             serial: JK1131YAHMS0MV
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=a16a8cf9-9635-43d3-868e-8246cee389c3 sectorsize=512
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/2tb
                version: 1.0
                serial: 52a015f3-494b-4022-a1ac-a01b7644cbbd
                size: 1863GiB
                capacity: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover $
                configuration: created=2013-05-07 19:43:32 filesystem=ext4 label=2tb lastmountpoint=/$
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3000DM001-9YN1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: CC4C
             serial: W1F0PNFF
             size: 2794GiB (3TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=40fd94da-94b4-48d0-adc3-58a65a614c13 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/3tb
                version: 1.0
                serial: 95450ef8-6e3e-42e4-90a0-8632fe743f52
                size: 2794GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover $
                configuration: created=2013-05-04 18:28:07 filesystem=ext4 label=3tb lastmountpoint=/$
     *-scsi:3
          physical id: 5
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31500341AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdd
             version: CC1H
             serial: 9VS2YJTV
             size: 1397GiB (1500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=8455940a-2827-41eb-8f3b-3668811779d7 sectorsize=512
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdd1
                version: 1.0
                serial: 4fe0f528-22ba-41dd-a34a-66830bedf08d
                size: 1397GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents $
                configuration: created=2013-05-05 18:05:32 filesystem=ext4 label=1.5tb lastmountpoint$

                                         
```

Picture is of the alsamixer command in the terminal. I cannot select any other devices using F6. Matter of fact none of the function keys work at all in that program.
[ATTACH=CONFIG]246513[/ATTACH]

---

### Post by miguel6 on 2013-09-25
Don't be offended by my solution but just in case you didn't do this...

When I plug my HDMI cable into my laptop and want audio to output the HDMI, I go up to the speaker icon and hit "Sound Settings..." and select HDMI

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_008_zps38fc5ac3.png~original[/IMG]

---

### Post by Yellow Pasque on 2013-09-26
```
Kernel release:    3.8.0-19-generic
```

That's kind of an old kernel (and it's known to have issues with HDMI audio: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984) ). When was the last time you updated your system?

---

### Post by Yellow Pasque on 2013-09-26
spekaer-test is always a good utility too:

```
speaker-test -t sine -c 2 -D <devicename>
```

Get devicename from:
```
aplay -L
```

---

### Post by BenTurpin on 2013-10-16
Hello,
I also have no sound and when I open the Sound setting, I get the box as you showed, but in the box with 'Play Sound through' i find nothing. Obviously I need to install something, and a new user of Ubuntu, could you inform me what and how to install?
Thanks, Ton

sorry I forgot to mention I am replying to the post that gives infromation on the Sound setting.

---

