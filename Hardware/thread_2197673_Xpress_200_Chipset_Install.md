---
title: "Xpress 200 Chipset Install"
date: 2014-01-04
forum: Hardware
---

### Post by rwfisher1 on 2014-01-04
Hi all.  I am not a complete noob here, but I've run into a roadblock that I'm hoping someone can help with.

A friend of mine asked if I could resurrect his old HP Pavilion a1130e with Ubuntu.  I told him I'd give it a shot.  I've installed Ubuntu on about a dozen different machines with only minor problems.  However this one has me completely stumped.

This particular machine has an HP OEM motherboard ([specs here]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c00496280")) using an ATI Xpress 200 chipset.

I'm trying to install 13.10 64-bit.  I've also tried 12.04 64-bit and 32-bit with the same results.  The initial boot to the live CD or live USB is flawless.  However, any attempt to enumerate the storage hardware causes the process to hang.  For instance, running lshw results in the process hanging at "SCSI".  Running GParted, fdisk -l, or the install program results in a hung process.

I looked at syslog and it shows several repeating errors related to the SATA ports:
```
Jan  4 21:51:14 ubuntu kernel: [ 1410.520223] ata2.00: status: { DRDY }
Jan  4 21:51:14 ubuntu kernel: [ 1410.520235] ata2: hard resetting link
Jan  4 21:51:14 ubuntu kernel: [ 1410.840217] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  4 21:51:14 ubuntu kernel: [ 1410.856453] ata2.00: configured for UDMA/33
Jan  4 21:51:14 ubuntu kernel: [ 1410.856463] ata2.00: device reported invalid CHS sector 0
Jan  4 21:51:14 ubuntu kernel: [ 1410.856475] ata2: EH complete
Jan  4 21:51:45 ubuntu kernel: [ 1441.498102] ata2: lost interrupt (Status 0x50)
Jan  4 21:51:45 ubuntu kernel: [ 1441.498140] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  4 21:51:45 ubuntu kernel: [ 1441.498147] ata2.00: failed command: READ DMA
Jan  4 21:51:45 ubuntu kernel: [ 1441.498154] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan  4 21:51:45 ubuntu kernel: [ 1441.498154]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan  4 21:51:45 ubuntu kernel: [ 1441.498157] ata2.00: status: { DRDY }
Jan  4 21:51:45 ubuntu kernel: [ 1441.498169] ata2: hard resetting link
Jan  4 21:51:45 ubuntu kernel: [ 1441.818155] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  4 21:51:45 ubuntu kernel: [ 1441.834389] ata2.00: configured for UDMA/33
Jan  4 21:51:45 ubuntu kernel: [ 1441.834399] ata2.00: device reported invalid CHS sector 0
Jan  4 21:51:45 ubuntu kernel: [ 1441.834413] ata2: EH complete

```

Here's the output of lspci:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 200 Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)

```

Output of df [note that /dev/sdb is not shown]:
```
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow             1250020  25536   1224484   3% /
udev             1238976      4   1238972   1% /dev
tmpfs             250008    836    249172   1% /run
/dev/sda1       30849024 908304  29940720   3% /cdrom
/dev/loop0        862976 862976         0 100% /rofs
none                   4      0         4   0% /sys/fs/cgroup
tmpfs            1250020     56   1249964   1% /tmp
none                5120      0      5120   0% /run/lock
none             1250020     76   1249944   1% /run/shm
none              102400     48    102352   1% /run/user

```

Output of lshw -disable scsi [since it hangs on scsi]:
```

ubuntu
    description: Desktop Computer
    product: PY196AV-ABA a1130e ()
    vendor: HP Pavilion 061
    version: 0qm1211CT101AMBEM00
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00ECAA36-FCA2-1010-A001-941CD7AF627C
  *-core
       description: Motherboard
       product: Amberine M
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.03
       serial: MB-1234567890
     *-firmware:0
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.08
          date: 09/13/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3200+
          slot: Socket 939
          size: 2GHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-cpu:1 DISABLED
          description: CPU
          physical id: 5
          bus info: cpu@1
          slot: Socket 939
     *-firmware:1
          description: BIOS
          physical id: 2000
          size: 1MiB
          capacity: 1536KiB
          capabilities: socketedrom pcmciaboot int5printscreen
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RC4xx/RS4xx PCI Bridge [int gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fde00000-fdefffff ioport:d8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:d8000000-dfffffff ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff
        *-ide:0
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
             resources: irq:11 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f1ff memory:a0000000-a007ffff
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
             resources: irq:19 memory:fe02e000-fe02efff
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
             resources: irq:19 memory:fe02d000-fe02dfff
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
             resources: irq:19 memory:fe02c000-fe02cfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:fe02b000-fe02b3ff
        *-ide:1
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
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
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
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:d000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d4:d4:ed:5d
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:10 ioport:dc00(size=256) memory:fddff000-fddff0ff
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: LSI Corporation
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
                resources: memory:fddfe000-fddfe0ff ioport:df00(size=8) ioport:da00(size=256)
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

```

I'm fairly certain the hard drive itself is OK since it was running XP just fine prior to attempting the Ubuntu install.  I also ran e2fsck and it found no errors.

I did a lot of searching on the forums and it seems that most people have no trouble getting the Xpress 200 chipsets to work with Ubuntu.  Any help you can provide would be greatly appreciated.

Thank you!
Robert

---

### Post by pme 72 on 2014-01-05
My Compaq had the same motherboard but with the 3500+ processor. There was an issue with Hardy Heron 8.04 that required a workaround for the Xpress200 that I think involved temporarily disabling Compiz and subsequently installing the proprietary ATI fglrx driver. Intrepid 8.10 installed without issue with the default open source Radeon driver but since then I have had a dedicated vga in the PCIe slot for all installations. My notes show I checked the performance of the Xpress 200 with my 12.04 32-bit installation and found that Unity seemed to struggle and there was an issue with resuming from Suspend that seemed to plague the Xpress 200 off and on in various distributions. Wish I could be more help but I got hooked on the game SuperTuxKart which ran better with a stronger video card.

---

### Post by rwfisher1 on 2014-01-05
pme 72: Thanks for the insight!

I finally found a solution after grinding away on this for 3 days.  I still don't know what the root cause was, but I found a BIOS update for the A8AE-LE motherboard on HP's site that took me from version 3.08 to 3.15.  Of course HP's BIOS updater only works on Windows XP or higher, so I installed Windows XP on the machine (fast forward 45 minutes)....only to find out that for some reason their BIOS updater really doesn't work at all (it crashed every time I tried to use it).  So then I extracted the BIOS binary image and used a DOS boot disk to flash the image with AWDFLASH.exe (Award Bios flasher for DOS).  After doing this, I booted to the Ubuntu live USB and magically everything worked.  The disk access problem was fixed and the network adapter stopped dropping every minute.

Now I've got this 8 year old machine humming!  Or...at least groaning!

Looks like we can mark this one as solved.

Thanks all!

---

### Post by mörgæs on 2014-01-05
> **rwfisher1 said:**
> 
Looks like we can mark this one as solved.


Good, please do (using 'thread tools'). 

If you want a faster system you could try Lubuntu.

---

