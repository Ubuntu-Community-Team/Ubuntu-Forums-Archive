---
title: "Won't Boot, Long Beep"
date: 2019-10-11
forum: Hardware
---

### Post by webmanoffesto on 2019-10-11
My laptop suddenly won't bootIt just gives one long, continuous beep


I ran Boot Rescue Disk

[URL="http://paste.ubuntu.com/p/BYpzcHrkNC"]http://paste.ubuntu.com/p/BYpzcHrkNC
[/URL]
Do you see anything in that which can help me to repair this problem?

---

### Post by CatKiller on 2019-10-12
[https://www.computerhope.com/beep.htm](https://www.computerhope.com/beep.htm)

---

### Post by Autodave on 2019-10-12
If it boots and runs from a USB or DVD, then it sounds like the hard drive has failed.

You *could* try re-installing the system: it is possible that you had a write failure to the disk that corrupted it.  But, more than likely, your HD is failing / has failed.

---

### Post by yancek on 2019-10-12
The page at the link below discusses the problem and gives some suggestions on efforts to make to repair (if possible) as it is likely hardware.

[https://smallbusiness.chron.com/long-continuous-beep-sound-mean-computer-79252.html](https://smallbusiness.chron.com/long-continuous-beep-sound-mean-computer-79252.html)

You don't indicate the type of hardware and different motherboards have different beep code meanings.  The page at the link below gives some information on that so check to see if your hardware is listed.

[https://www.computerhope.com/beep.htm](https://www.computerhope.com/beep.htm)

---

### Post by webmanoffesto on 2019-10-12
I'm now booting off a flash drive and running Ubuuntu 18 to diagnose the failing laptop.

> **yancek said:**
>  You don't indicate the type of hardware and different motherboards have different beep code meanings.  The page at the link below gives some information on that so check to see if your hardware is listed.

I assume this is the item I'm concerned with. Does this give any indication of health or failure?

```

  *-scsi:0
          physical id: 6
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: S2RENXAH302583Z
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0002d4c2
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: d1dc2540-fc44-47dc-a749-88e08be90b00
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-01-09 18:04:17 filesystem=ext4 lastmountpoint=/mnt/boot-sav/sda1 modified=2019-10-12 00:07:12 mounted=2019-10-12 00:07:12 state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 670d08f8-498c-4ac5-ad0b-eddf64dc8534
                size: 880GiB
                capacity: 880GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-01-09 18:04:17 filesystem=ext4 lastmountpoint=/home modified=2019-10-12 00:07:12 mounted=2019-10-12 00:07:12 state=clean
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f2c26c25-ac0d-46c7-af3a-21fafebb01ff
                size: 31GiB
                capacity: 31GiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096



```

Further Hardware details

lspci
```
[COLOR=#8AE234]**ubuntu@ubuntu**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445] (rev 83)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)

```

lshw
```

ubuntu@ubuntu:~$ sudo lshw
ubuntu                      
    description: Notebook
    product: HP ProBook 450 G3 (Y6E48UT#ABA)
    vendor: HP
    serial: 5CD63927Q3
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=PRO frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=Y6E48UT#ABA uuid=2441BB6B-CB85-E611-A34F-72ACB9008055
  *-core
       description: Motherboard
       product: 8101
       vendor: HP
       physical id: 0
       version: KBC Version 40.60
       serial: PFXJK028J442IO
     *-cache:0
          description: L1 cache
          physical id: 0
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 1
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 2
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 3
          slot: L3 Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1355MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: CT8G4SFS8213.M8FB
             vendor: Unknown - [0x9B85]
             physical id: 0
             serial: E01F3AF0
             slot: Bottom-Slot 1(top)
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: M471A1K43BB0-CPB
             vendor: Samsung
             physical id: 1
             serial: 16A6F838
             slot: Bottom-Slot 2(under)
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-firmware
          description: BIOS
          vendor: HP
          physical id: b
          version: N78 Ver. 01.12
          date: 06/14/2016
          size: 64KiB
          capacity: 15MiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 520
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:128 memory:e1000000-e1ffffff memory:c0000000-cfffffff ioport:6000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:124 memory:e2400000-e240ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Cruzer
                   vendor: SanDisk
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi3
                   version: 1.02
                   serial: 200607752113C0F0A48B
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@3:0.0.0
                      logical name: /dev/sdb
                      version: 1.10
                      size: 29GiB (32GB)
                      capabilities: removable
                      configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         size: 29GiB (32GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=686a6515
                       *-volume:0
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sdb1
                            logical name: /isodevice
                            version: FAT32
                            serial: 7f5d-e59c
                            size: 28GiB
                            capacity: 28GiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=MULTISYSTEM mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
                       *-volume:1
                            description: EXT4 volume
                            vendor: Linux
                            physical id: 2
                            logical name: /dev/sdb2
                            version: 1.0
                            serial: eb47bc29-aa23-4b83-a52e-543930de014c
                            size: 1023MiB
                            capacity: 1023MiB
                            capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                            configuration: created=2018-11-16 18:10:05 filesystem=ext4 label=Tom modified=2019-10-12 00:05:33 mounted=2019-10-12 00:00:43 state=clean
              *-usb:1
                   description: Video
                   product: HP HD Camera
                   vendor: DETNR019I39196
                   physical id: 6
                   bus info: usb@1:6
                   version: 0.09
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:e242a000-e242afff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:130 memory:e242b000-e242bfff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:e2428000-e2429fff memory:e242e000-e242e0ff ioport:6080(size=8) ioport:6088(size=4) ioport:6040(size=32) memory:e242c000-e242c7ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:120 ioport:3000(size=4096) memory:e2000000-e20fffff ioport:d0000000(size=270532608)
           *-display
                description: Display controller
                product: Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 83
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:129 memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:3000(size=256) memory:e2000000-e203ffff memory:e2040000-e205ffff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:4000(size=4096) memory:e2100000-e21fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 15
                serial: 98:e7:f4:5e:1f:3a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:16 ioport:4000(size=256) memory:e2104000-e2104fff memory:e2100000-e2103fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:5000(size=4096) memory:e2200000-e22fffff
           *-network
                description: Wireless interface
                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: 54:8c:a0:05:d8:53
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8188ee driverversion=4.15.0-29-generic firmware=N/A ip=192.168.1.164 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:132 ioport:5000(size=256) memory:e2200000-e2203fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:7000(size=4096) memory:e2300000-e23fffff ioport:be900000(size=2097152)
           *-generic
                description: Unassigned class
                product: RTS522A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:125 memory:e2300000-e2300fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:e2420000-e2423fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:131 memory:e2424000-e2427fff memory:e2410000-e241ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e242d000-e242d0ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 6
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: S2RENXAH302583Z
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0002d4c2
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: d1dc2540-fc44-47dc-a749-88e08be90b00
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-01-09 18:04:17 filesystem=ext4 lastmountpoint=/mnt/boot-sav/sda1 modified=2019-10-12 00:07:12 mounted=2019-10-12 00:07:12 state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 670d08f8-498c-4ac5-ad0b-eddf64dc8534
                size: 880GiB
                capacity: 880GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-01-09 18:04:17 filesystem=ext4 lastmountpoint=/home modified=2019-10-12 00:07:12 mounted=2019-10-12 00:07:12 state=clean
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f2c26c25-ac0d-46c7-af3a-21fafebb01ff
                size: 31GiB
                capacity: 31GiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 7
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  DU8A6SH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: RI04044
       vendor: 131-22-34
       physical id: 1
       slot: Primary
       capacity: 2950mWh
       configuration: voltage=14.8V
ubuntu@ubuntu:~$ 



```

---

### Post by oldfred on 2019-10-12
You have an UEFI system, but BIOS boot installs.
Are you sure you have system booting in BIOS mode, not UEFI?

If you updated UEFI/BIOS, it would reset to defaults and that would change boot mode.

---

### Post by Autodave on 2019-10-12
Seeing as how you can boot and run from the USB, your RAM obviously isn't the problem.  To me, you either have a failed HD or possibly a failed motherboard.

HDs are pretty cheap anynore: SSDs (120G) can be had for $20 and up depending on what size you want/need.

---

### Post by webmanoffesto on 2019-10-13
> **oldfred said:**
> If you updated UEFI/BIOS, it would reset to defaults and that would change boot mode.

What rescue disk would do this. I have Boot Repair Disk. I ran that, and it didn't help, but I don't really know what it did.

---

### Post by oldfred on 2019-10-13
To update UEFI, you typically have to go to the vendor's site & download an update file.
Some update using Windows, some update directly from within UEFI reading update file from a FAT32 partition, and some have you create a  DOS bootable FAT32 flash drive with the update file.

A few vendors now let you update from within Linux. HP only has a couple of new models on the list last time I looked.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)  
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

But many with HP have said UEFI update resolved some issues.
My desktop does not beep, but has a red LED that says boot error if I try to boot in wrong mode  or it cannot see correct boot device. (I have multiple installs on multiple drives and it gets confused sometimes).

---

### Post by jimmyrus on 2019-10-14
> **webmanoffesto said:**
> What rescue disk would do this. I have Boot Repair Disk. I ran that, and it didn't help, but I don't really know what it did.
It does sound like you've got a bad hard drive. You can at least maybe test this by just unplugging your hard drive, and see if the long-beep is still there. Might be since it
may be coming from bios about a missing or failed drive, but it might not. How old is the drive?  Getting a new one is cheap these days and going from the rotating disk
you have now to an ssd will help your laptop run a ton cooler and a lot faster too. Grab a new ssd and a cheapey usb enclosure for your old hard drive. Reinstall
on the ssd and plug the old drive in usb when your back up to see if you can access it. Otherwise, you still have a faster working system with all your file and a nice new
1tb external usb drive.

---

### Post by webmanoffesto on 2019-10-15
> **jimmyrus said:**
> It does sound like you've got a bad hard drive.

While booting off a flash drive I can navigate to my HD and open and save documents to it /media/ubuntu/670d08f8-498c-4ac5-ad0b-eddf64dc8534/tom/Documents
So I guess it's still working, or at least that partition.
I can also see folders on the Linux partition /media/ubuntu/d1dc2540-fc44-47dc-a749-88e08be90b00

---

### Post by webmanoffesto on 2019-10-15
> **oldfred said:**
> If you updated UEFI/BIOS, it would reset to defaults and that would change boot mode.
Thank you OldFred. I was able to get to the Boot Menu, plug in to a wired LAN, and get to "System BIOS Update". Now my laptop seems to work just fine.

---

