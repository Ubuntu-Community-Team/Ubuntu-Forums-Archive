---
title: "unity freezing up"
date: 2011-05-02
forum: Hardware
---

### Post by sn0m on 2011-05-02
Hi
I've upgraded to 11.04 and love the new interphase.
I must admit it took a bit to get used to but now it is fine, even my missus likes it.
Now me computer has freezed up a few times forcing me to reboot.
this is the output from dmesg | grep error:
[   17.547834] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   22.654370] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   24.842007] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[ 5555.336557] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[25156.484087] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[25465.753586] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[27513.690537] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[28017.654922] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[31026.626574] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[31796.309716] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[33448.440243] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[33761.597473] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[34421.356994] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[39186.624948] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[39948.558974] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[40432.397513] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[41870.580977] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[42469.855497] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[42556.955277] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[43151.592223] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[45673.138345] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[46748.855694] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[52437.755078] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[53038.167166] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[59784.112539] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[60092.755750] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[65916.111155] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[69859.499264] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600

Now the hard disk is ok i think:

koli@koli-laptop:~$ sudo smartctl -d ata -H /dev/sda
smartctl 5.40 2010-07-12 r3124 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

koli@koli-laptop:~$ 

and this is my laptop:
koli-laptop               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2953MiB
     *-cpu
          product: Genuine Intel(R) CPU           T1600  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 250MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=1
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
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f4000000-f43fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f4400000-f44fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f4704000-f47043ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:f4700000-f4703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f0000000-f1ffffff ioport:f6000000(size=67108864)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:7f:31:bc
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:2000(size=256) memory:f8000000-f8000fff memory:f6000000-f600ffff memory:f6020000-f603ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f2000000-f3ffffff ioport:fa000000(size=33554432)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 02
                serial: 00:1f:3c:d0:6e:ca
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.0.5 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:44 memory:f2000000-f2000fff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f4704400-f47047ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18f8(size=8) ioport:180c(size=4) ioport:18f0(size=8) ioport:1808(size=4) ioport:18e0(size=16) ioport:1810(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0000000-c00000ff ioport:1c00(size=32)
        *-ide:1
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1c50(size=8) ioport:1c44(size=4) ioport:1c48(size=8) ioport:1c40(size=4) ioport:1c30(size=16) ioport:1c20(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
--------------------------------------------------------------------------

Now is this a bug or has my hardware became so outdated that I am forced to buy a new laptop with bigger specs, or even worse, do I need to go back to classic view?
Thanks
Sokol

---

### Post by hsoulen on 2011-05-13
Same problem here.

Switched to Ubuntu Classic (Gnome) and so far no freezes.

Unity... Ugh.

Hank

---

