---
title: "usb3 no longer working?"
date: 2011-06-06
forum: Hardware
---

### Post by phibuntu on 2011-06-06
Hi to every hardware crack


I have just upgraded to Ubuntu 11.04 and the USB-3 port is no longer working. It worked formerly using 10.10.

I am using an external USB 3 (1 TByte) hard drive.
The drive is still working, but not on the blue usb3 connector. So I have to go back to usb 2 :-(


Any Ideas (see [FONT="Courier New"]lshw[/FONT] output below)?

PS: I installed Windows 7 on a second partition. I don't know if it was the installation of Win 7 or the upgrade to 11.04 that corrupted my USB 3 "driver".


```
>sudo lshw
[sudo] password for phi: 
rose                      
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P67 Pro3
       vendor: ASRock
       physical id: 0
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 2200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-through unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4D1
             vendor: Micron
             physical id: 0
             serial: 31295D99
             slot: A1_DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4D1
             vendor: Micron
             physical id: 1
             serial: EA38A63B
             slot: A1_DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4D1
             vendor: Micron
             physical id: 2
             serial: 31290C29
             slot: A1_DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JTF25664AZ-1G4D1
             vendor: Micron
             physical id: 3
             serial: 293C71E2
             slot: A1_DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.80
          date: 02/15/2011
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f8000000-fa0fffff ioport:d0000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF106 [GeForce 450 GTS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f8000000-f8ffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
           *-multimedia
                description: Audio device
                product: GF106 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:fa080000-fa083fff
        *-communication UNCLAIMED
             description: Communication controller
             product: 6 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:fa207000-fa20700f
        *-usb:0
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fa206000-fa2063ff
        *-multimedia
             description: Audio device
             product: 6 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:fa200000-fa203fff
        *-pci:1
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-pci:2
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) ioport:dc100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 00:25:22:b1:e3:86
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:45 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
        *-pci:3
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:fa100000-fa1fffff
           *-usb
                description: USB Controller
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:46 memory:fa100000-fa107fff
        *-pci:4
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
        *-usb:1
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fa205000-fa2053ff
        *-isa
             description: ISA bridge
             product: P67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 6 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f090(size=16) ioport:f080(size=16)
           *-disk:0
                description: ATA Disk
                product: OCZ-VERTEX3
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2.02
                serial: OCZ-JAK789G06HC9Z689
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00044678
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 61fc4fb0-d0ee-4ba5-9a1b-f01faf22cb11
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-25 17:35:12 filesystem=ext4 lastmountpoint=/ modified=2011-06-05 09:50:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-06 08:04:45 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: d1899a32-9e30-48e6-99ed-be3807d072f1
                   size: 7662MiB
                   capacity: 7662MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: f63c30e1-774d-4fb1-b7d3-77fe99788848
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-05-25 12:42:53 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: BDDVDRW CH10LS20
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: OCZ-VERTEX3
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 2.02
                serial: OCZ-U9S382WE259W9ZKC
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007566d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /scratch
                   version: 3.1
                   serial: 7675a958-237e-40ef-9742-c017f9d907ce
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-25 12:42:09 filesystem=ntfs label=scratch mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-disk:2
                description: ATA Disk
                product: WDC WD1003FBYX-0
                vendor: Western Digital
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: 01.0
                serial: WD-WCAW31767603
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000545da
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   logical name: /multimedia
                   version: 3.1
                   serial: 69ccf13d-9aed-439d-bf96-625cd2929fa2
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-24 20:53:49 filesystem=ntfs label=multimedia mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fa204000-fa2040ff ioport:f000(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f030(size=16) ioport:f020(size=16)
```

---

### Post by macalga on 2011-06-07
hi,

I have the same problem and I have found a workaround on Linux Mint 11 (Ubuntu)

Connect the USB3 HDD before booting ... that's work for me.

Regards
Gaetano

---

### Post by phibuntu on 2011-06-07
Thanks macalga, but no! 

Your "trick" does not work in my case.

The life-cd ubuntu 10.10 64-bit works out of the box (I tried ten minutes ago).

Probably the upgrade-process to 11.04 was not propper?

Here the syslog (PS: "rose" is my wifes chosen name for the machine):

  ```
Jun  7 21:25:42 rose kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun  7 21:25:42 rose rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="749" x-info="http://www.rsyslog.com"] (re)start
Jun  7 21:25:42 rose rsyslogd: rsyslogd's groupid changed to 103
Jun  7 21:25:42 rose rsyslogd: rsyslogd's userid changed to 101
Jun  7 21:25:42 rose rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun  7 21:25:42 rose kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  7 21:25:42 rose kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  7 21:25:42 rose kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun  7 21:25:42 rose kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=61fc4fb0-d0ee-4ba5-9a1b-f01faf22cb11 ro quiet splash vt.handoff=7
Jun  7 21:25:42 rose kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf58e000 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf58e000 - 00000000cf5e3000 (ACPI NVS)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf5e3000 - 00000000cf608000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf608000 - 00000000cf609000 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf609000 - 00000000cf60a000 (ACPI data)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf60a000 - 00000000cf614000 (ACPI NVS)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf614000 - 00000000cf639000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf639000 - 00000000cf67c000 (ACPI NVS)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000cf67c000 - 00000000cf800000 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed40000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000022f800000 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000] NX (Execute Disable) protection: active
Jun  7 21:25:42 rose kernel: [    0.000000] DMI 2.6 present.
Jun  7 21:25:42 rose kernel: [    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./P67 Pro3, BIOS P1.80 02/15/2011
Jun  7 21:25:42 rose kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun  7 21:25:42 rose kernel: [    0.000000] No AGP bridge found
Jun  7 21:25:42 rose kernel: [    0.000000] last_pfn = 0x22f800 max_arch_pfn = 0x400000000
Jun  7 21:25:42 rose kernel: [    0.000000] MTRR default type: uncachable
Jun  7 21:25:42 rose kernel: [    0.000000] MTRR fixed ranges enabled:
Jun  7 21:25:42 rose kernel: [    0.000000]   00000-9FFFF write-back
Jun  7 21:25:42 rose kernel: [    0.000000]   A0000-BFFFF uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   C0000-CFFFF write-protect
Jun  7 21:25:42 rose kernel: [    0.000000]   D0000-E7FFF uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   E8000-FFFFF write-protect
Jun  7 21:25:42 rose kernel: [    0.000000] MTRR variable ranges enabled:
Jun  7 21:25:42 rose kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Jun  7 21:25:42 rose kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Jun  7 21:25:42 rose kernel: [    0.000000]   2 base 0D0000000 mask FF0000000 uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   4 base 22F800000 mask FFF800000 uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   5 base 230000000 mask FF0000000 uncachable
Jun  7 21:25:42 rose kernel: [    0.000000]   6 disabled
Jun  7 21:25:42 rose kernel: [    0.000000]   7 disabled
Jun  7 21:25:42 rose kernel: [    0.000000]   8 disabled
Jun  7 21:25:42 rose kernel: [    0.000000]   9 disabled
Jun  7 21:25:42 rose kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  7 21:25:42 rose kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun  7 21:25:42 rose kernel: [    0.000000] last_pfn = 0xcf800 max_arch_pfn = 0x400000000
Jun  7 21:25:42 rose kernel: [    0.000000] found SMP MP-table at [ffff8800000fcf60] fcf60
Jun  7 21:25:42 rose kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun  7 21:25:42 rose kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cf800000
Jun  7 21:25:42 rose kernel: [    0.000000]  0000000000 - 00cf800000 page 2M
Jun  7 21:25:42 rose kernel: [    0.000000] kernel direct mapping tables up to cf800000 @ 1fffb000-20000000
Jun  7 21:25:42 rose kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000022f800000
Jun  7 21:25:42 rose kernel: [    0.000000]  0100000000 - 022f800000 page 2M
Jun  7 21:25:42 rose kernel: [    0.000000] kernel direct mapping tables up to 22f800000 @ cf7f6000-cf800000
Jun  7 21:25:42 rose kernel: [    0.000000] RAMDISK: 366e2000 - 37369000
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: XSDT 00000000cf5db068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: FACP 00000000cf5e1fd0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: DSDT 00000000cf5db150 06E7A (v02 ALASKA    A M I 00000000 INTL 20051117)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: FACS 00000000cf60bf80 00040
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: APIC 00000000cf5e20c8 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: SSDT 00000000cf5e2160 001D6 (v01 AMICPU     PROC 00000001 MSFT 03000001)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: MCFG 00000000cf5e2338 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: AAFT 00000000cf5e2378 0006F (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: HPET 00000000cf5e23e8 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  7 21:25:42 rose kernel: [    0.000000] No NUMA configuration found
Jun  7 21:25:42 rose kernel: [    0.000000] Faking a node at 0000000000000000-000000022f800000
Jun  7 21:25:42 rose kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000022f800000
Jun  7 21:25:42 rose kernel: [    0.000000]   NODE_DATA [000000022f7fb000 - 000000022f7fffff]
Jun  7 21:25:42 rose kernel: [    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880227600000-ffff88022e7fffff] on node 0
Jun  7 21:25:42 rose kernel: [    0.000000] Zone PFN ranges:
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun  7 21:25:42 rose kernel: [    0.000000]   Normal   0x00100000 -> 0x0022f800
Jun  7 21:25:42 rose kernel: [    0.000000] Movable zone start PFN for each node
Jun  7 21:25:42 rose kernel: [    0.000000] early_node_map[5] active PFN ranges
Jun  7 21:25:42 rose kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun  7 21:25:42 rose kernel: [    0.000000]     0: 0x00000100 -> 0x000cf58e
Jun  7 21:25:42 rose kernel: [    0.000000]     0: 0x000cf608 -> 0x000cf609
Jun  7 21:25:42 rose kernel: [    0.000000]     0: 0x000cf67c -> 0x000cf800
Jun  7 21:25:42 rose kernel: [    0.000000]     0: 0x00100000 -> 0x0022f800
Jun  7 21:25:42 rose kernel: [    0.000000] On node 0 totalpages: 2092705
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA zone: 6 pages reserved
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA zone: 3920 pages, LIFO batch:0
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun  7 21:25:42 rose kernel: [    0.000000]   DMA32 zone: 831307 pages, LIFO batch:31
Jun  7 21:25:42 rose kernel: [    0.000000]   Normal zone: 16996 pages used for memmap
Jun  7 21:25:42 rose kernel: [    0.000000]   Normal zone: 1226140 pages, LIFO batch:31
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Jun  7 21:25:42 rose kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  7 21:25:42 rose kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  7 21:25:42 rose kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jun  7 21:25:42 rose kernel: [    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
Jun  7 21:25:42 rose kernel: [    0.000000] nr_irqs_gsi: 40
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf58e000 - 00000000cf5e3000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf5e3000 - 00000000cf608000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf609000 - 00000000cf60a000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf60a000 - 00000000cf614000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf614000 - 00000000cf639000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf639000 - 00000000cf67c000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000cf800000 - 00000000fed1c000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed40000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000ff000000
Jun  7 21:25:42 rose kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Jun  7 21:25:42 rose kernel: [    0.000000] Allocating PCI resources starting at cf800000 (gap: cf800000:2f51c000)
Jun  7 21:25:42 rose kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  7 21:25:42 rose kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Jun  7 21:25:42 rose kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cf200000 s84416 r8192 d22080 u262144
Jun  7 21:25:42 rose kernel: [    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
Jun  7 21:25:42 rose kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jun  7 21:25:42 rose kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061367
Jun  7 21:25:42 rose kernel: [    0.000000] Policy zone: Normal
Jun  7 21:25:42 rose kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=61fc4fb0-d0ee-4ba5-9a1b-f01faf22cb11 ro quiet splash vt.handoff=7
Jun  7 21:25:42 rose kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun  7 21:25:42 rose kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Jun  7 21:25:42 rose kernel: [    0.000000] Checking aperture...
Jun  7 21:25:42 rose kernel: [    0.000000] No AGP bridge found
Jun  7 21:25:42 rose kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun  7 21:25:42 rose kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun  7 21:25:42 rose kernel: [    0.000000] Memory: 8160764k/9166848k available (5940k kernel code, 796028k absent, 210056k reserved, 5017k data, 956k init)
Jun  7 21:25:42 rose kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jun  7 21:25:42 rose kernel: [    0.000000] Hierarchical RCU implementation.
Jun  7 21:25:42 rose kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun  7 21:25:42 rose kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Jun  7 21:25:42 rose kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Jun  7 21:25:42 rose kernel: [    0.000000] Extended CMOS year: 2000
Jun  7 21:25:42 rose kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun  7 21:25:42 rose kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  7 21:25:42 rose kernel: [    0.000000] console [tty0] enabled
Jun  7 21:25:42 rose kernel: [    0.000000] allocated 83886080 bytes of page_cgroup
Jun  7 21:25:42 rose kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  7 21:25:42 rose kernel: [    0.000000] hpet clockevent registered
Jun  7 21:25:42 rose kernel: [    0.000000] Fast TSC calibration using PIT
Jun  7 21:25:42 rose kernel: [    0.010000] Detected 3392.711 MHz processor.
Jun  7 21:25:42 rose kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6785.42 BogoMIPS (lpj=33927110)
Jun  7 21:25:42 rose kernel: [    0.000005] pid_max: default: 32768 minimum: 301
Jun  7 21:25:42 rose kernel: [    0.000020] Security Framework initialized
Jun  7 21:25:42 rose kernel: [    0.000029] AppArmor: AppArmor initialized
Jun  7 21:25:42 rose kernel: [    0.000030] Yama: becoming mindful.
Jun  7 21:25:42 rose kernel: [    0.000551] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun  7 21:25:42 rose kernel: [    0.001800] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun  7 21:25:42 rose kernel: [    0.002287] Mount-cache hash table entries: 256
Jun  7 21:25:42 rose kernel: [    0.002359] Initializing cgroup subsys ns
Jun  7 21:25:42 rose kernel: [    0.002361] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jun  7 21:25:42 rose kernel: [    0.002362] Initializing cgroup subsys cpuacct
Jun  7 21:25:42 rose kernel: [    0.002365] Initializing cgroup subsys memory
Jun  7 21:25:42 rose kernel: [    0.002369] Initializing cgroup subsys devices
Jun  7 21:25:42 rose kernel: [    0.002370] Initializing cgroup subsys freezer
Jun  7 21:25:42 rose kernel: [    0.002371] Initializing cgroup subsys net_cls
Jun  7 21:25:42 rose kernel: [    0.002372] Initializing cgroup subsys blkio
Jun  7 21:25:42 rose kernel: [    0.002392] CPU: Physical Processor ID: 0
Jun  7 21:25:42 rose kernel: [    0.002392] CPU: Processor Core ID: 0
Jun  7 21:25:42 rose kernel: [    0.002396] mce: CPU supports 9 MCE banks
Jun  7 21:25:42 rose kernel: [    0.002406] CPU0: Thermal monitoring enabled (TM1)
Jun  7 21:25:42 rose kernel: [    0.002411] using mwait in idle threads.
Jun  7 21:25:42 rose kernel: [    0.004094] ACPI: Core revision 20110112
Jun  7 21:25:42 rose kernel: [    0.006141] ftrace: allocating 24314 entries in 96 pages
Jun  7 21:25:42 rose kernel: [    0.012676] Setting APIC routing to flat
Jun  7 21:25:42 rose kernel: [    0.013010] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  7 21:25:42 rose kernel: [    0.112742] CPU0: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz stepping 07
Jun  7 21:25:42 rose kernel: [    0.227733] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
Jun  7 21:25:42 rose kernel: [    0.227737] ... version:                3
Jun  7 21:25:42 rose kernel: [    0.227737] ... bit width:              48
Jun  7 21:25:42 rose kernel: [    0.227738] ... generic registers:      4
Jun  7 21:25:42 rose kernel: [    0.227739] ... value mask:             0000ffffffffffff
Jun  7 21:25:42 rose kernel: [    0.227740] ... max period:             000000007fffffff
Jun  7 21:25:42 rose kernel: [    0.227741] ... fixed-purpose events:   3
Jun  7 21:25:42 rose kernel: [    0.227741] ... event mask:             000000070000000f
Jun  7 21:25:42 rose kernel: [    0.228020] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
Jun  7 21:25:42 rose kernel: [    1.484246] Brought up 8 CPUs
Jun  7 21:25:42 rose kernel: [    1.484249] Total of 8 processors activated (54277.51 BogoMIPS).
Jun  7 21:25:42 rose kernel: [    1.488257] devtmpfs: initialized
Jun  7 21:25:42 rose kernel: [    1.488845] print_constraints: dummy: 
Jun  7 21:25:42 rose kernel: [    1.488870] Time: 21:25:32  Date: 06/07/11
Jun  7 21:25:42 rose kernel: [    1.488888] NET: Registered protocol family 16
Jun  7 21:25:42 rose kernel: [    1.488949] Trying to unpack rootfs image as initramfs...
Jun  7 21:25:42 rose kernel: [    1.488952] ACPI: bus type pci registered
Jun  7 21:25:42 rose kernel: [    1.489001] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun  7 21:25:42 rose kernel: [    1.489002] PCI: not using MMCONFIG
Jun  7 21:25:42 rose kernel: [    1.489003] PCI: Using configuration type 1 for base access
Jun  7 21:25:42 rose kernel: [    1.489425] bio: create slab <bio-0> at 0
Jun  7 21:25:42 rose kernel: [    1.490221] ACPI: EC: Look up EC in DSDT
Jun  7 21:25:42 rose kernel: [    1.490958] ACPI: Executed 1 blocks of module-level executable AML code
Jun  7 21:25:42 rose kernel: [    1.492914] ACPI: SSDT 00000000cf613898 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
Jun  7 21:25:42 rose kernel: [    1.493166] ACPI: Dynamic OEM Table Load:
Jun  7 21:25:42 rose kernel: [    1.493168] ACPI: SSDT           (null) 006F4 (v01    AMI      IST 00000001 MSFT 03000001)
Jun  7 21:25:42 rose kernel: [    1.493191] ACPI: SSDT 00000000cf60ad98 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
Jun  7 21:25:42 rose kernel: [    1.493375] ACPI: Dynamic OEM Table Load:
Jun  7 21:25:42 rose kernel: [    1.493376] ACPI: SSDT           (null) 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
Jun  7 21:25:42 rose kernel: [    1.493925] ACPI: Interpreter enabled
Jun  7 21:25:42 rose kernel: [    1.493926] ACPI: (supports S0 S1 S3 S4 S5)
Jun  7 21:25:42 rose kernel: [    1.493939] ACPI: Using IOAPIC for interrupt routing
Jun  7 21:25:42 rose kernel: [    1.493955] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun  7 21:25:42 rose kernel: [    1.494000] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun  7 21:25:42 rose kernel: [    1.529741] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jun  7 21:25:42 rose kernel: [    1.532716] ACPI: No dock devices found.
Jun  7 21:25:42 rose kernel: [    1.532718] HEST: Table not found.
Jun  7 21:25:42 rose kernel: [    1.532719] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun  7 21:25:42 rose kernel: [    1.532843] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun  7 21:25:42 rose kernel: [    1.532980] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jun  7 21:25:42 rose kernel: [    1.532981] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jun  7 21:25:42 rose kernel: [    1.532982] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun  7 21:25:42 rose kernel: [    1.532983] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
Jun  7 21:25:42 rose kernel: [    1.532985] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xffffffff]
Jun  7 21:25:42 rose kernel: [    1.532993] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
Jun  7 21:25:42 rose kernel: [    1.533017] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.533034] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533036] pci 0000:00:01.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533091] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Jun  7 21:25:42 rose kernel: [    1.533122] pci 0000:00:16.0: reg 10: [mem 0xfa207000-0xfa20700f 64bit]
Jun  7 21:25:42 rose kernel: [    1.533205] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533209] pci 0000:00:16.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533251] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Jun  7 21:25:42 rose kernel: [    1.533278] pci 0000:00:1a.0: reg 10: [mem 0xfa206000-0xfa2063ff]
Jun  7 21:25:42 rose kernel: [    1.533379] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533383] pci 0000:00:1a.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533413] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Jun  7 21:25:42 rose kernel: [    1.533433] pci 0000:00:1b.0: reg 10: [mem 0xfa200000-0xfa203fff 64bit]
Jun  7 21:25:42 rose kernel: [    1.533512] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533515] pci 0000:00:1b.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533540] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.533628] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533632] pci 0000:00:1c.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533664] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.533751] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533755] pci 0000:00:1c.4: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533783] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.533871] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.533875] pci 0000:00:1c.5: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.533905] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.533998] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.534002] pci 0000:00:1c.6: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.534030] pci 0000:00:1c.7: [8086:244e] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.534117] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.534121] pci 0000:00:1c.7: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.534156] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Jun  7 21:25:42 rose kernel: [    1.534184] pci 0000:00:1d.0: reg 10: [mem 0xfa205000-0xfa2053ff]
Jun  7 21:25:42 rose kernel: [    1.534285] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.534289] pci 0000:00:1d.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.534317] pci 0000:00:1f.0: [8086:1c46] type 0 class 0x000601
Jun  7 21:25:42 rose kernel: [    1.534462] pci 0000:00:1f.2: [8086:1c00] type 0 class 0x000101
Jun  7 21:25:42 rose kernel: [    1.534484] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
Jun  7 21:25:42 rose kernel: [    1.534494] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
Jun  7 21:25:42 rose kernel: [    1.534504] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
Jun  7 21:25:42 rose kernel: [    1.534514] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
Jun  7 21:25:42 rose kernel: [    1.534525] pci 0000:00:1f.2: reg 20: [io  0xf090-0xf09f]
Jun  7 21:25:42 rose kernel: [    1.534535] pci 0000:00:1f.2: reg 24: [io  0xf080-0xf08f]
Jun  7 21:25:42 rose kernel: [    1.534586] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Jun  7 21:25:42 rose kernel: [    1.534607] pci 0000:00:1f.3: reg 10: [mem 0xfa204000-0xfa2040ff 64bit]
Jun  7 21:25:42 rose kernel: [    1.534636] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
Jun  7 21:25:42 rose kernel: [    1.534679] pci 0000:00:1f.5: [8086:1c08] type 0 class 0x000101
Jun  7 21:25:42 rose kernel: [    1.534701] pci 0000:00:1f.5: reg 10: [io  0xf070-0xf077]
Jun  7 21:25:42 rose kernel: [    1.534711] pci 0000:00:1f.5: reg 14: [io  0xf060-0xf063]
Jun  7 21:25:42 rose kernel: [    1.534722] pci 0000:00:1f.5: reg 18: [io  0xf050-0xf057]
Jun  7 21:25:42 rose kernel: [    1.534732] pci 0000:00:1f.5: reg 1c: [io  0xf040-0xf043]
Jun  7 21:25:42 rose kernel: [    1.534743] pci 0000:00:1f.5: reg 20: [io  0xf030-0xf03f]
Jun  7 21:25:42 rose kernel: [    1.534752] pci 0000:00:1f.5: reg 24: [io  0xf020-0xf02f]
Jun  7 21:25:42 rose kernel: [    1.534821] pci 0000:01:00.0: [10de:0dc4] type 0 class 0x000300
Jun  7 21:25:42 rose kernel: [    1.534828] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
Jun  7 21:25:42 rose kernel: [    1.534836] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xd7ffffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.534845] pci 0000:01:00.0: reg 1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.534850] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
Jun  7 21:25:42 rose kernel: [    1.534856] pci 0000:01:00.0: reg 30: [mem 0xfa000000-0xfa07ffff pref]
Jun  7 21:25:42 rose kernel: [    1.534889] pci 0000:01:00.1: [10de:0be9] type 0 class 0x000403
Jun  7 21:25:42 rose kernel: [    1.534897] pci 0000:01:00.1: reg 10: [mem 0xfa080000-0xfa083fff]
Jun  7 21:25:42 rose kernel: [    1.553950] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun  7 21:25:42 rose kernel: [    1.553953] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jun  7 21:25:42 rose kernel: [    1.553955] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfa0fffff]
Jun  7 21:25:42 rose kernel: [    1.553957] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdbffffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.554020] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun  7 21:25:42 rose kernel: [    1.554024] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Jun  7 21:25:42 rose kernel: [    1.554028] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  7 21:25:42 rose kernel: [    1.554036] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  7 21:25:42 rose kernel: [    1.554124] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
Jun  7 21:25:42 rose kernel: [    1.554149] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
Jun  7 21:25:42 rose kernel: [    1.554191] pci 0000:03:00.0: reg 18: [mem 0xdc104000-0xdc104fff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.554217] pci 0000:03:00.0: reg 20: [mem 0xdc100000-0xdc103fff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.554292] pci 0000:03:00.0: supports D1 D2
Jun  7 21:25:42 rose kernel: [    1.554293] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.554299] pci 0000:03:00.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.573900] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Jun  7 21:25:42 rose kernel: [    1.573905] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
Jun  7 21:25:42 rose kernel: [    1.573909] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  7 21:25:42 rose kernel: [    1.573916] pci 0000:00:1c.4:   bridge window [mem 0xdc100000-0xdc1fffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.574003] pci 0000:04:00.0: [1b6f:7023] type 0 class 0x000c03
Jun  7 21:25:42 rose kernel: [    1.574036] pci 0000:04:00.0: reg 10: [mem 0xfa100000-0xfa107fff 64bit]
Jun  7 21:25:42 rose kernel: [    1.574162] pci 0000:04:00.0: supports D1 D2
Jun  7 21:25:42 rose kernel: [    1.574163] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  7 21:25:42 rose kernel: [    1.574169] pci 0000:04:00.0: PME# disabled
Jun  7 21:25:42 rose kernel: [    1.593842] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
Jun  7 21:25:42 rose kernel: [    1.593847] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
Jun  7 21:25:42 rose kernel: [    1.593852] pci 0000:00:1c.5:   bridge window [mem 0xfa100000-0xfa1fffff]
Jun  7 21:25:42 rose kernel: [    1.593859] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  7 21:25:42 rose kernel: [    1.593922] pci 0000:00:1c.6: PCI bridge to [bus 05-05]
Jun  7 21:25:42 rose kernel: [    1.593926] pci 0000:00:1c.6:   bridge window [io  0xf000-0x0000] (disabled)
Jun  7 21:25:42 rose kernel: [    1.593930] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  7 21:25:42 rose kernel: [    1.593937] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594015] pci 0000:06:00.0: [1b21:1080] type 1 class 0x000604
Jun  7 21:25:42 rose kernel: [    1.594145] pci 0000:00:1c.7: PCI bridge to [bus 06-07] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594149] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594154] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594160] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594162] pci 0000:00:1c.7:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594163] pci 0000:00:1c.7:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594165] pci 0000:00:1c.7:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594166] pci 0000:00:1c.7:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594167] pci 0000:00:1c.7:   bridge window [mem 0xd0000000-0xffffffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594304] pci 0000:06:00.0: PCI bridge to [bus 07-07] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594315] pci 0000:06:00.0:   bridge window [io  0xfff000-0x0000] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594321] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594332] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jun  7 21:25:42 rose kernel: [    1.594334] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594335] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594336] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594338] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594339] pci 0000:06:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594340] pci 0000:06:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594342] pci 0000:06:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594343] pci 0000:06:00.0:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594344] pci 0000:06:00.0:   bridge window [mem 0xd0000000-0xffffffff] (subtractive decode)
Jun  7 21:25:42 rose kernel: [    1.594395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun  7 21:25:42 rose kernel: [    1.594483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun  7 21:25:42 rose kernel: [    1.594504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Jun  7 21:25:42 rose kernel: [    1.594520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Jun  7 21:25:42 rose kernel: [    1.594537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
Jun  7 21:25:42 rose kernel: [    1.594553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
Jun  7 21:25:42 rose kernel: [    1.594571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7.PE2P._PRT]
Jun  7 21:25:42 rose kernel: [    1.594602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jun  7 21:25:42 rose kernel: [    1.594676]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun  7 21:25:42 rose kernel: [    1.594759]  pci0000:00: ACPI _OSC control (0x1d) granted
Jun  7 21:25:42 rose kernel: [    1.597203] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597232] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597260] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 10 11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597287] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597314] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
Jun  7 21:25:42 rose kernel: [    1.597341] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
Jun  7 21:25:42 rose kernel: [    1.597368] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597395] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jun  7 21:25:42 rose kernel: [    1.597459] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun  7 21:25:42 rose kernel: [    1.597461] vgaarb: loaded
Jun  7 21:25:42 rose kernel: [    1.597556] SCSI subsystem initialized
Jun  7 21:25:42 rose kernel: [    1.597590] libata version 3.00 loaded.
Jun  7 21:25:42 rose kernel: [    1.597615] usbcore: registered new interface driver usbfs
Jun  7 21:25:42 rose kernel: [    1.597620] usbcore: registered new interface driver hub
Jun  7 21:25:42 rose kernel: [    1.597634] usbcore: registered new device driver usb
Jun  7 21:25:42 rose kernel: [    1.597686] wmi: Mapper loaded
Jun  7 21:25:42 rose kernel: [    1.597687] PCI: Using ACPI for IRQ routing
Jun  7 21:25:42 rose kernel: [    1.597689] PCI: pci_cache_line_size set to 64 bytes
Jun  7 21:25:42 rose kernel: [    1.597763] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun  7 21:25:42 rose kernel: [    1.597764] reserve RAM buffer: 00000000cf58e000 - 00000000cfffffff 
Jun  7 21:25:42 rose kernel: [    1.597766] reserve RAM buffer: 00000000cf609000 - 00000000cfffffff 
Jun  7 21:25:42 rose kernel: [    1.597768] reserve RAM buffer: 00000000cf800000 - 00000000cfffffff 
Jun  7 21:25:42 rose kernel: [    1.597769] reserve RAM buffer: 000000022f800000 - 000000022fffffff 
Jun  7 21:25:42 rose kernel: [    1.597824] NetLabel: Initializing
Jun  7 21:25:42 rose kernel: [    1.597825] NetLabel:  domain hash size = 128
Jun  7 21:25:42 rose kernel: [    1.597825] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  7 21:25:42 rose kernel: [    1.597832] NetLabel:  unlabeled traffic allowed by default
Jun  7 21:25:42 rose kernel: [    1.597858] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jun  7 21:25:42 rose kernel: [    1.597861] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun  7 21:25:42 rose kernel: [    1.599868] Switching to clocksource hpet
Jun  7 21:25:42 rose kernel: [    1.603498] AppArmor: AppArmor Filesystem Enabled
Jun  7 21:25:42 rose kernel: [    1.603511] pnp: PnP ACPI init
Jun  7 21:25:42 rose kernel: [    1.603520] ACPI: bus type pnp registered
Jun  7 21:25:42 rose kernel: [    1.603615] pnp 00:00: [bus 00-ff]
Jun  7 21:25:42 rose kernel: [    1.603616] pnp 00:00: [io  0x0cf8-0x0cff]
Jun  7 21:25:42 rose kernel: [    1.603617] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun  7 21:25:42 rose kernel: [    1.603618] pnp 00:00: [io  0x0d00-0xffff window]
Jun  7 21:25:42 rose kernel: [    1.603620] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun  7 21:25:42 rose kernel: [    1.603621] pnp 00:00: [mem 0x000c8000-0x000dffff window]
Jun  7 21:25:42 rose kernel: [    1.603622] pnp 00:00: [mem 0xd0000000-0xffffffff window]
Jun  7 21:25:42 rose kernel: [    1.603623] pnp 00:00: [mem 0x00000000 window]
Jun  7 21:25:42 rose kernel: [    1.603663] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jun  7 21:25:42 rose kernel: [    1.603699] pnp 00:01: [mem 0xfed10000-0xfed19fff]
Jun  7 21:25:42 rose kernel: [    1.603700] pnp 00:01: [mem 0xe0000000-0xefffffff]
Jun  7 21:25:42 rose kernel: [    1.603701] pnp 00:01: [mem 0xfed90000-0xfed93fff]
Jun  7 21:25:42 rose kernel: [    1.603702] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Jun  7 21:25:42 rose kernel: [    1.603703] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
Jun  7 21:25:42 rose kernel: [    1.603731] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603732] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603734] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603735] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603736] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603738] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun  7 21:25:42 rose kernel: [    1.603772] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Jun  7 21:25:42 rose kernel: [    1.603773] pnp 00:02: [io  0x0290-0x029f]
Jun  7 21:25:42 rose kernel: [    1.603774] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Jun  7 21:25:42 rose kernel: [    1.603800] Switched to NOHz mode on CPU #0
Jun  7 21:25:42 rose kernel: [    1.603817] system 00:02: [io  0x0290-0x029f] has been reserved
Jun  7 21:25:42 rose kernel: [    1.603818] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  7 21:25:42 rose kernel: [    1.603838] Switched to NOHz mode on CPU #1
Jun  7 21:25:42 rose kernel: [    1.603841] Switched to NOHz mode on CPU #2
Jun  7 21:25:42 rose kernel: [    1.603843] Switched to NOHz mode on CPU #3
Jun  7 21:25:42 rose kernel: [    1.603895] Switched to NOHz mode on CPU #4
Jun  7 21:25:42 rose kernel: [    1.603899] Switched to NOHz mode on CPU #5
Jun  7 21:25:42 rose kernel: [    1.603901] Switched to NOHz mode on CPU #6
Jun  7 21:25:42 rose kernel: [    1.603906] Switched to NOHz mode on CPU #7
Jun  7 21:25:42 rose kernel: [    1.604015] pnp 00:03: [io  0x03f0-0x03f5]
Jun  7 21:25:42 rose kernel: [    1.604016] pnp 00:03: [io  0x03f7]
Jun  7 21:25:42 rose kernel: [    1.604023] pnp 00:03: [irq 6]
Jun  7 21:25:42 rose kernel: [    1.604025] pnp 00:03: [dma 2]
Jun  7 21:25:42 rose kernel: [    1.604055] pnp 00:03: Plug and Play ACPI device, IDs PNP0700 (active)
Jun  7 21:25:42 rose kernel: [    1.604130] pnp 00:04: [dma 4]
Jun  7 21:25:42 rose kernel: [    1.604131] pnp 00:04: [io  0x0000-0x000f]
Jun  7 21:25:42 rose kernel: [    1.604134] pnp 00:04: [io  0x0081-0x0083]
Jun  7 21:25:42 rose kernel: [    1.604135] pnp 00:04: [io  0x0087]
Jun  7 21:25:42 rose kernel: [    1.604136] pnp 00:04: [io  0x0089-0x008b]
Jun  7 21:25:42 rose kernel: [    1.604137] pnp 00:04: [io  0x008f]
Jun  7 21:25:42 rose kernel: [    1.604138] pnp 00:04: [io  0x00c0-0x00df]
Jun  7 21:25:42 rose kernel: [    1.604151] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
Jun  7 21:25:42 rose kernel: [    1.604157] pnp 00:05: [io  0x0070-0x0071]
Jun  7 21:25:42 rose kernel: [    1.604161] pnp 00:05: [irq 8]
Jun  7 21:25:42 rose kernel: [    1.604174] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun  7 21:25:42 rose kernel: [    1.604178] pnp 00:06: [io  0x0061]
Jun  7 21:25:42 rose kernel: [    1.604191] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Jun  7 21:25:42 rose kernel: [    1.604200] pnp 00:07: [io  0x0010-0x001f]
Jun  7 21:25:42 rose kernel: [    1.604201] pnp 00:07: [io  0x0022-0x003f]
Jun  7 21:25:42 rose kernel: [    1.604202] pnp 00:07: [io  0x0044-0x005f]
Jun  7 21:25:42 rose kernel: [    1.604203] pnp 00:07: [io  0x0062-0x0063]
Jun  7 21:25:42 rose kernel: [    1.604204] pnp 00:07: [io  0x0065-0x006f]
Jun  7 21:25:42 rose kernel: [    1.604205] pnp 00:07: [io  0x0072-0x007f]
Jun  7 21:25:42 rose kernel: [    1.604206] pnp 00:07: [io  0x0080]
Jun  7 21:25:42 rose kernel: [    1.604207] pnp 00:07: [io  0x0084-0x0086]
Jun  7 21:25:42 rose kernel: [    1.604208] pnp 00:07: [io  0x0088]
Jun  7 21:25:42 rose kernel: [    1.604209] pnp 00:07: [io  0x008c-0x008e]
Jun  7 21:25:42 rose kernel: [    1.604209] pnp 00:07: [io  0x0090-0x009f]
Jun  7 21:25:42 rose kernel: [    1.604210] pnp 00:07: [io  0x00a2-0x00bf]
Jun  7 21:25:42 rose kernel: [    1.604211] pnp 00:07: [io  0x00e0-0x00ef]
Jun  7 21:25:42 rose kernel: [    1.604212] pnp 00:07: [io  0x04d0-0x04d1]
Jun  7 21:25:42 rose kernel: [    1.604243] system 00:07: [io  0x04d0-0x04d1] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604245] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  7 21:25:42 rose kernel: [    1.604249] pnp 00:08: [io  0x00f0-0x00ff]
Jun  7 21:25:42 rose kernel: [    1.604253] pnp 00:08: [irq 13]
Jun  7 21:25:42 rose kernel: [    1.604268] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun  7 21:25:42 rose kernel: [    1.604281] pnp 00:09: [io  0x0060]
Jun  7 21:25:42 rose kernel: [    1.604282] pnp 00:09: [io  0x0064]
Jun  7 21:25:42 rose kernel: [    1.604285] pnp 00:09: [irq 1]
Jun  7 21:25:42 rose kernel: [    1.604300] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jun  7 21:25:42 rose kernel: [    1.604461] pnp 00:0a: [io  0x03f8-0x03ff]
Jun  7 21:25:42 rose kernel: [    1.604465] pnp 00:0a: [irq 4]
Jun  7 21:25:42 rose kernel: [    1.604466] pnp 00:0a: [dma 0 disabled]
Jun  7 21:25:42 rose kernel: [    1.604493] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
Jun  7 21:25:42 rose kernel: [    1.604601] pnp 00:0b: [io  0x0400-0x0453]
Jun  7 21:25:42 rose kernel: [    1.604602] pnp 00:0b: [io  0x0458-0x047f]
Jun  7 21:25:42 rose kernel: [    1.604604] pnp 00:0b: [io  0x1180-0x119f]
Jun  7 21:25:42 rose kernel: [    1.604605] pnp 00:0b: [io  0x0500-0x057f]
Jun  7 21:25:42 rose kernel: [    1.604606] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Jun  7 21:25:42 rose kernel: [    1.604607] pnp 00:0b: [mem 0xfec00000-0xfecfffff]
Jun  7 21:25:42 rose kernel: [    1.604608] pnp 00:0b: [mem 0xfed08000-0xfed08fff]
Jun  7 21:25:42 rose kernel: [    1.604609] pnp 00:0b: [mem 0xff000000-0xffffffff]
Jun  7 21:25:42 rose kernel: [    1.604636] system 00:0b: [io  0x0400-0x0453] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604637] system 00:0b: [io  0x0458-0x047f] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604638] system 00:0b: [io  0x1180-0x119f] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604640] system 00:0b: [io  0x0500-0x057f] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604641] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604643] system 00:0b: [mem 0xfec00000-0xfecfffff] could not be reserved
Jun  7 21:25:42 rose kernel: [    1.604644] system 00:0b: [mem 0xfed08000-0xfed08fff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604646] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604647] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun  7 21:25:42 rose kernel: [    1.604669] pnp 00:0c: [io  0x0454-0x0457]
Jun  7 21:25:42 rose kernel: [    1.604691] system 00:0c: [io  0x0454-0x0457] has been reserved
Jun  7 21:25:42 rose kernel: [    1.604693] system 00:0c: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Jun  7 21:25:42 rose kernel: [    1.604757] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
Jun  7 21:25:42 rose kernel: [    1.604780] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
Jun  7 21:25:42 rose kernel: [    1.604875] pnp: PnP ACPI: found 14 devices
Jun  7 21:25:42 rose kernel: [    1.604876] ACPI: ACPI bus type pnp unregistered
Jun  7 21:25:42 rose kernel: [    1.610305] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun  7 21:25:42 rose kernel: [    1.610306] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jun  7 21:25:42 rose kernel: [    1.610308] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfa0fffff]
Jun  7 21:25:42 rose kernel: [    1.610310] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdbffffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.610313] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun  7 21:25:42 rose kernel: [    1.610314] pci 0000:00:1c.0:   bridge window [io  disabled]
Jun  7 21:25:42 rose kernel: [    1.610319] pci 0000:00:1c.0:   bridge window [mem disabled]
Jun  7 21:25:42 rose kernel: [    1.610323] pci 0000:00:1c.0:   bridge window [mem pref disabled]
Jun  7 21:25:42 rose kernel: [    1.610330] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Jun  7 21:25:42 rose kernel: [    1.610333] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
Jun  7 21:25:42 rose kernel: [    1.610338] pci 0000:00:1c.4:   bridge window [mem disabled]
Jun  7 21:25:42 rose kernel: [    1.610342] pci 0000:00:1c.4:   bridge window [mem 0xdc100000-0xdc1fffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.610349] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
Jun  7 21:25:42 rose kernel: [    1.610350] pci 0000:00:1c.5:   bridge window [io  disabled]
Jun  7 21:25:42 rose kernel: [    1.610356] pci 0000:00:1c.5:   bridge window [mem 0xfa100000-0xfa1fffff]
Jun  7 21:25:42 rose kernel: [    1.610360] pci 0000:00:1c.5:   bridge window [mem pref disabled]
Jun  7 21:25:42 rose kernel: [    1.610367] pci 0000:00:1c.6: PCI bridge to [bus 05-05]
Jun  7 21:25:42 rose kernel: [    1.610368] pci 0000:00:1c.6:   bridge window [io  disabled]
Jun  7 21:25:42 rose kernel: [    1.610373] pci 0000:00:1c.6:   bridge window [mem disabled]
Jun  7 21:25:42 rose kernel: [    1.610377] pci 0000:00:1c.6:   bridge window [mem pref disabled]
Jun  7 21:25:42 rose kernel: [    1.610384] pci 0000:06:00.0: PCI bridge to [bus 07-07]
Jun  7 21:25:42 rose kernel: [    1.610385] pci 0000:06:00.0:   bridge window [io  disabled]
Jun  7 21:25:42 rose kernel: [    1.610393] pci 0000:06:00.0:   bridge window [mem disabled]
Jun  7 21:25:42 rose kernel: [    1.610399] pci 0000:06:00.0:   bridge window [mem pref disabled]
Jun  7 21:25:42 rose kernel: [    1.610409] pci 0000:00:1c.7: PCI bridge to [bus 06-07]
Jun  7 21:25:42 rose kernel: [    1.610410] pci 0000:00:1c.7:   bridge window [io  disabled]
Jun  7 21:25:42 rose kernel: [    1.610415] pci 0000:00:1c.7:   bridge window [mem disabled]
Jun  7 21:25:42 rose kernel: [    1.610419] pci 0000:00:1c.7:   bridge window [mem pref disabled]
Jun  7 21:25:42 rose kernel: [    1.610433] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  7 21:25:42 rose kernel: [    1.610435] pci 0000:00:01.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610443] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  7 21:25:42 rose kernel: [    1.610447] pci 0000:00:1c.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610453] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  7 21:25:42 rose kernel: [    1.610457] pci 0000:00:1c.4: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610463] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jun  7 21:25:42 rose kernel: [    1.610467] pci 0000:00:1c.5: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610475] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun  7 21:25:42 rose kernel: [    1.610479] pci 0000:00:1c.6: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610487] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun  7 21:25:42 rose kernel: [    1.610490] pci 0000:00:1c.7: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610497] pci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  7 21:25:42 rose kernel: [    1.610503] pci 0000:06:00.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.610507] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun  7 21:25:42 rose kernel: [    1.610508] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun  7 21:25:42 rose kernel: [    1.610509] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun  7 21:25:42 rose kernel: [    1.610510] pci_bus 0000:00: resource 7 [mem 0x000c8000-0x000dffff]
Jun  7 21:25:42 rose kernel: [    1.610512] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xffffffff]
Jun  7 21:25:42 rose kernel: [    1.610513] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Jun  7 21:25:42 rose kernel: [    1.610514] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfa0fffff]
Jun  7 21:25:42 rose kernel: [    1.610515] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdbffffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.610517] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun  7 21:25:42 rose kernel: [    1.610518] pci_bus 0000:03: resource 2 [mem 0xdc100000-0xdc1fffff 64bit pref]
Jun  7 21:25:42 rose kernel: [    1.610519] pci_bus 0000:04: resource 1 [mem 0xfa100000-0xfa1fffff]
Jun  7 21:25:42 rose kernel: [    1.610520] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
Jun  7 21:25:42 rose kernel: [    1.610521] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
Jun  7 21:25:42 rose kernel: [    1.610523] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
Jun  7 21:25:42 rose kernel: [    1.610524] pci_bus 0000:06: resource 7 [mem 0x000c8000-0x000dffff]
Jun  7 21:25:42 rose kernel: [    1.610525] pci_bus 0000:06: resource 8 [mem 0xd0000000-0xffffffff]
Jun  7 21:25:42 rose kernel: [    1.610526] pci_bus 0000:07: resource 8 [io  0x0000-0x0cf7]
Jun  7 21:25:42 rose kernel: [    1.610527] pci_bus 0000:07: resource 9 [io  0x0d00-0xffff]
Jun  7 21:25:42 rose kernel: [    1.610529] pci_bus 0000:07: resource 10 [mem 0x000a0000-0x000bffff]
Jun  7 21:25:42 rose kernel: [    1.610530] pci_bus 0000:07: resource 11 [mem 0x000c8000-0x000dffff]
Jun  7 21:25:42 rose kernel: [    1.610531] pci_bus 0000:07: resource 12 [mem 0xd0000000-0xffffffff]
Jun  7 21:25:42 rose kernel: [    1.610548] NET: Registered protocol family 2
Jun  7 21:25:42 rose kernel: [    1.610699] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun  7 21:25:42 rose kernel: [    1.611340] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun  7 21:25:42 rose kernel: [    1.612333] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  7 21:25:42 rose kernel: [    1.612453] TCP: Hash tables configured (established 524288 bind 65536)
Jun  7 21:25:42 rose kernel: [    1.612454] TCP reno registered
Jun  7 21:25:42 rose kernel: [    1.612464] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jun  7 21:25:42 rose kernel: [    1.612491] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jun  7 21:25:42 rose kernel: [    1.612561] NET: Registered protocol family 1
Jun  7 21:25:42 rose kernel: [    1.858206] Freeing initrd memory: 12828k freed
Jun  7 21:25:42 rose kernel: [    1.869285] pci 0000:01:00.0: Boot video device
Jun  7 21:25:42 rose kernel: [    1.869350] PCI: CLS 64 bytes, default 64
Jun  7 21:25:42 rose kernel: [    1.869352] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun  7 21:25:42 rose kernel: [    1.869353] Placing 64MB software IO TLB between ffff8800cb18c000 - ffff8800cf18c000
Jun  7 21:25:42 rose kernel: [    1.869354] software IO TLB at phys 0xcb18c000 - 0xcf18c000
Jun  7 21:25:42 rose kernel: [    1.869763] audit: initializing netlink socket (disabled)
Jun  7 21:25:42 rose kernel: [    1.869770] type=2000 audit(1307481932.690:1): initialized
Jun  7 21:25:42 rose kernel: [    1.878137] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun  7 21:25:42 rose kernel: [    1.879071] VFS: Disk quotas dquot_6.5.2
Jun  7 21:25:42 rose kernel: [    1.879102] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  7 21:25:42 rose kernel: [    1.879458] fuse init (API version 7.16)
Jun  7 21:25:42 rose kernel: [    1.879507] msgmni has been set to 15964
Jun  7 21:25:42 rose kernel: [    1.879642] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun  7 21:25:42 rose kernel: [    1.879658] io scheduler noop registered
Jun  7 21:25:42 rose kernel: [    1.879659] io scheduler deadline registered
Jun  7 21:25:42 rose kernel: [    1.879681] io scheduler cfq registered (default)
Jun  7 21:25:42 rose kernel: [    1.879737] pcieport 0000:00:01.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.879755] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    1.879799] pcieport 0000:00:1c.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.879853] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    1.879932] pcieport 0000:00:1c.4: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.879986] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    1.880067] pcieport 0000:00:1c.5: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.880120] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    1.880199] pcieport 0000:00:1c.6: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    1.880252] pcieport 0000:00:1c.6: irq 44 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    1.880334] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880335] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880337] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880338] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
Jun  7 21:25:42 rose kernel: [    1.880356] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880360] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Jun  7 21:25:42 rose kernel: [    1.880376] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880377] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880381] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
Jun  7 21:25:42 rose kernel: [    1.880398] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880399] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880403] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
Jun  7 21:25:42 rose kernel: [    1.880420] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
Jun  7 21:25:42 rose kernel: [    1.880424] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
Jun  7 21:25:42 rose kernel: [    1.880432] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  7 21:25:42 rose kernel: [    1.880444] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  7 21:25:42 rose kernel: [    1.880468] intel_idle: MWAIT substates: 0x1120
Jun  7 21:25:42 rose kernel: [    1.880469] intel_idle: v0.4 model 0x2A
Jun  7 21:25:42 rose kernel: [    1.880470] intel_idle: lapic_timer_reliable_states 0xffffffff
Jun  7 21:25:42 rose kernel: [    1.880546] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun  7 21:25:42 rose kernel: [    1.880549] ACPI: Power Button [PWRB]
Jun  7 21:25:42 rose kernel: [    1.880572] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun  7 21:25:42 rose kernel: [    1.880574] ACPI: Power Button [PWRF]
Jun  7 21:25:42 rose kernel: [    1.880677] ACPI: acpi_idle yielding to intel_idle
Jun  7 21:25:42 rose kernel: [    1.882175] ERST: Table is not found!
Jun  7 21:25:42 rose kernel: [    1.882212] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun  7 21:25:42 rose kernel: [    1.902717] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  7 21:25:42 rose kernel: [    2.150136] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  7 21:25:42 rose kernel: [    2.150306] Linux agpgart interface v0.103
Jun  7 21:25:42 rose kernel: [    2.150932] brd: module loaded
Jun  7 21:25:42 rose kernel: [    2.151197] loop: module loaded
Jun  7 21:25:42 rose kernel: [    2.151239] i2c-core: driver [adp5520] using legacy suspend method
Jun  7 21:25:42 rose kernel: [    2.151240] i2c-core: driver [adp5520] using legacy resume method
Jun  7 21:25:42 rose kernel: [    2.151281] ata_piix 0000:00:1f.2: version 2.13
Jun  7 21:25:42 rose kernel: [    2.151289] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  7 21:25:42 rose kernel: [    2.151293] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jun  7 21:25:42 rose kernel: [    2.151322] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    2.151489] scsi0 : ata_piix
Jun  7 21:25:42 rose kernel: [    2.151534] scsi1 : ata_piix
Jun  7 21:25:42 rose kernel: [    2.152295] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf090 irq 14
Jun  7 21:25:42 rose kernel: [    2.152300] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf098 irq 15
Jun  7 21:25:42 rose kernel: [    2.152312] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun  7 21:25:42 rose kernel: [    2.152315] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jun  7 21:25:42 rose kernel: [    2.152336] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
Jun  7 21:25:42 rose kernel: [    2.152342] ata_piix 0000:00:1f.5: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    2.152460] scsi2 : ata_piix
Jun  7 21:25:42 rose kernel: [    2.152492] scsi3 : ata_piix
Jun  7 21:25:42 rose kernel: [    2.153018] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 19
Jun  7 21:25:42 rose kernel: [    2.153019] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 19
Jun  7 21:25:42 rose kernel: [    2.153178] Fixed MDIO Bus: probed
Jun  7 21:25:42 rose kernel: [    2.153193] PPP generic driver version 2.4.2
Jun  7 21:25:42 rose kernel: [    2.153212] tun: Universal TUN/TAP device driver, 1.6
Jun  7 21:25:42 rose kernel: [    2.153213] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  7 21:25:42 rose kernel: [    2.153259] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  7 21:25:42 rose kernel: [    2.153269] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  7 21:25:42 rose kernel: [    2.153289] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    2.153292] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun  7 21:25:42 rose kernel: [    2.153314] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun  7 21:25:42 rose kernel: [    2.153356] ehci_hcd 0000:00:1a.0: debug port 2
Jun  7 21:25:42 rose kernel: [    2.157241] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Jun  7 21:25:42 rose kernel: [    2.157252] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfa206000
Jun  7 21:25:42 rose kernel: [    2.178358] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun  7 21:25:42 rose kernel: [    2.178455] hub 1-0:1.0: USB hub found
Jun  7 21:25:42 rose kernel: [    2.178457] hub 1-0:1.0: 2 ports detected
Jun  7 21:25:42 rose kernel: [    2.178499] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun  7 21:25:42 rose kernel: [    2.178508] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    2.178511] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun  7 21:25:42 rose kernel: [    2.178533] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun  7 21:25:42 rose kernel: [    2.178573] ehci_hcd 0000:00:1d.0: debug port 2
Jun  7 21:25:42 rose kernel: [    2.182438] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Jun  7 21:25:42 rose kernel: [    2.182448] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfa205000
Jun  7 21:25:42 rose kernel: [    2.198302] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun  7 21:25:42 rose kernel: [    2.198388] hub 2-0:1.0: USB hub found
Jun  7 21:25:42 rose kernel: [    2.198390] hub 2-0:1.0: 2 ports detected
Jun  7 21:25:42 rose kernel: [    2.198424] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  7 21:25:42 rose kernel: [    2.198430] uhci_hcd: USB Universal Host Controller Interface driver
Jun  7 21:25:42 rose kernel: [    2.198499] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun  7 21:25:42 rose kernel: [    2.198500] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun  7 21:25:42 rose kernel: [    2.199188] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  7 21:25:42 rose kernel: [    2.199245] mousedev: PS/2 mouse device common for all mice
Jun  7 21:25:42 rose kernel: [    2.199313] rtc_cmos 00:05: RTC can wake from S4
Jun  7 21:25:42 rose kernel: [    2.199348] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jun  7 21:25:42 rose kernel: [    2.199379] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun  7 21:25:42 rose kernel: [    2.199430] device-mapper: uevent: version 1.0.3
Jun  7 21:25:42 rose kernel: [    2.199473] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Jun  7 21:25:42 rose kernel: [    2.199508] device-mapper: multipath: version 1.2.0 loaded
Jun  7 21:25:42 rose kernel: [    2.199509] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  7 21:25:42 rose kernel: [    2.199664] cpuidle: using governor ladder
Jun  7 21:25:42 rose kernel: [    2.199829] cpuidle: using governor menu
Jun  7 21:25:42 rose kernel: [    2.199950] TCP cubic registered
Jun  7 21:25:42 rose kernel: [    2.200012] NET: Registered protocol family 10
Jun  7 21:25:42 rose kernel: [    2.200260] NET: Registered protocol family 17
Jun  7 21:25:42 rose kernel: [    2.200268] Registering the dns_resolver key type
Jun  7 21:25:42 rose kernel: [    2.201199] PM: Hibernation image not present or could not be loaded.
Jun  7 21:25:42 rose kernel: [    2.201203] registered taskstats version 1
Jun  7 21:25:42 rose kernel: [    2.201475]   Magic number: 15:128:449
Jun  7 21:25:42 rose kernel: [    2.201567] rtc_cmos 00:05: setting system clock to 2011-06-07 21:25:33 UTC (1307481933)
Jun  7 21:25:42 rose kernel: [    2.201569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  7 21:25:42 rose kernel: [    2.201570] EDD information not available.
Jun  7 21:25:42 rose kernel: [    2.217980] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jun  7 21:25:42 rose kernel: [    2.497468] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun  7 21:25:42 rose kernel: [    2.647730] hub 1-1:1.0: USB hub found
Jun  7 21:25:42 rose kernel: [    2.647810] hub 1-1:1.0: 6 ports detected
Jun  7 21:25:42 rose kernel: [    2.766705] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun  7 21:25:42 rose kernel: [    2.866405] Refined TSC clocksource calibration: 3392.293 MHz.
Jun  7 21:25:42 rose kernel: [    2.866410] Switching to clocksource tsc
Jun  7 21:25:42 rose kernel: [    2.916951] hub 2-1:1.0: USB hub found
Jun  7 21:25:42 rose kernel: [    2.917036] hub 2-1:1.0: 8 ports detected
Jun  7 21:25:42 rose kernel: [    3.006088] ata2.00: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jun  7 21:25:42 rose kernel: [    3.006103] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  7 21:25:42 rose kernel: [    3.006252] ata1.00: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jun  7 21:25:42 rose kernel: [    3.006275] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  7 21:25:42 rose kernel: [    3.105859] ata2.00: ATA-9: OCZ-VERTEX3, 2.02, max UDMA/133
Jun  7 21:25:42 rose kernel: [    3.105861] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  7 21:25:42 rose kernel: [    3.106033] ata2.01: ATA-8: WDC WD1003FBYX-01Y7B0, 01.01V01, max UDMA/133
Jun  7 21:25:42 rose kernel: [    3.106037] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  7 21:25:42 rose kernel: [    3.165694] ata1.00: ATA-9: OCZ-VERTEX3, 2.02, max UDMA/133
Jun  7 21:25:42 rose kernel: [    3.165696] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  7 21:25:42 rose kernel: [    3.165699] ata1.01: ATAPI: HL-DT-ST BDDVDRW CH10LS20, 1.00, max UDMA/133
Jun  7 21:25:42 rose kernel: [    3.195621] usb 2-1.6: new low speed USB device using ehci_hcd and address 3
Jun  7 21:25:42 rose kernel: [    3.265409] ata2.00: configured for UDMA/133
Jun  7 21:25:42 rose kernel: [    3.286367] ata2.01: configured for UDMA/133
Jun  7 21:25:42 rose kernel: [    3.365112] ata1.00: configured for UDMA/133
Jun  7 21:25:42 rose kernel: [    3.404998] ata1.01: configured for UDMA/133
Jun  7 21:25:42 rose kernel: [    3.410837] scsi 0:0:0:0: Direct-Access     ATA      OCZ-VERTEX3      2.02 PQ: 0 ANSI: 5
Jun  7 21:25:42 rose kernel: [    3.410915] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  7 21:25:42 rose kernel: [    3.419941] scsi 0:0:1:0: CD-ROM            HL-DT-ST BDDVDRW CH10LS20 1.00 PQ: 0 ANSI: 5
Jun  7 21:25:42 rose kernel: [    3.419977] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jun  7 21:25:42 rose kernel: [    3.434798] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  7 21:25:42 rose kernel: [    3.434802] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun  7 21:25:42 rose kernel: [    3.434868] sr 0:0:1:0: Attached scsi CD-ROM sr0
Jun  7 21:25:42 rose kernel: [    3.434884] sd 0:0:0:0: [sda] Write Protect is off
Jun  7 21:25:42 rose kernel: [    3.434887] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun  7 21:25:42 rose kernel: [    3.434904] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jun  7 21:25:42 rose kernel: [    3.434994] scsi 1:0:0:0: Direct-Access     ATA      OCZ-VERTEX3      2.02 PQ: 0 ANSI: 5
Jun  7 21:25:42 rose kernel: [    3.435061] sd 1:0:0:0: Attached scsi generic sg2 type 0
Jun  7 21:25:42 rose kernel: [    3.435079] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jun  7 21:25:42 rose kernel: [    3.435109] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1003FBYX-0 01.0 PQ: 0 ANSI: 5
Jun  7 21:25:42 rose kernel: [    3.435127] sd 1:0:0:0: [sdb] Write Protect is off
Jun  7 21:25:42 rose kernel: [    3.435128] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun  7 21:25:42 rose kernel: [    3.435138] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  7 21:25:42 rose kernel: [    3.435187] sd 1:0:1:0: Attached scsi generic sg3 type 0
Jun  7 21:25:42 rose kernel: [    3.435250] sd 1:0:1:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun  7 21:25:42 rose kernel: [    3.435358] sd 1:0:1:0: [sdc] Write Protect is off
Jun  7 21:25:42 rose kernel: [    3.435360] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
Jun  7 21:25:42 rose kernel: [    3.435608]  sdb: sdb1
Jun  7 21:25:42 rose kernel: [    3.435630] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  7 21:25:42 rose kernel: [    3.435797] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun  7 21:25:42 rose kernel: [    3.442263] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  7 21:25:42 rose kernel: [    3.442899]  sda: sda1 sda2 sda3
Jun  7 21:25:42 rose kernel: [    3.443137] sd 0:0:0:0: [sda] Attached SCSI disk
Jun  7 21:25:42 rose kernel: [    3.446297]  sdc: sdc1
Jun  7 21:25:42 rose kernel: [    3.446474] sd 1:0:1:0: [sdc] Attached SCSI disk
Jun  7 21:25:42 rose kernel: [    3.447449] Freeing unused kernel memory: 956k freed
Jun  7 21:25:42 rose kernel: [    3.447533] Write protecting the kernel read-only data: 10240k
Jun  7 21:25:42 rose kernel: [    3.448114] Freeing unused kernel memory: 184k freed
Jun  7 21:25:42 rose kernel: [    3.450961] Freeing unused kernel memory: 1444k freed
Jun  7 21:25:42 rose kernel: [    3.461885] <30>udev[96]: starting version 167
Jun  7 21:25:42 rose kernel: [    3.474028] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun  7 21:25:42 rose kernel: [    3.474046] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  7 21:25:42 rose kernel: [    3.474093] r8169 0000:03:00.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    3.474098] r8169 0000:03:00.0: (unregistered net_device): unknown MAC, using family default
Jun  7 21:25:42 rose kernel: [    3.474173] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    3.474437] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xffffc90000c68000, 00:25:22:b1:e3:86, XID 0c200000 IRQ 45
Jun  7 21:25:42 rose kernel: [    3.491722] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input3
Jun  7 21:25:42 rose kernel: [    3.491777] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:1d.0-1.6/input0
Jun  7 21:25:42 rose kernel: [    3.491784] usbcore: registered new interface driver usbhid
Jun  7 21:25:42 rose kernel: [    3.491785] usbhid: USB HID core driver
Jun  7 21:25:42 rose kernel: [    3.496983] FDC 0 is a post-1991 82077
Jun  7 21:25:42 rose kernel: [    3.673211] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun  7 21:25:42 rose kernel: [    8.832674] Adding 7845884k swap on /dev/sda2.  Priority:-1 extents:1 across:7845884k SS
Jun  7 21:25:42 rose kernel: [    8.855638] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jun  7 21:25:42 rose kernel: [    8.906663] <30>udev[360]: starting version 167
Jun  7 21:25:42 rose kernel: [    9.395442] lp: driver loaded but no devices found
Jun  7 21:25:42 rose kernel: [    9.400834] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  7 21:25:42 rose kernel: [    9.400857] xhci_hcd 0000:04:00.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    9.400862] xhci_hcd 0000:04:00.0: xHCI Host Controller
Jun  7 21:25:42 rose kernel: [    9.400915] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Jun  7 21:25:42 rose kernel: [    9.450167] nvidia: module license 'NVIDIA' taints kernel.
Jun  7 21:25:42 rose kernel: [    9.450170] Disabling lock debugging due to kernel taint
Jun  7 21:25:42 rose kernel: [    9.527482] xhci_hcd 0000:04:00.0: irq 17, io mem 0xfa100000
Jun  7 21:25:42 rose kernel: [    9.527506] xhci_hcd 0000:04:00.0: Failed to enable MSI-X
Jun  7 21:25:42 rose kernel: [    9.527643] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [    9.527713] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
Jun  7 21:25:42 rose kernel: [    9.527819] xHCI xhci_add_endpoint called for root hub
Jun  7 21:25:42 rose kernel: [    9.527821] xHCI xhci_check_bandwidth called for root hub
Jun  7 21:25:42 rose kernel: [    9.527869] hub 3-0:1.0: USB hub found
Jun  7 21:25:42 rose kernel: [    9.527873] hub 3-0:1.0: 4 ports detected
Jun  7 21:25:42 rose kernel: [    9.776148] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  7 21:25:42 rose kernel: [    9.776153] nvidia 0000:01:00.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [    9.776157] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun  7 21:25:42 rose kernel: [    9.776254] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Jun  7 21:25:42 rose kernel: [    9.906291] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [    9.906296] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   10.175521] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   10.175526] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   10.197765] type=1400 audit(1307474741.508:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=550 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.197821] type=1400 audit(1307474741.508:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=528 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.198320] type=1400 audit(1307474741.508:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=550 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.198375] type=1400 audit(1307474741.508:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=528 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.198653] type=1400 audit(1307474741.508:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=550 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.198707] type=1400 audit(1307474741.508:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=528 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.223033] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun  7 21:25:42 rose kernel: [   10.223090] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Jun  7 21:25:42 rose kernel: [   10.223118] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [   10.320214] hda_codec: ALC892: BIOS auto-probing.
Jun  7 21:25:42 rose kernel: [   10.326964] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Jun  7 21:25:42 rose kernel: [   10.327061] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun  7 21:25:42 rose kernel: [   10.327064] hda_intel: Disable MSI for Nvidia chipset
Jun  7 21:25:42 rose kernel: [   10.327148] HDA Intel 0000:01:00.1: setting latency timer to 64
Jun  7 21:25:42 rose kernel: [   10.444865] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   10.444868] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   10.710437] type=1400 audit(1307474742.018:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=748 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.711006] type=1400 audit(1307474742.018:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=747 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.711542] type=1400 audit(1307474742.018:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=747 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.712642] type=1400 audit(1307474742.018:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=745 comm="apparmor_parser"
Jun  7 21:25:42 rose kernel: [   10.713964] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   10.713974] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose cron[811]: (CRON) INFO (pidfile fd = 3)
Jun  7 21:25:42 rose acpid: starting up with proc fs
Jun  7 21:25:42 rose anacron[825]: Anacron 2.3 started on 2011-06-07
Jun  7 21:25:42 rose cron[828]: (CRON) STARTUP (fork ok)
Jun  7 21:25:42 rose init: apport pre-start process (803) terminated with status 1
Jun  7 21:25:42 rose init: apport post-stop process (835) terminated with status 1
Jun  7 21:25:42 rose anacron[825]: Will run job `cron.daily' in 5 min.
Jun  7 21:25:42 rose anacron[825]: Jobs will be executed sequentially
Jun  7 21:25:42 rose cron[828]: (CRON) INFO (Running @reboot jobs)
Jun  7 21:25:42 rose acpid: 32 rules loaded
Jun  7 21:25:42 rose acpid: waiting for events: event logging is off
Jun  7 21:25:42 rose NetworkManager[900]: <info> NetworkManager (version 0.8.3.998) is starting...
Jun  7 21:25:42 rose NetworkManager[900]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun  7 21:25:42 rose avahi-daemon[910]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jun  7 21:25:42 rose NetworkManager[900]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun  7 21:25:42 rose avahi-daemon[910]: Successfully dropped root privileges.
Jun  7 21:25:42 rose avahi-daemon[910]: avahi-daemon 0.6.30 starting up.
Jun  7 21:25:42 rose NetworkManager[900]: <info> trying to start the modem manager...
Jun  7 21:25:42 rose avahi-daemon[910]: Successfully called chroot().
Jun  7 21:25:42 rose avahi-daemon[910]: Successfully dropped remaining capabilities.
Jun  7 21:25:42 rose avahi-daemon[910]: Loading service file /services/udisks.service.
Jun  7 21:25:42 rose avahi-daemon[910]: Network interface enumeration completed.
Jun  7 21:25:42 rose avahi-daemon[910]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun  7 21:25:42 rose avahi-daemon[910]: Server startup complete. Host name is rose.local. Local service cookie is 1303290221.
Jun  7 21:25:42 rose avahi-daemon[910]: Service "rose" (/services/udisks.service) successfully established.
Jun  7 21:25:42 rose polkitd[922]: started daemon version 0.101 using authority implementation `local' version `0.101'
Jun  7 21:25:42 rose NetworkManager[900]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  7 21:25:42 rose modem-manager[915]: <info>  ModemManager (version 0.4) starting...
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Option High-Speed
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin ZTE
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin SimTech
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: init!
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: update_system_hostname
Jun  7 21:25:42 rose NetworkManager[900]:    SCPluginIfupdown: management mode: unmanaged
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Huawei
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0, iface: eth0)
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: end _init.
Jun  7 21:25:42 rose NetworkManager[900]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Nokia
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Option
Jun  7 21:25:42 rose NetworkManager[900]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  7 21:25:42 rose NetworkManager[900]:    Ifupdown: get unmanaged devices count: 0
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: (25525600) ... get_connections.
Jun  7 21:25:42 rose NetworkManager[900]:    SCPlugin-Ifupdown: (25525600) ... get_connections (managed=false): return empty list.
Jun  7 21:25:42 rose NetworkManager[900]:    Ifupdown: get unmanaged devices count: 0
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Sierra
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Novatel
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Generic
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Gobi
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin MotoC
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Linktop
Jun  7 21:25:42 rose NetworkManager[900]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  7 21:25:42 rose NetworkManager[900]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  7 21:25:42 rose NetworkManager[900]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  7 21:25:42 rose NetworkManager[900]: <info> Networking is enabled by state file
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Ericsson MBM
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin X22X
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): carrier is OFF
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin Longcheer
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): now managed
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): bringing up device.
Jun  7 21:25:42 rose modem-manager[915]: <info>  Loaded plugin AnyData
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): preparing device.
Jun  7 21:25:42 rose NetworkManager[900]: <info> (eth0): deactivating device (reason: 2).
Jun  7 21:25:42 rose NetworkManager[900]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
Jun  7 21:25:42 rose NetworkManager[900]: <info> modem-manager is now available
Jun  7 21:25:42 rose NetworkManager[900]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  7 21:25:42 rose NetworkManager[900]: <info> Trying to start the supplicant...
Jun  7 21:25:42 rose kernel: [   10.904686] r8169 0000:03:00.0: eth0: link down
Jun  7 21:25:42 rose kernel: [   10.904693] r8169 0000:03:00.0: eth0: link down
Jun  7 21:25:42 rose kernel: [   10.905062] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  7 21:25:42 rose kernel: [   10.981898] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun  7 21:25:42 rose kernel: [   10.983194] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   10.983197] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   10.983282] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Jun  7 21:25:42 rose kernel: [   11.102929] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   11.102932] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   11.372090] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   11.372093] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:42 rose kernel: [   11.641329] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:42 rose kernel: [   11.641334] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:43 rose kernel: [   11.910556] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:43 rose kernel: [   11.910561] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:43 rose kernel: [   12.179785] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:43 rose kernel: [   12.179790] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:43 rose kernel: [   12.179869] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Jun  7 21:25:43 rose kernel: [   12.299444] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:43 rose kernel: [   12.299449] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): carrier now ON (device state 2)
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) starting connection 'Auto eth0'
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  7 21:25:43 rose NetworkManager[900]: <info> dhclient started with pid 1031
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  7 21:25:43 rose dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jun  7 21:25:43 rose dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jun  7 21:25:43 rose dhclient: All rights reserved.
Jun  7 21:25:43 rose dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  7 21:25:43 rose dhclient: 
Jun  7 21:25:43 rose kernel: [   12.505072] r8169 0000:03:00.0: eth0: link up
Jun  7 21:25:43 rose kernel: [   12.505436] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  7 21:25:43 rose kernel: [   12.568673] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:43 rose kernel: [   12.568675] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:43 rose dhclient: Listening on LPF/eth0/00:25:22:b1:e3:86
Jun  7 21:25:43 rose dhclient: Sending on   LPF/eth0/00:25:22:b1:e3:86
Jun  7 21:25:43 rose dhclient: Sending on   Socket/fallback
Jun  7 21:25:43 rose dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun  7 21:25:43 rose dhclient: DHCPOFFER of 192.168.2.100 from 192.168.2.1
Jun  7 21:25:43 rose dhclient: DHCPREQUEST of 192.168.2.100 on eth0 to 255.255.255.255 port 67
Jun  7 21:25:43 rose dhclient: DHCPACK of 192.168.2.100 from 192.168.2.1
Jun  7 21:25:43 rose dhclient: bound to 192.168.2.100 -- renewal in 18676 seconds.
Jun  7 21:25:43 rose NetworkManager[900]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  7 21:25:43 rose NetworkManager[900]: <info>   address 192.168.2.100
Jun  7 21:25:43 rose NetworkManager[900]: <info>   prefix 24 (255.255.255.0)
Jun  7 21:25:43 rose NetworkManager[900]: <info>   gateway 192.168.2.1
Jun  7 21:25:43 rose NetworkManager[900]: <info>   nameserver '192.168.2.1'
Jun  7 21:25:43 rose NetworkManager[900]: <info> Scheduling stage 5
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  7 21:25:43 rose NetworkManager[900]: <info> Done scheduling stage 5
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  7 21:25:43 rose NetworkManager[900]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun  7 21:25:43 rose avahi-daemon[910]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.100.
Jun  7 21:25:43 rose avahi-daemon[910]: New relevant interface eth0.IPv4 for mDNS.
Jun  7 21:25:43 rose avahi-daemon[910]: Registering new address record for 192.168.2.100 on eth0.IPv4.
Jun  7 21:25:43 rose kernel: [   12.625201] ppdev: user-space parallel port driver
Jun  7 21:25:44 rose init: udev-fallback-graphics main process (1046) terminated with status 1
Jun  7 21:25:44 rose gdm-binary[1073]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  7 21:25:44 rose init: plymouth-splash main process (1070) terminated with status 1
Jun  7 21:25:44 rose gdm-binary[1073]: WARNING: Unable to find users: no seat-id found
Jun  7 21:25:44 rose gdm-simple-slave[1143]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  7 21:25:44 rose acpid: client connected from 1146[0:0]
Jun  7 21:25:44 rose acpid: 1 client rule loaded
Jun  7 21:25:44 rose kernel: [   12.837902] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:44 rose kernel: [   12.837905] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:44 rose kernel: [   12.858528] ioremap error for 0xcf5db000-0xcf5dc000, requested 0x10, got 0x0
Jun  7 21:25:44 rose kernel: [   13.107115] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:44 rose kernel: [   13.107117] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:44 rose kernel: [   13.376371] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:44 rose kernel: [   13.376374] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:44 rose kernel: [   13.376377] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Jun  7 21:25:44 rose acpid: client connected from 1146[0:0]
Jun  7 21:25:44 rose acpid: 1 client rule loaded
Jun  7 21:25:44 rose kernel: [   13.496000] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:44 rose kernel: [   13.496002] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:44 rose NetworkManager[900]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun  7 21:25:44 rose NetworkManager[900]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  7 21:25:44 rose NetworkManager[900]: <info> Activation (eth0) successful, device activated.
Jun  7 21:25:44 rose NetworkManager[900]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  7 21:25:45 rose kernel: [   13.765242] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:45 rose kernel: [   13.765246] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:45 rose gdm-session-worker[1241]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun  7 21:25:45 rose kernel: [   14.034484] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:45 rose kernel: [   14.034490] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:45 rose gdm-simple-greeter[1240]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jun  7 21:25:45 rose gdm-simple-greeter[1240]: WARNING: Unable to load CK history: no seat-id found
Jun  7 21:25:45 rose kernel: [   14.303704] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:45 rose kernel: [   14.303707] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:45 rose avahi-daemon[910]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::225:22ff:feb1:e386.
Jun  7 21:25:45 rose avahi-daemon[910]: New relevant interface eth0.IPv6 for mDNS.
Jun  7 21:25:45 rose avahi-daemon[910]: Registering new address record for fe80::225:22ff:feb1:e386 on eth0.*.
Jun  7 21:25:45 rose kernel: [   14.461647] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun  7 21:25:45 rose kernel: [   14.572972] xhci_hcd 0000:04:00.0: Unknown completion code 192 for reset device command.
Jun  7 21:25:45 rose kernel: [   14.572974] usb 3-3: Cannot reset HCD device state
Jun  7 21:25:45 rose kernel: [   14.572976] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Jun  7 21:25:45 rose kernel: [   14.572989] hub 3-0:1.0: unable to enumerate USB device on port 3
Jun  7 21:25:53 rose ntpdate[1217]: step time server 91.189.94.4 offset 0.679738 sec
Jun  7 21:25:55 rose kernel: [   23.337850] eth0: no IPv6 routers present
Jun  7 21:26:42 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:26:42 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:26:42 rose acpid: client connected from 1146[0:0]
Jun  7 21:26:42 rose acpid: 1 client rule loaded
Jun  7 21:26:43 rose acpid: client connected from 1146[0:0]
Jun  7 21:26:43 rose acpid: 1 client rule loaded
Jun  7 21:26:46 rose gdm-session-worker[1241]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  7 21:26:49 rose gdm-session-worker[1241]: pam_sm_authenticate: Called
Jun  7 21:26:49 rose gdm-session-worker[1241]: pam_sm_authenticate: username = [phi]
Jun  7 21:26:51 rose rtkit-daemon[1463]: Successfully called chroot.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Successfully dropped privileges.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Successfully limited resources.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Running.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Watchdog thread running.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Canary thread running.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Successfully made thread 1460 of process 1460 (n/a) owned by '1000' high priority at nice level -11.
Jun  7 21:26:51 rose rtkit-daemon[1463]: Supervising 1 threads of 1 processes of 1 users.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Successfully made thread 1697 of process 1460 (n/a) owned by '1000' RT at priority 5.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Supervising 2 threads of 1 processes of 1 users.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Successfully made thread 1698 of process 1460 (n/a) owned by '1000' RT at priority 5.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Supervising 3 threads of 1 processes of 1 users.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Successfully made thread 1699 of process 1460 (n/a) owned by '1000' RT at priority 5.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Supervising 4 threads of 1 processes of 1 users.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Successfully made thread 1704 of process 1704 (n/a) owned by '1000' high priority at nice level -11.
Jun  7 21:26:53 rose rtkit-daemon[1463]: Supervising 5 threads of 2 processes of 1 users.
Jun  7 21:26:53 rose pulseaudio[1704]: pid.c: Daemon already running.
Jun  7 21:26:54 rose kernel: [   81.807272] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Jun  7 21:28:37 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:28:37 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:28:37 rose acpid: client connected from 1146[0:0]
Jun  7 21:28:37 rose acpid: 1 client rule loaded
Jun  7 21:28:37 rose acpid: client connected from 1146[0:0]
Jun  7 21:28:37 rose acpid: 1 client rule loaded
Jun  7 21:30:42 rose anacron[825]: Job `cron.daily' started
Jun  7 21:30:42 rose anacron[1830]: Updated timestamp for job `cron.daily' to 2011-06-07
Jun  7 21:32:34 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:32:34 rose acpid: client 1146[0:0] has disconnected
Jun  7 21:32:34 rose acpid: client connected from 1146[0:0]
Jun  7 21:32:34 rose acpid: 1 client rule loaded
Jun  7 21:32:35 rose acpid: client connected from 1146[0:0]
Jun  7 21:32:35 rose acpid: 1 client rule loaded
```

---

### Post by phibuntu on 2011-06-08
Just to make sure, if it is the upgrade to 11.04 (all Versions 64 bit) or 11.04 itself, I burnt a life distro 11.04 some minutes ago.

The missing Driver lies in 10.10, but no longer in 11.04 (no difference, if you start 11.04 from CD, or if you upgrade from 10.10).

10.10 installed AND 10.10 Life CD both work fine with USB 3!

see also the same bug description on a german forum: [http://forum.ubuntuusers.de/topic/natty-erkennt-usb-3-0-festplatte-nicht-mehr-ma/#post-2862233]("http://forum.ubuntuusers.de/topic/natty-erkennt-usb-3-0-festplatte-nicht-mehr-ma/#post-2862233")

---

### Post by c147258 on 2011-06-24
Hello, 

I upgraded to 11.04 Ubuntu and now I want to install a USB 3.0 Express Card (Expresscard) from AKE. It works very fine in Windows 7 and shows that it is a Renesas Card (chip?). 
Anyway the problem is that the card is sometimes working.. and sometimes not. 

This is the following dmesg output:
```
[  183.120137] usb 9-3: new low speed USB device using xhci_hcd and address 2
[  183.160997] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  183.167987] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  183.172985] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  183.174141] usb 9-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  183.236436] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1c.0/0000:02:00.0/usb9/9-3/9-3:1.0/input/input11
[  183.236619] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:02:00.0-3/input0
[  183.236944] usbcore: registered new interface driver usbhid
[  183.236946] usbhid: USB HID core driver
[  200.779057] usb 9-3: USB disconnect, address 2
[  220.420292] usb 9-1: new SuperSpeed USB device using xhci_hcd and address 3
[  220.441801] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  220.442171] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  220.442545] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  220.443044] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  220.506194] usbcore: registered new interface driver uas
[  220.523246] Initializing USB Mass Storage driver...
[  220.523426] scsi6 : usb-storage 9-1:1.0
[  220.523902] usbcore: registered new interface driver usb-storage
[  220.523906] USB Mass Storage support registered.
[  222.663322] scsi 6:0:0:0: Direct-Access     WD       My Passport 0730 1008 PQ: 0 ANSI: 6
[  222.663801] scsi 6:0:0:1: Enclosure         WD       SES Device       1008 PQ: 0 ANSI: 6
[  222.665210] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  222.665595] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[  227.702064] sd 6:0:0:0: [sdb] 1465081856 512-byte logical blocks: (750 GB/698 GiB)
[  227.702325] sd 6:0:0:0: [sdb] Write Protect is off
[  227.702334] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
[  227.702779] sd 6:0:0:0: [sdb] No Caching mode page present
[  227.702788] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  227.704420] sd 6:0:0:0: [sdb] No Caching mode page present
[  227.704429] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  227.710976]  sdb: sdb1
[  227.714907] sd 6:0:0:0: [sdb] No Caching mode page present
[  227.714916] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  227.714923] sd 6:0:0:0: [sdb] Attached SCSI disk
[  227.794102] ses 6:0:0:1: Attached Enclosure device
[  227.841138] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint

```

As I guess the WARN command is not very good, so I am asking about any suggestion to get rid from it. 

Thank you very much.

---

### Post by c147258 on 2011-06-25
Right now it just worked, but after I rebootet it I get the following message and I am not able to mount/see the external 2,5" WD USB 3.0 harddrive:

```

chris@mydtserv:~$ dmesg | grep xhci
[   18.024995] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.025025] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   18.025031] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   18.025806] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[   18.050348] xhci_hcd 0000:02:00.0: irq 16, io mem 0xf4000000
[   18.050456] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[   18.050460] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[   18.050464] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[   18.062841] xHCI xhci_add_endpoint called for root hub
[   18.062844] xHCI xhci_check_bandwidth called for root hub
[   18.390093] usb 9-3: new high speed USB device using xhci_hcd and address 2
[   68.790052] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
[  119.003220] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
[  169.160323] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
```

---

### Post by zeni on 2011-11-15
hi everyone,
 
since I am pretty new to Ubuntu i first thought it was just me being noobish. But after 2 Days of google and research, its maybe not just me. I'm having a pretty similar problem with Ubuntu server 11.10.
Aslong its plugged into an USB2 my external gets mounted and shown properly (and works fine) but as it is in a USB3 port it just disappears and is not shown with lsusb. Its not even shown in the BIOS (in USB2 it is).
 
My board: Intel DH67CL
External: WD Passport essential SE 1TB
 
do you guys have a similar hardware?

---

### Post by phibuntu on 2011-11-16
Hello Zeni


I don't know my board by heart. But me also, I use a
WD passport 1TByte USB 3.0 external Harddrive.


But why is this not supported any more:?:

---

