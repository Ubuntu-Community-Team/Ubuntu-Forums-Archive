---
title: "Dell Vostro 3450 i5 SB/Radeon 6630M - battery discharging extremely fast! (11.10)"
date: 2011-09-21
forum: Hardware
---

### Post by Siekacz on 2011-09-21
Yes, I know - there is a well-known power issue in kernel since 2.6.38. There is also a workaround - forcing ASPM to run. But it does not work for me. Even if I set proper parameter in the GRUB's confguration, it still fails to run. PowerTOP shows that Ubutnu eats 23W.


```
bartosz@bartosz-Dell-System-Vostro-3450:~$ dmesg | grep OSC
[    1.064427] \_SB_.PCI0:_OSC invalid UUID
[    1.064428] _OSC request data:1 8 1f 
[    1.146672] \_SB_.PCI0:_OSC invalid UUID
[    1.146673] _OSC request data:1 1f 1f 
[    1.146677]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.146704] \_SB_.PCI0:_OSC invalid UUID
[    1.146705] _OSC request data:1 0 1d 
[    1.146708]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.146709] ACPI _OSC control for PCIe not granted, disabling ASPM
```
```
bartosz@bartosz-Dell-System-Vostro-3450:~$ dmesg | grep ASPM
[    0.000000] PCIe ASPM is forcedly enabled
[    1.146709] ACPI _OSC control for PCIe not granted, disabling ASPM
```

Looks like BOS is blocking kernel to run ASPM. Any other workaround?

```
bartosz-dell-system-vostro-3450
    description: Portable Computer
    product: Dell System Vostro 3450 (System SKUNumber)
    vendor: Winbond Electronics
    version: 0.1
    serial: 2FJ1SQ1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=portable family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=44454C4C-4600-104A-8031-B2C04F535131
  *-core
       description: Motherboard
       product: 0K8WHD
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: .2FJ1SQ1.CN4864318B0286.
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 07/22/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 2e
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          serial: Not Supported by CPU
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2f
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 30
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 31
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M2S4G64CB8HB5N-CG
             vendor: Nanya Technology
             physical id: 0
             serial: E872056C
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: NT4GC64B8HB0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: DA68C816
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:e1700000-e17fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: NI Whistler [AMD Radeon HD 6600M Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:51 memory:c0000000-cfffffff memory:e1700000-e171ffff ioport:4000(size=256) memory:e1720000-e173ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:49 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:5000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:e1805000-e180500f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:e180a000-e180a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:50 memory:e1800000-e1803fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:e1600000-e16fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 34
                serial: ac:72:89:3e:7d:03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-11-generic firmware=17.168.5.1 build 33993 ip=192.168.69.173 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:48 memory:e1600000-e1601fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:e1500000-e15fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:e1500000-e1501fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) ioport:e0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: 14:fe:b5:bf:20:c7
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:3000(size=256) memory:e0404000-e0404fff memory:e0400000-e0403fff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:e0d00000-e14fffff ioport:e0500000(size=8388608)
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e1809000-e18093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
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
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:e1808000-e18087ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: D005
                serial: 5VJDCQRH
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e43e8
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2cc3c43d-c8bd-444d-96c7-549fe80291f9
                   size: 457GiB
                   capacity: 457GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-19 11:31:29 filesystem=ext4 lastmountpoint=/ modified=2011-09-19 11:41:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-09-21 09:50:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 8084MiB
                   capacity: 8084MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8084MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D500
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e1804000-e18040ff ioport:efa0(size=32)
  *-battery
       product: DELL
       vendor: Dynapack
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
       capacity: 48840mWh
       configuration: voltage=11,1V
```

---

### Post by nex_gen on 2011-09-30
Check out this article: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

You can add these boot arguments to /etc/default/grub ->
```
GRUB_CMDLINE_LINUX_DEFAULT="quit splash i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"
``` 
and then run
```
sudo update-grub
```

Also, make sure you disable the discrete GPU.
This can be done by running 
```
sudo bash
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit
```
as mentioned here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Unfortunately, I haven't find a way to use my discrete GPU under ubuntu as current amd blob doesn't support the 6630m and I had no luck with the open source drivers either.

---

### Post by Siekacz on 2011-10-05
Works. Now battery lifetime is about 4h, but still cannot find any workaround to make radeon work.

---

### Post by www.rzr.online.fr on 2011-11-01
Can you explain :


[    1.064427] \_SB_.PCI0:_OSC invalid UUID


I have that one in my logs on lenovo g470 :

[http://rzr.online.fr/q/aspm](http://rzr.online.fr/q/aspm)

---

