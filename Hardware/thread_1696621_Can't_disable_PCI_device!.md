---
title: "Can't disable PCI device!"
date: 2011-02-27
forum: Hardware
---

### Post by xdominex on 2011-02-27
Hello,
I've been trying very hard to find a way to disable my ATI graphics card so that my laptop will boot up with it powered off. I have a hybrid-graphics laptop (HP tm2t-1100 CTO), and Ubuntu uses the intel integrated graphics by default, anyway. The second card just sucks power, heats up the laptop, and confuses the machine.

The first thing I tried was to put a nice
```
echo OFF > switch /sys/kernel/debug/vgaswitcheroo
```in the /etc/rc.local file, but that didn't do jack squat no matter who the owner of the the vgaswitcheroo directory was or anything.

This is the second method I tried, and it simply had no results whatsover:
[http://www.ehow.com/how_6885724_disable-linux-pci-device.html](http://www.ehow.com/how_6885724_disable-linux-pci-device.html)

However, no matter what I tried for the name of the graphics device, it would still load and power on!
Here are my outputs for lspci and lshw:

```
mgodby@godby-tablet:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (rev ff)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] (rev ff)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
mgodby@godby-tablet:~$ 

``````

mgodby@godby-tablet:~$ sudo lshw
godby-tablet              
    description: Notebook
    product: HP TouchSmart tm2 Notebook PC
    vendor: Hewlett-Packard
    version: 0489200000252A20001220000
    serial: CNU0431R9X
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=8E82BA9B-BA9B-AB22-E6B4-9CA9C71D8D30
  *-core
       description: Motherboard
       product: 1486
       vendor: Hewlett-Packard
       physical id: 0
       version: 83.1F
       serial: PBMXN00QEZM00S
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.23 (10/28/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron
             physical id: 0
             serial: E945DBE4
             slot: Bottom-Slot 1 (left)
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 16JSF51264HZ-1G4D1
             vendor: Micron
             physical id: 1
             serial: E65EFEFD
             slot: Bottom-Slot 2 (right)
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       U 430  @ 1.20GHz
          vendor: Intel Corp.
          physical id: 18
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       U 430  @ 1.20GHz
          slot: CPU
          size: 666MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 19
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 1b
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 1c
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 1a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:c4400000-c44fffff ioport:a0000000(size=268435456)
           *-generic:0
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:47 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
           *-generic:1
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=HDA Intel latency=255 maxlatency=255 mingnt=255
                resources: irq:49 memory:c4420000-c4423fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:c4506100-c450610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c4505c00-c4505fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:48 memory:c4500000-c4503fff
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
             resources: irq:41 ioport:2000(size=4096) memory:c3400000-c43fffff ioport:c0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 1c:c1:de:b7:7f:c7
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:43 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:c2400000-c33fffff ioport:c1400000(size=16777216)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:26:c7:b2:ae:aa
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=128.50.3.1 build 13488 ip=192.168.1.137 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 memory:c2400000-c2401fff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:c4505800-c4505bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:4048(size=8) ioport:405c(size=4) ioport:4040(size=8) ioport:4058(size=4) ioport:4020(size=32) memory:c4505000-c45057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS72505
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PC4O
                serial: 100910PCK400VLKBWBRJ
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000af32
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: eab7-275a
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-02-01 18:25:37 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 7cff7677-c741-bd44-8ab1-c7ba622a3e43
                   size: 344GiB
                   capacity: 344GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-02-01 18:25:40 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 60c62f16-4c20-4e80-bb4b-df4b904d01cc
                   size: 121GiB
                   capacity: 121GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-02-26 15:38:11 filesystem=ext4 lastmountpoint=/&#65533;<&#1288;&#65533;&#65533;&#65533;{&#65533;@R&#1288;&#65533;&#65533;&#65533;Q&#1096;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#1288;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-02-26 16:14:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-27 15:15:47 state=mounted
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
             resources: memory:c4506000-c45060ff ioport:4000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:21 memory:c4504000-c4504fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
  *-battery
       product: LU06062
       vendor: Dynapack
       physical id: 1
       slot: Primary
       capacity: 62160mWh
       configuration: voltage=11.1V
mgodby@godby-tablet:~$ 

```After that, I decided to try something else. I pulled up the page linked below this paragraph and began following the instructions for the section marked "Script for use during bootup."
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

When I got to the point where I am supposed to type "initramfs-tools -c -k all," though, terminal returned "command not found: initramfs-tools." Here is the code:
```
mgodby@godby-tablet:~$ initramfs-tools -c -k all
initramfs-tools: command not found
mgodby@godby-tablet:~$ sudo initramfs-tools -c -k all
sudo: initramfs-tools: command not found
mgodby@godby-tablet:~$ 

```Another method I wanted to try is the section headlined "Script for use inside an X session" on this page:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

There is no "exit 0 line in this file, though. Did the page writer perhaps mean /etc/rc.local instead of /etc/init.d/rc.local?

Please help me! I don't know why so many other people who have this computer seem to have great success with the first method while I have no success with ANY method, but surely someone has a solution!

Thank you sooo much in advance, guys!
Matthew Godby

---

### Post by xdominex on 2011-02-27
Nevermind; I got it finally!

---

### Post by weiteh on 2011-03-01
may I ask how you got through the problem with 'command not found: initramfs-tools'? I am running into the exact same problem while trying to disable my ATI discrete card running in Lucid (10.04LTS).

---

### Post by sean.leber on 2011-05-16
I too am suffering from the same problem, please let us know what you did!

---

