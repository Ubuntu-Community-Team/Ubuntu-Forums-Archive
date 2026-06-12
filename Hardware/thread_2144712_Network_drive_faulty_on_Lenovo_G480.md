---
title: "Network drive faulty on Lenovo G480"
date: 2013-05-13
forum: Hardware
---

### Post by lindaonline15 on 2013-05-13
hi,

I'm having problems with my network driver.
1. at first installation, I did not have either wireless or wired networks.
2. I updated my system using a network USB dongle, and got proprietary drivers, installed it
3. then I had wired, but no wireless, I did this:
```
apt-get installlinux-headers-generic build-essential
[COLOR=#333333][FONT=Consolas]wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]cd compat-wireless-3.5.1-1-snpc[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]./scripts/driver-select alx[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]make[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]make install[/FONT][/COLOR]
[COLOR=black][FONT=Consolas]modprobe alx[/FONT][/COLOR]
```
4. after that my wired worked for sometime but after some updates, again I cant use wired.
5. this is what ifconfig gives me:
```
eth1      Link encap:Ethernet  HWaddr c0:14:3d:cf:8a:83            inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c214:3dff:fecf:8a83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17070 errors:46 dropped:0 overruns:0 frame:318962
          TX packets:13006 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20981283 (20.9 MB)  TX bytes:1709014 (1.7 MB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5349 (5.3 KB)  TX bytes:5349 (5.3 KB)



```
6. and this is iwconfig:
```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"ss1"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: B8:A3:86:B3:9B:D4   
          Bit Rate=1 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
7. and this is lspci:
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
```

8. and lshw:
```
lenovo                        description: Notebook
    product: 20156 (System SKUNumber)
    vendor: LENOVO
    version: Lenovo G480
    serial: WB08752512WB02101102
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=notebook family=ChiefRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=A8CEF6C0-13E8-11E2-8844-9EF679CB254A
  *-core
       description: Motherboard
       product: Emerald Lake 2
       vendor: LENOVO
       physical id: 0
       version: FAB1
       serial: WB08752512
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 62CN41WW
          date: 09/10/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: CPU Socket - U3E1
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-cache:0
          description: L1 cache
          physical id: 5
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-cache:1
          description: L1 cache
          physical id: 6
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through instruction
     *-cache:2
          description: L2 cache
          physical id: 7
          slot: L2-Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through unified
     *-cache:3
          description: L3 cache
          physical id: 8
          slot: L3-Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 9905428-086.A00LF
             vendor: Kingston
             physical id: 0
             serial: C40FD949
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 9905428-086.A00LF
             vendor: Kingston
             physical id: 2
             serial: C30FC649
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:3000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f0600000-f060ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:f0615000-f061500f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0619000-f06193ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f0610000-f0613fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f0500000-f05fffff
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: c0:14:3d:cf:8a:83
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.127 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f0500000-f0503fff
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f0400000-f04fffff
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8162 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: latency=0
                resources: memory:f0400000-f043ffff ioport:2000(size=128)
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0618000-f06183ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi4
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:f0617000-f06177ff
           *-disk
                description: ATA Disk
                product: ST500LT012-9WS14
                vendor: Seagate
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 0001
                serial: W0V1RC6J
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002b45e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: aaa04f60-63aa-4a27-9a42-5199e6ec9fab
                   size: 420GiB
                   capacity: 420GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-12-19 22:30:20 filesystem=ext4 lastmountpoint=/ modified=2013-05-07 10:26:39 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-05-13 17:43:26 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: c44af690-18d5-5740-829b-c14e75bbec21
                   size: 29GiB
                   capacity: 30GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-03-30 14:01:36 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 14GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SN-208AB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: LA03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0614000-f06140ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@2:1.6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Card  Reader
             vendor: Multiple
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@3:4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
  *-battery
       product: Smart Battery
       vendor: Intel Corp.
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
  *-power UNCLAIMED
       description: TBD by ODM
       product: TBD by ODM
       vendor: TBD by ODM
       physical id: 2
       version: 1.0
       serial: TBD by ODM
       capacity: 32768mWh



```


does anyone have any idea how to solve this?
Thanks!

---

