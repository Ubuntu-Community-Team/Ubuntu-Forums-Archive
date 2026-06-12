---
title: "problem with cpu speed control"
date: 2011-01-25
forum: Hardware
---

### Post by qwertyjjj on 2011-01-25
I installed the applet panel for cpufreq but I am having a problem controlling the CPU speed - it just seems to be permanently stuck on 800MHz when it should rotate between that and the full speed of 1.73.
Sometimes after restarting, I see it flipping between 800, 1.07, 1.33 and 1.73 but then it randomly stops. It's almost like the Intel speedswitch isn't working. FWIW, I had the same issue when XP was installed before.

Any ideas on what I can do?
Computer info. below:

```

j@j-Inspiron-9300:~$ sudo dmidecode|grep "Current Speed"
[sudo] password for j:
Current Speed: 800 MHz
j@j-Inspiron-9300:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 13
model name : Intel(R) Pentium(R) M processor 1.73GHz
stepping : 8
cpu MHz : 800.000
cache size : 2048 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips : 1596.64
clflush size : 64
cache_alignment : 64
address sizes : 32 bits physical, 32 bits virtual
power management:

j@j-Inspiron-9300:~$ sudo lshw
j-inspiron-9300
description: Portable Computer
product: Inspiron 9300
vendor: Dell Inc.
serial: 2TJ2Z1J
width: 32 bits
capabilities: smbios-2.3 dmi-2.3
configuration: boot=normal chassis=portable uuid=44454C4C-5400-104A-8032-B2C04F5A314A
*-core
description: Motherboard
product: 0C5668
vendor: Dell Inc.
physical id: 0
serial: .2TJ2Z1J.CN129615AJ3266.
*-firmware
description: BIOS
vendor: Dell Inc.
physical id: 0
version: A05 (09/19/2005)
size: 64KiB
capacity: 512KiB
capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
*-cpu
description: CPU
product: Intel(R) Pentium(R) M processor 1.73GHz
vendor: Intel Corp.
physical id: 400
bus info: cpu@0
version: 6.13.8
slot: Microprocessor
size: 800MHz
capacity: 1800MHz
width: 32 bits
clock: 133MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
*-cache:0
description: L1 cache
physical id: 700
size: 8KiB
capacity: 8KiB
capabilities: internal write-back data
*-cache:1
description: L2 cache
physical id: 701
size: 2MiB
capacity: 2MiB
clock: 66MHz (15.0ns)
capabilities: pipeline-burst internal varies unified
*-memory
description: System Memory
physical id: 1000
slot: System board or motherboard
size: 2GiB
*-bank:0
description: DIMM DDR Synchronous 667 MHz (1.5 ns)
vendor: 7F7F7F7F7F9B0000
physical id: 0
serial: D34253B9
slot: DIMM_A
size: 1GiB
width: 64 bits
clock: 667MHz (1.5ns)
*-bank:1
description: DIMM DDR Synchronous 667 MHz (1.5 ns)
vendor: 7F7F7F7F7F9B0000
physical id: 1
serial: D435CD3D
slot: DIMM_B
size: 1GiB
width: 64 bits
clock: 667MHz (1.5ns)
*-pci
description: Host bridge
product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 03
width: 32 bits
clock: 33MHz
*-pci:0
description: PCI bridge
product: Mobile 915GM/PM Express PCI Express Root Port
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:40 ioport:d000(size=4096) memory:dfd00000-dfefffff memory:d0000000-d7ffffff
*-display
description: VGA compatible controller
product: M22 [Mobility Radeon X300]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:41 memory:d0000000-d7ffffff ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff
*-usb:0
description: USB Controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: irq:16 ioport:bf80(size=32)
*-usb:1
description: USB Controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
vendor: Intel Corporation
physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: irq:17 ioport:bf60(size=32)
*-usb:2
description: USB Controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 03
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: irq:18 ioport:bf40(size=32)
*-usb:3
description: USB Controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
vendor: Intel Corporation
physical id: 1d.3
bus info: pci@0000:00:1d.3
version: 03
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: irq:19 ioport:bf20(size=32)
*-usb:4
description: USB Controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
vendor: Intel Corporation
physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
resources: irq:16 memory:ffa80800-ffa80bff
*-pci:1
description: PCI bridge
product: 82801 Mobile PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: d3
width: 32 bits
clock: 33MHz
capabilities: pci subtractive_decode bus_master cap_list
resources: ioport:2000(size=4096) memory:dfc00000-dfcfffff ioport:80000000(size=67108864)
*-network:0
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:14:22:de:03:0d
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
resources: irq:18 memory:dfcfe000-dfcfffff
*-pcmcia
description: CardBus bridge
product: RL5c476 II
vendor: Ricoh Co Ltd
physical id: 1
bus info: pci@0000:03:01.0
version: b3
width: 64 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
resources: iomemory:b00704030-b0070402f irq:19 memory:dfc00000-dfc00fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff memory:84000000-87ffffff
*-firewire
description: FireWire (IEEE 1394)
product: R5C552 IEEE 1394 Controller
vendor: Ricoh Co Ltd
physical id: 1.1
bus info: pci@0000:03:01.1
version: 08
width: 32 bits
clock: 33MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
resources: irq:18 memory:dfcfc800-dfcfcfff
*-generic
description: SD Host controller
product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
vendor: Ricoh Co Ltd
physical id: 1.2
bus info: pci@0000:03:01.2
version: 17
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=sdhci-pci latency=64
resources: irq:17 memory:dfcfc700-dfcfc7ff
*-network:1
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:03:03.0
logical name: eth1
version: 05
serial: 00:13:ce:d3:04:21
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.33 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:dfcfd000-dfcfdfff
*-multimedia
description: Multimedia audio controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
vendor: Intel Corporation
physical id: 1e.2
bus info: pci@0000:00:1e.2
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=0
resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
*-communication UNCLAIMED
description: Modem
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
vendor: Intel Corporation
physical id: 1e.3
bus info: pci@0000:00:1e.3
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm generic cap_list
configuration: latency=0
resources: ioport:ee00(size=256) ioport:ec80(size=12
*-isa
description: ISA bridge
product: 82801FBM (ICH6M) LPC Interface Bridge
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: isa bus_master
configuration: latency=0
*-ide
description: IDE interface
product: 82801FBM (ICH6M) SATA Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi0
logical name: scsi1
version: 03
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=ata_piix latency=0
resources: irq:17 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:bfa0(size=16)
*-disk
description: ATA Disk
product: SAMSUNG MP0603H
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: UD20
serial: S03ZJ10YB51849
size: 55GiB (60GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=000f0170
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: 7c78da4b-a063-46b6-b567-91aecbbfc3fb
size: 53GiB
capacity: 53GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration: created=2011-01-22 18:12:59 filesystem=ext4 lastmountpoint=/5[;!&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;9&#65533;P&#65533;&#65533;&#65533;Dq!&#65533;P&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; s!&#65533; j modified=2011-01-22 18:34:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-25 16:49:17 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
size: 2380MiB
capacity: 2380MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 2380MiB
capabilities: nofs
*-cdrom
description: DVD reader
product: CDRW/DVD TSL462C
vendor: TSSTcorp
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: DE01
capabilities: removable audio cd-r cd-rw dvd
configuration: ansiversion=5 status=nodisc
*-serial UNCLAIMED
description: SMBus
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 03
width: 32 bits
clock: 33MHz
configuration: latency=0
resources: ioport:10c0(size=32)
*-battery
product: DELL F51335A
vendor: Sanyo
physical id: 1
slot: Sys. Battery Bay
capacity: 48000mWh
configuration: voltage=11.1V
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes
j@j-Inspiron-9300:~$ 

```

---

### Post by qwertyjjj on 2011-01-27
Here is an example where for no reason at all it changes the speed to 800 to 800. The fan didn't even come on so it can't be the PCU getting hot.
I have highlighted the times in bold 15 mins apart with the giverner speed settings.

```

j@j-Inspiron-9300:~$ date
**Thu Jan 27 09:05:41 CET 2011**
j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
 ** current policy: frequency should be within 800 MHz and 1.73 GHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
  cpufreq stats: 1.73 GHz:18.10%, 1.33 GHz:1.19%, 1.07 GHz:0.59%, 800 MHz:80.12%  (9055)

j@j-Inspiron-9300:~$ date
**Thu Jan 27 09:20:23 CET 2011**
j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
**  current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:24.51%, 1.33 GHz:3.24%, 1.07 GHz:1.13%, 800 MHz:71.13%  (28892) 

```

---

