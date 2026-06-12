---
title: "Computer randomly turns off"
date: 2015-11-08
forum: Hardware
---

### Post by xubuntu84 on 2015-11-08
Hello,

Recently my computer will randomly turn off. This morning after waking up, I discovered the power light and HDD activity lights were off (two left lights on the following picture), but the fan indication lights (5 lights on the right) were on, indicating the motherboard is off but power supply still on.; see this picture: [IMG]http://images17.newegg.com/is/image/newegg/11-146-068-V01?$S640$[/IMG]

I had to turn the PS switch off, wait for lights on motherboard to go out (Intel DP55KG), and then turn on the PS switch, and finally the power button on the case. It booted fine, and I was able to use the computer again.

A couple hours later, the computer was completely off (no power lights for fans). Again, the power button on top did not work, so I cycled the PS switch, then turned it on. Also, on a possibly related note, every few minutes my monitor will go black for roughly 3 seconds, as if the graphics card is turning off and then back on. During this time, the power button on the monitor stays lit, so I think it is a loss of input signal. One more thing, when the computer boots and I enter my user's password to login, the desktop background is a jumble of black and white blocks, and there are stacks upon stacks of "System problem detected." After about a minute, the desktop wallpaper is shown, and I just cancel all the problem boxes. This issue has been going on for several months, see this picture:

[https://goo.gl/photos/ymMd8oZjcwJfgQz58](https://goo.gl/photos/ymMd8oZjcwJfgQz58)

I tried looking through kern.log, but nothing was logged around the time it would have turned off. What logs should I look at and/or post here for help from the community?  I'll post output of uname, lscpci, lshw, and dmidecode below.

I don't know what path to go down for troubleshooting. Is it a PS issue, graphics card issue, or something with the OS?

Thank you for reading this post, and for hopefully shedding some light!!

Ben

uname:
```

benmctee@xubuntu-server:~$ uname -a
Linux xubuntu-server 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

lspci:
```

benmctee@xubuntu-server:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX / 9800 GTX+] (rev a2)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6145 SATA II PCI-E controller (rev a1)
04:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

lshw:
```

benmctee@xubuntu-server:~$ sudo lshw
xubuntu-server            
    description: Computer
    product: ()
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal uuid=FD640A56-016F-11DF-88EA-00112550A074
  *-core
       description: Motherboard
       product: DP55KG
       vendor: Intel Corporation
       physical id: 0
       version: AAE47218-405
       serial: AZKG003000SJ
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz
          slot: LGA 1156
          size: 1199MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L3 cache
             physical id: 1
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 4
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 5
          version: KGIBX10J.86A.5893.2010.1116.0001
          date: 11/16/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: 9905471-006.A01LF
             vendor: AMD
             physical id: 0
             serial: 0x6B0ED1FE
             slot: J1MY
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: OCZ3P1600LV2G
             vendor: 0x84B0
             physical id: 1
             serial: 0x00000000
             slot: J2MY
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: 9905471-006.A01LF
             vendor: AMD
             physical id: 2
             serial: 0x6A0E8FD0
             slot: J3MY
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: OCZ3P1600LV2G
             vendor: 0x84B0
             physical id: 3
             serial: 0x00000000
             slot: J4MY
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:2000(size=4096) memory:f0000000-f2ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9800 GTX / 9800 GTX+]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:49 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:2000(size=128)
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82578DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: 00:27:0e:1b:3b:ff
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.12-5 ip=10.0.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:47 memory:f3200000-f321ffff memory:f3224000-f3224fff ioport:3020(size=32)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f3302000-f33023ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f3220000-f3223fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:4000(size=4096) memory:f3400000-f35fffff ioport:f3600000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:1000(size=4096) memory:f3100000-f31fffff ioport:f3800000(size=1048576)
           *-ide
                description: IDE interface
                product: 88SE6145 SATA II PCI-E controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom
                configuration: driver=pata_marvell latency=0 mingnt=8
                resources: irq:19 ioport:1018(size=8) ioport:1024(size=4) ioport:1010(size=8) ioport:1020(size=4) ioport:1000(size=16) memory:f3100000-f31003ff memory:f3800000-f383ffff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f3225000-f32253ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f3000000-f30fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:04:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:19 memory:f3004000-f30047ff memory:f3000000-f3003fff
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3098(size=8) ioport:30ac(size=4) ioport:3090(size=8) ioport:30a8(size=4) ioport:3070(size=16) ioport:3060(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f3303000-f33030ff ioport:3000(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3088(size=8) ioport:30a4(size=4) ioport:3080(size=8) ioport:30a0(size=4) ioport:3050(size=16) ioport:3040(size=16)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=i7core_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:3f:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:3f:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:3f:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:3f:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:3f:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:3f:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:3f:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:3f:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:3f:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD20EZRX-00D
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: 80.0
             serial: WD-WMC4M1647998
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000de414
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 4a8ba465-0a4b-4b7a-b3ed-d3fb5c4b52af
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-25 23:42:14 filesystem=ext4 modified=2014-11-25 23:42:14 state=clean
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 51.0
             serial: WD-WMAZA0745783
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=81a6fd5b
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 71b1c6ed-5f13-4a99-aaba-83d25f975edc
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-25 23:42:24 filesystem=ext4 modified=2014-11-25 23:42:24 state=clean
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sdc
             version: 51.0
             serial: WD-WMAZA0447336
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000d7096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.1.0,1
                logical name: /dev/sdc1
                version: 1.0
                serial: c42bce96-4569-46bf-b34f-b21be2f3615d
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-25 23:42:36 filesystem=ext4 modified=2014-11-25 23:42:36 state=clean
     *-scsi:2
          physical id: 4
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-RW   BDR-205
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.08
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:3
          physical id: 6
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD20EZRX-00D
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 80.0
             serial: WD-WCC4ML56HT90
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000c69a9
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                version: 1.0
                serial: 3e895401-13a3-498f-a15c-69e3ee8788dd
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-25 23:42:46 filesystem=ext4 modified=2014-11-25 23:42:46 state=clean
     *-scsi:4
          physical id: 7
          logical name: scsi5
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: ST3250318AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sde
             version: CC38
             serial: 9VMKJGRW
             size: 232GiB (250GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=cdd2f29f-864d-4adc-9b31-ea4224270851 sectorsize=512
           *-volume:0
                description: Linux swap volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sde1
                version: 1
                serial: f271aec8-6337-4d13-b296-ed30d0e56da0
                size: 3904MiB
                capacity: 3904MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sde2
                logical name: /
                version: 1.0
                serial: c8428ebf-d359-41af-91b5-abaec4867d38
                size: 229GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-04-29 18:01:49 filesystem=ext4 lastmountpoint=/ modified=2015-11-08 15:14:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-11-08 15:14:12 state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/sdf
             version: 51.0
             serial: WD-WMAZA0747797
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00052a78
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.1.0,1
                logical name: /dev/sdf1
                version: 1.0
                serial: 8d55241f-80ee-47a9-b6f9-5e52b8b1f7b7
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-25 23:42:55 filesystem=ext4 modified=2014-11-25 23:42:56 state=clean

```

dmidecode:
```

benmctee@xubuntu-server:~$ sudo dmidecode
# dmidecode 2.12
SMBIOS 2.6 present.
36 structures occupying 1910 bytes.
Table at 0x000EB040.

Handle 0x0000, DMI type 4, 42 bytes
Processor Information
    Socket Designation: LGA 1156
    Type: Central Processor
    Family: Core i7
    Manufacturer: Intel(R) Corporation
    ID: E5 06 01 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 30, Stepping 5
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz
    Voltage: 1.1 V
    External Clock: 133 MHz
    Max Speed: 4000 MHz
    Current Speed: 2801 MHz
    Status: Populated, Enabled
    Upgrade: Socket LGA1156
    L1 Cache Handle: 0x0004
    L2 Cache Handle: 0x0003
    L3 Cache Handle: 0x0001
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 8192 kB
    Maximum Size: 8192 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0003, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 4-way Set-associative

Handle 0x0005, DMI type 0, 24 bytes
BIOS Information
    Vendor: Intel Corp.
    Version: KGIBX10J.86A.5893.2010.1116.0001
    Release Date: 11/16/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 0.0
    Firmware Revision: 0.0

Handle 0x0006, DMI type 1, 27 bytes
System Information
    Manufacturer:                                 
    Product Name:                                 
    Version:                         
    Serial Number:                                 
    UUID: 560A64FD-6F01-DF11-88EA-00112550A074
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family: Not Specified

Handle 0x0007, DMI type 2, 20 bytes
Base Board Information
    Manufacturer: Intel Corporation
    Product Name: DP55KG
    Version: AAE47218-405
    Serial Number: AZKG003000SJ
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0008
    Type: Unknown
    Contained Object Handles: 0

Handle 0x0008, DMI type 3, 21 bytes
Chassis Information
    Manufacturer:                                 
    Type: Unknown
    Lock: Not Present
    Version:                         
    Serial Number:                                 
    Asset Tag:                                 
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Other
    Security Status: Other
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: Unspecified
    Contained Elements: 0

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ATX_PWR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X16 SLOT
    Type: x16 PCI Express 2
    Current Usage: In Use
    Length: Short
    ID: 7
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X8  SLOT
    Type: x8 PCI Express 2
    Current Usage: Available
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X4 SLOT
    Type: x4 PCI Express
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000F, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X1 SLOT 1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 5
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0010, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X1 SLOT 2
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 6
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0011, DMI type 9, 17 bytes
System Slot Information
    Designation: PCI SLOT 1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 3
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
    Designation: PCI SLOT 2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0013, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Intel(R) 82578DC Gigabit Network Connection

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Intel(R) High Definition Audio Device

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
    Type: SATA Controller
    Status: Enabled
    Description: Intel(R) SATA Controller 0

Handle 0x0016, DMI type 10, 6 bytes
On Board Device Information
    Type: SATA Controller
    Status: Enabled
    Description: Intel(R) SATA Controller 1

Handle 0x0017, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) 82578DC Gigabit Network Connection
    Type: Ethernet
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:19.0

Handle 0x0018, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) High Definition Audio Device
    Type: Sound
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:1b.0

Handle 0x0019, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) SATA Controller 0
    Type: SATA Controller
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:1f.2

Handle 0x001A, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) SATA Controller 1
    Type: SATA Controller
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:1f.5

Handle 0x001B, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 1
        enUS
    Currently Installed Language: enUS

Handle 0x001C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x001D, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001E, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x002FFFFFFFF
    Range Size: 12 GB
    Physical Array Handle: 0x001D
    Partition Width: 4

Handle 0x001F, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: J1MY
    Bank Locator: CHANNEL A DIMM 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x0198
    Serial Number: 0x6B0ED1FE
    Asset Tag: Unknown
    Part Number: 0x393930353437312D3030362E4130314C4620
    Rank: Unknown

Handle 0x0020, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J2MY
    Bank Locator: CHANNEL A DIMM 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x84B0
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x4F435A3350313630304C5632472020202020
    Rank: Unknown

Handle 0x0021, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: J3MY
    Bank Locator: CHANNEL B DIMM 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x0198
    Serial Number: 0x6A0E8FD0
    Asset Tag: Unknown
    Part Number: 0x393930353437312D3030362E4130314C4620
    Rank: Unknown

Handle 0x0022, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J4MY
    Bank Locator: CHANNEL B DIMM 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x84B0
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x4F435A3350313630304C5632472020202020
    Rank: Unknown

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

benmctee@xubuntu-server:~$ clear

benmctee@xubuntu-server:~$ sudo dmidecode
# dmidecode 2.12
SMBIOS 2.6 present.
36 structures occupying 1910 bytes.
Table at 0x000EB040.

Handle 0x0000, DMI type 4, 42 bytes
Processor Information
    Socket Designation: LGA 1156
    Type: Central Processor
    Family: Core i7
    Manufacturer: Intel(R) Corporation
    ID: E5 06 01 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 30, Stepping 5
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7 CPU         870  @ 2.93GHz
    Voltage: 1.1 V
    External Clock: 133 MHz
    Max Speed: 4000 MHz
    Current Speed: 2801 MHz
    Status: Populated, Enabled
    Upgrade: Socket LGA1156
    L1 Cache Handle: 0x0004
    L2 Cache Handle: 0x0003
    L3 Cache Handle: 0x0001
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 8192 kB
    Maximum Size: 8192 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0003, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 4-way Set-associative

Handle 0x0005, DMI type 0, 24 bytes
BIOS Information
    Vendor: Intel Corp.
    Version: KGIBX10J.86A.5893.2010.1116.0001
    Release Date: 11/16/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 0.0
    Firmware Revision: 0.0

Handle 0x0006, DMI type 1, 27 bytes
System Information
    Manufacturer:                                 
    Product Name:                                 
    Version:                         
    Serial Number:                                 
    UUID: 560A64FD-6F01-DF11-88EA-00112550A074
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family: Not Specified

Handle 0x0007, DMI type 2, 20 bytes
Base Board Information
    Manufacturer: Intel Corporation
    Product Name: DP55KG
    Version: AAE47218-405
    Serial Number: AZKG003000SJ
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0008
    Type: Unknown
    Contained Object Handles: 0

Handle 0x0008, DMI type 3, 21 bytes
Chassis Information
    Manufacturer:                                 
    Type: Unknown
    Lock: Not Present
    Version:                         
    Serial Number:                                 
    Asset Tag:                                 
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Other
    Security Status: Other
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: Unspecified
    Contained Elements: 0

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ATX_PWR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X16 SLOT
    Type: x16 PCI Express 2
    Current Usage: In Use
    Length: Short
    ID: 7
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X8  SLOT
    Type: x8 PCI Express 2
    Current Usage: Available
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X4 SLOT
    Type: x4 PCI Express
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
    Bus Address: 0000:00:00.0

Handle 0x000F, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X1 SLOT 1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 5
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0010, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIE X1 SLOT 2
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 6
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0011, DMI type 9, 17 bytes
System Slot Information
    Designation: PCI SLOT 1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 3
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
    Designation: PCI SLOT 2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        3.3 V is provided
        PME signal is supported
        SMBus signal is supported
    Bus Address: 0000:00:00.0

Handle 0x0013, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Intel(R) 82578DC Gigabit Network Connection

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Intel(R) High Definition Audio Device

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
    Type: SATA Controller
    Status: Enabled
    Description: Intel(R) SATA Controller 0

Handle 0x0016, DMI type 10, 6 bytes
On Board Device Information
    Type: SATA Controller
    Status: Enabled
    Description: Intel(R) SATA Controller 1

Handle 0x0017, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) 82578DC Gigabit Network Connection
    Type: Ethernet
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:19.0

Handle 0x0018, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) High Definition Audio Device
    Type: Sound
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:1b.0

Handle 0x0019, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) SATA Controller 0
    Type: SATA Controller
    Status: Enabled
    Type Instance: 0
    Bus Address: 0000:00:1f.2

Handle 0x001A, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Intel(R) SATA Controller 1
    Type: SATA Controller
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:1f.5

Handle 0x001B, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 1
        enUS
    Currently Installed Language: enUS

Handle 0x001C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x001D, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001E, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x002FFFFFFFF
    Range Size: 12 GB
    Physical Array Handle: 0x001D
    Partition Width: 4

Handle 0x001F, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: J1MY
    Bank Locator: CHANNEL A DIMM 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x0198
    Serial Number: 0x6B0ED1FE
    Asset Tag: Unknown
    Part Number: 0x393930353437312D3030362E4130314C4620
    Rank: Unknown

Handle 0x0020, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J2MY
    Bank Locator: CHANNEL A DIMM 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x84B0
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x4F435A3350313630304C5632472020202020
    Rank: Unknown

Handle 0x0021, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: J3MY
    Bank Locator: CHANNEL B DIMM 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x0198
    Serial Number: 0x6A0E8FD0
    Asset Tag: Unknown
    Part Number: 0x393930353437312D3030362E4130314C4620
    Rank: Unknown

Handle 0x0022, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: J4MY
    Bank Locator: CHANNEL B DIMM 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: 0x84B0
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x4F435A3350313630304C5632472020202020
    Rank: Unknown

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

```

---

### Post by weatherman2 on 2015-11-08
I'd guess failing power supply or failing motherboard.  Power supply is easiest to swap out and replace.

---

### Post by pqwoerituytrueiwoq on 2015-11-09
and on that note a bad PSU can take parts out with it (in particular non-reputable ones)
given how high end your system i hope you did not use some generic 20$ PSU
which driver is running that GeForce 9800? id probably go with one of the older series drivers in the software preferences for that card

make sure the GPU is properly seated in it's slot
run a memtest

---

### Post by xubuntu84 on 2015-11-10
> **weatherman2 said:**
> I'd guess failing power supply or failing motherboard.  Power supply is easiest to swap out and replace.

Thanks for the advice. That's kind of the path I was going to head down. Hopefully it's the PSU.

> **pqwoerituytrueiwoq said:**
> and on that note a bad PSU can take parts out with it (in particular non-reputable ones)
given how high end your system i hope you did not use some generic 20$ PSU which driver is running that GeForce 9800? id probably go with one of the older series drivers in the software preferences for that card make sure the GPU is properly seated in it's slot run a memtest

The PSU was a pretty decent unit when I bought it (Ultra X4 750W; U12-40504, not manufactured anymore). However, I live near the ocean in Hawaii and the salty air probably got to it, just like it does everything else we own. It's very likely that it or the motherboard is seeing premature failure.

I've tried reseating the GPU, and we'll see how that works out. Also, I'll research how to do the memtest and post back the results. As far as the current driver, I'm not sure how to tell if I'm using an older one, but I found [this post]("http://askubuntu.com/questions/28033/how-to-check-the-information-of-current-installed-video-drivers") that gives the following information:

```

benmctee@xubuntu-server:~$ lspci | grep VGA ; lsmod | grep "kms\|drm" ; find /dev -group video ; \
> cat /proc/cmdline ; find /etc/modprobe.d/; cat /etc/modprobe.d/*kms* ; \
> ls /etc/X11/xorg.conf ; glxinfo | grep -i "vendor\|rendering" ; \
> grep LoadModule /var/log/Xorg.0.log
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX / 9800 GTX+] (rev a2)
drm_kms_helper         55071  1 nouveau
drm                   303102  5 ttm,drm_kms_helper,nouveau
/dev/fb0
/dev/dri/card0
/dev/dri/controlD64
BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=c8428ebf-d359-41af-91b5-abaec4867d38 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
/etc/modprobe.d/
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/options.conf~
/etc/modprobe.d/mlx4.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/options.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/vmwgfx-fbdev.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/fbdev-blacklist.conf
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
ls: cannot access /etc/X11/xorg.conf: No such file or directory
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: nouveau
[    47.795] (II) LoadModule: "glx"
[    48.546] (II) LoadModule: "nvidia"
[    48.563] (II) LoadModule: "nouveau"
[    48.610] (II) LoadModule: "modesetting"
[    48.610] (II) LoadModule: "fbdev"
[    48.610] (II) LoadModule: "vesa"
[    48.610] (II) LoadModule: "nvidia"
[    48.610] (II) LoadModule: "nouveau"
[    48.611] (II) LoadModule: "modesetting"
[    48.611] (II) LoadModule: "fbdev"
[    48.611] (II) LoadModule: "vesa"
[    48.611] (II) LoadModule: "fbdevhw"
[    48.612] (II) LoadModule: "dri2"
[    48.977] (II) LoadModule: "fb"
[    48.978] (II) LoadModule: "shadowfb"
[    48.996] (II) LoadModule: "exa"
[    49.115] (II) LoadModule: "evdev"

```

Thanks for your help!
-Ben

---

### Post by xubuntu84 on 2015-11-11
So I didn't run memtest from GRUB yet, because I want to see if the computer turns off after reseating the graphics card, but I did run memtester, and got the following results:

```


benmctee@xubuntu-server:~$ sudo memtester 10246M
memtester version 4.3.0 (64-bit)
Copyright (C) 2001-2012 Charles Cazabon.
Licensed under the GNU General Public License version 2 (only).

pagesize is 4096
pagesizemask is 0xfffffffffffff000
want 10246MB (10743709696 bytes)
got  10246MB (10743709696 bytes), trying mlock ...locked.
Loop 1:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : testing   0FAILURE: 0xaaaaaaaaaaaaaaaa != 0xaaaaaaaaaa8aaaaa at offset 0x6e58d7b8.
  Bit Spread          : testing   0FAILURE: 0xfffffffffffffffa != 0xffffffffffdffffa at offset 0x6e58d7b8.
  Bit Flip            : testing   1FAILURE: 0xfffffffffffffffe != 0xffffffffffdffffe at offset 0x6e58d7b8.
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Loop 2:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : testing  11FAILURE: 0xffffffffffffffff != 0xffffffffffdfffff at offset 0x6e58d7b8.
  Block Sequential    : ok         
  Checkerboard        : testing   0FAILURE: 0xaaaaaaaaaaaaaaaa != 0xaaaaaaaaaa8aaaaa at offset 0x6e58d7b8.
  Bit Spread          : testing   0FAILURE: 0xfffffffffffffffa != 0xffffffffffdffffa at offset 0x6e58d7b8.
  Bit Flip            : testing   1FAILURE: 0xfffffffffffffffe != 0xffffffffffdffffe at offset 0x6e58d7b8.
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : \FAILURE: 0xbffc5baa7f7f09ad != 0xbffc5baa7f5f09ad at offset 0x6e58d7b8.
  16-bit Writes       : ok


```

It looks like I have a bad block at 0x6e58d7b8, but what does this tell me? If it's anything like a HDD, I would assume the OS would recognize it as bad and choose not to use it. But I'm not nearly as educated on memory as I am with hard drives.

---

### Post by pqwoerituytrueiwoq on 2015-11-11
any failure on ram means it is bad and should be replaced
try to figure out which stick is bad and remove it and look for a replacement
a  bad memory stick can do about anything depending on how bad it is
* most ram has a lifetime warranty

underclocking the ram may get it to pass

also make sure you can get ram to pass in the slot the bad stick is found in

---

