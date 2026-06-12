---
title: "P4 overclock"
date: 2012-02-24
forum: Hardware
---

### Post by roelforg on 2012-02-24
I'm not an overclocking expert.

But i noticed something in my lshw output after upgrading some HW.
Better see yourself:
```

  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) 4 CPU 1.80GHz
       vendor: Intel Corp.
       physical id: 5
       bus info: cpu@0
       version: 15.1.2
       slot: XU1 PROCESSOR
       size: 1800MHz
       capacity: 3GHz
       width: 32 bits
       clock: 400MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
       configuration: id=0

```
Look at the capacity (3GHZ).
If i could achieve it, my pc would work a lot better.
Sadly, i'm not an overclock expert (or novice) and don't know how.
Does anybody know?

---

### Post by Yellow Pasque on 2012-02-24
It is probably running at 1.8GHZ to save power. Under load, it should ramp to 3GHz. Can you post output of:
```
cpufreq-info
```

---

### Post by roelforg on 2012-02-24
```

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 448 MHz - 1.79 GHz
  available frequency steps: 448 MHz, 673 MHz, 897 MHz, 1.12 GHz, 1.35 GHz, 1.57 GHz, 1.79 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 448 MHz and 1.79 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.79 GHz (asserted by call to hardware).
  cpufreq stats: 448 MHz:0.00%, 673 MHz:0.00%, 897 MHz:0.00%, 1.12 GHz:0.00%, 1.35 GHz:0.00%, 1.57 GHz:0.00%, 1.79 GHz:100.00%

```
Here you go.

---

### Post by ahallubuntu on 2012-02-24
I think "capacity" means that the P4 version you have was available at up to 3GHZ.   I'm going to take a guess that you have a slow Northwood P4.  The fastest Northwood P4 with a 400MHZ FSB runs at 3GHZ, according to Wikipedia:

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

You may be able to overclock depending on your motherboard, but simply upgrading to a faster CPU may be fairly inexpensive and not very difficult.  I've upgraded a couple of Pentium 4 computers.  Recently I bought a 2.8GHZ Pentium 4 on eBay for $5 USD.  To upgrade, you must know the exact specs your motherboard can handle.  If it can handle only a 400MHZ FSB (Front Side Bus), your upgrade options are limited (many faster P4s run at 533MHZ or 800MHZ FSB), but you may still be able to find an inexpensive faster CPU.

What are the specs of your computer or motherboard?

---

### Post by roelforg on 2012-02-24
Adding the shipping costs...
I'd spend more on the CPU than the entire PC cost me (which i'm not planning to do).

LSHW:
```

ubuntu
    description: Desktop Computer
    product: Evo D310
    vendor: Compaq
    serial: 6S31LDBZE18M
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=BE625FCA-9169-D611-8858-37F16983501A
  *-core
       description: Motherboard
       product: 0804h
       vendor: Compaq
       physical id: 0
       serial: 6S31LDBZE18M
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686O2 v2.18
          date: 09/24/2002
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.1.2
          slot: XU1 PROCESSOR
          size: 1793MHz
          capacity: 3GHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 256KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: D1D266-064645I
             vendor: JEDEC ID:7F DA 00 00 00 00 00 00
             physical id: 0
             serial: 00000000
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: D1D266-064645I
             vendor: JEDEC ID:7F DA 00 00 00 00 00 00
             physical id: 1
             serial: 00000000
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 23
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:fc800000-fc87ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2440(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2460(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2480(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc880000-fc8803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:1000(size=4096) memory:fc200000-fc5fffff memory:fc900000-fcbfffff
           *-network:0
                description: Ethernet interface
                product: 82557/8/9/0/1 Ethernet Pro 100
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth0
                version: 05
                serial: 00:50:8b:6c:be:f7
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.115 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:16 memory:fc900000-fc900fff ioport:1440(size=32) memory:fc400000-fc4fffff memory:fca00000-fcafffff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth2
                version: 81
                serial: 00:0b:cd:09:e4:e0
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.103 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:fc500000-fc500fff ioport:1400(size=64)
           *-network:2
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@0000:05:09.0
                logical name: eth1
                version: 10
                serial: 00:50:fc:a3:e2:42
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.1 latency=66 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:1000(size=256) memory:fc501000-fc5010ff memory:fc910000-fc91ffff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
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
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:24c0(size=16) memory:40000000-400003ff
           *-disk:0
                description: ATA Disk
                product: Maxtor 6E040L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: NAR6
                serial: E16C9HPN
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b30f8
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d26ba15a-a741-416d-8eea-609b7145d840
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-23 20:29:35 filesystem=ext4 lastmountpoint=/ modified=2012-02-21 11:29:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-02-24 15:41:20 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 90MiB
                   capacity: 90MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 90MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 6E040L0
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: NAR6
                serial: E165XSYN
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=15881587
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /data
                   version: 1.0
                   serial: ddb6ee34-2b35-440d-84ef-e92ccada4498
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-12-23 20:11:50 filesystem=ext4 label=DATA_DISK lastmountpoint=/data modified=2012-02-23 18:28:31 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-02-23 15:01:21 state=mounted
           *-cdrom
                description: DVD reader
                product: DVD D  DH16D2P
                vendor: ATAPI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP56
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:2000(size=256) ioport:2400(size=64) memory:fc880400-fc8805ff memory:fc880600-fc8806ff


```

---

### Post by ahallubuntu on 2012-02-24
I don't think you can overclock very easily with a "brand name" computer like a Compaq/HP.  But the good news is, it looks like your Compaq will support a FSB up to 533MHZ, which is great.  That improves your upgrade options for a P4 a lot.  This shows you what Pentium 4 processors were available in the EVO D310:

[http://h18000.www1.hp.com/products/quickspecs/11348_div/11348_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11348_div/11348_div.HTML)

You'd want a Socket 478 NORTHWOOD (not Prescott) Pentium 4, with up to a 533MHZ FSB.

You could get up to a 3.06GHZ Pentium 4, but that's probably not going to be cheap.

As I said, I recently paid only $5.00 USD (including shipping) for a used P4 2.8GHZ.  That's a pretty cheap upgrade (4 Euros?) for you from 1.8GHZ to 2.8GHZ (and a faster FSB).

There are several versions of the Socket 478 Pentium 4 2.8GHZ 533MHZ, listed here (SL6HL, SL6K6, SL6PF, SL6QB, SL6S4).   (You want a NORTHWOOD and *NOT* a PRESCOTT P4 by the way!!!)  I got those part numbers here:

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

When I want to find one of these CPUs, I search eBay for the part number.  I just searched again and find SL6PF seems to be cheapest: about $6.00 USD in the US.  I assume you can search in Europe for cheaper shipping?  

The only things to watch out for: you might want to upgrade the BIOS to latest available from HP, before upgrading the CPU.  (You might have to do this in Windows or find a boot floppy to handle it - check HP's website.)   Also, the cooling fan on the CPU for a 1.8GHZ model may not be adequate for a 2.8GHZ model that generates more heat.  Then again, if you were able to overclock it, you'd have the same problem with more heat to worry about.  You can try it and see.

---

### Post by roelforg on 2012-02-25
> **ahallubuntu said:**
> I don't think you can overclock very easily with a "brand name" computer like a Compaq/HP.  But the good news is, it looks like your Compaq will support a FSB up to 533MHZ, which is great.  That improves your upgrade options for a P4 a lot.  This shows you what Pentium 4 processors were available in the EVO D310:

[http://h18000.www1.hp.com/products/quickspecs/11348_div/11348_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11348_div/11348_div.HTML)

You'd want a Socket 478 NORTHWOOD (not Prescott) Pentium 4, with up to a 533MHZ FSB.

You could get up to a 3.06GHZ Pentium 4, but that's probably not going to be cheap.

As I said, I recently paid only $5.00 USD (including shipping) for a used P4 2.8GHZ.  That's a pretty cheap upgrade (4 Euros?) for you from 1.8GHZ to 2.8GHZ (and a faster FSB).

There are several versions of the Socket 478 Pentium 4 2.8GHZ 533MHZ, listed here (SL6HL, SL6K6, SL6PF, SL6QB, SL6S4).   (You want a NORTHWOOD and *NOT* a PRESCOTT P4 by the way!!!)  I got those part numbers here:

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

When I want to find one of these CPUs, I search eBay for the part number.  I just searched again and find SL6PF seems to be cheapest: about $6.00 USD in the US.  I assume you can search in Europe for cheaper shipping?  

The only things to watch out for: you might want to upgrade the BIOS to latest available from HP, before upgrading the CPU.  (You might have to do this in Windows or find a boot floppy to handle it - check HP's website.)   Also, the cooling fan on the CPU for a 1.8GHZ model may not be adequate for a 2.8GHZ model that generates more heat.  Then again, if you were able to overclock it, you'd have the same problem with more heat to worry about.  You can try it and see.
Actually i just pulled parts from different PC's and made a new one (the mobo is from a Compaq, the mem from a different pc (brandless)).

Again, upgrading is not a viable option.
I paid 30 euros for the entire pc, and the CPU+shipping would be too expensive.

---

### Post by Rich2811 on 2012-02-25
its would defiantly a worth while and inexpensive upgrade. im currently slowly building/modifying a computer using socket 478. i upgraded from from a slow 2.0ghz celeron to a northwood 2.8 and the performance gains were very noticeable. although i later discovered through the terminal window that because of the motherboard i had it was restricting the clock speed to 2.1 but i was still having the gains of the upgraded cache and fsb speeds tho. meant that i now have swopped for a motherboard that can support the faster cpu and the clock speed now reads 2.8 and is even faster!
all i did was google the p/n on the motherboard and look at the spec and what it is capable of supporting

---

### Post by roelforg on 2012-02-25
> **Rich2811 said:**
> its would defiantly a worth while and inexpensive upgrade. im currently slowly building/modifying a computer using socket 478. i upgraded from from a slow 2.0ghz celeron to a northwood 2.8 and the performance gains were very noticeable. although i later discovered through the terminal window that because of the motherboard i had it was restricting the clock speed to 2.1 but i was still having the gains of the upgraded cache and fsb speeds tho. meant that i now have swopped for a motherboard that can support the faster cpu and the clock speed now reads 2.8 and is even faster!
all i did was google the p/n on the motherboard and look at the spec and what it is capable of supporting
My point being i'd rather not spend any money (my other pc's cost me exactly 0 euro, take the broken* pc's others give me and combine them in good working pc's),
i checked some stuff and it appears as if it should be possible to overclock it.

* I even once got a perfectly fine system whose only problem was that the dvd-drive never opens on the first try.

---

### Post by Yellow Pasque on 2012-02-25
Ok, so it appears you have a 1.8GHz Northwood (since Compaq Evo D310 was Socket 478). See: [http://www.sharkyextreme.com/guides/hwGuides/article.php/10709_1380951__1](http://www.sharkyextreme.com/guides/hwGuides/article.php/10709_1380951__1)

Don't expect 3GHz though. 2.4 is more reasonable.

---

### Post by roelforg on 2012-02-26
> **Temüjin said:**
> Ok, so it appears you have a 1.8GHz Northwood (since Compaq Evo D310 was Socket 478). See: [http://www.sharkyextreme.com/guides/hwGuides/article.php/10709_1380951__1](http://www.sharkyextreme.com/guides/hwGuides/article.php/10709_1380951__1)

Don't expect 3GHz though. 2.4 is more reasonable.
I'll check the guide out!
Yes, i know 3ghz is maybe to much for this old mobo/cpu but the 2.4 is a good improvement too!

My homeserver runs at 2Ghz on it's own, then again, it has a celeron proc.

---

### Post by roelforg on 2012-02-26
After reading the first part of the guide i found out that my system can't handle it. :(
It would overheat.
And the PSU isn't strong enough.

---

