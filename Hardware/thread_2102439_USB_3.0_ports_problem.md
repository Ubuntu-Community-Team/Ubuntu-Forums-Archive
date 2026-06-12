---
title: "USB 3.0 ports problem"
date: 2013-01-07
forum: Hardware
---

### Post by Mijuca on 2013-01-07
Hi,

i have Toshiba Satellite L850-18t with windows 7 and ubuntu 12.04. On ubuntu 2 of 3 usb ports dont work, i guess because they are usb 3.0 supported.

When i am on win7 everything works fine, so ports are not damaged.

Please help it's really frustrating  when you have only 1 usb port.


```
lspci
```
```
aleksa@SATELLITE-L850-18T:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks HDMI Audio [Radeon HD 6000 Series]
08:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
aleksa@SATELLITE-L850-18T:~$ 
```


```
sudo lshw
```
```
aleksa@SATELLITE-L850-18T:~$ sudo lshw
[sudo] password for aleksa: 
satellite-l850-18t        
    description: Notebook
    product: SATELLITE L850-18T (PSKDNE-00R00RY4)
    vendor: TOSHIBA
    version: PSKDNE-00R00RY4
    serial: 7C663863R
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=Type1Family sku=PSKDNE-00R00RY4 uuid=80DF531E-3F4C-E281-3333-4C72B970EDEA
  *-core
       description: Motherboard
       product: Type2 - Board Product Name1
       vendor: Type2 - Board Vendor Name1
       physical id: 0
       version: Type2 - Board Version
       serial: Type2 - Board Serial Number
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 1.60
          date: 06/27/2012
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5773CHS-CK0
             vendor: Samsung
             physical id: 0
             serial: E2BDACBD
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5173BH0-CK0
             vendor: Samsung
             physical id: 1
             serial: B246E0CE
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Ivy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:c2000000-c2ffffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Thames XT/GL [Radeon HD 7600M Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:b0000000-bfffffff memory:c2000000-c201ffff ioport:3000(size=256) memory:c2040000-c205ffff
           *-multimedia
                description: Audio device
                product: Turks HDMI Audio [Radeon HD 6000 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:47 memory:c2020000-c2023fff
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
             resources: irq:42 memory:c3100000-c310ffff
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
             resources: irq:44 memory:c3114000-c311400f
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
             resources: irq:16 memory:c3119000-c31193ff
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
             resources: irq:46 memory:c3110000-c3113fff
        *-pci:1
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
             resources: irq:17
        *-pci:2
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
             resources: irq:16 memory:c3000000-c30fffff ioport:c3300000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 1c:c6:3c:a7:49:d6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-35-generic firmware=N/A ip=192.168.1.48 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:c3000000-c307ffff memory:c3300000-c330ffff
        *-pci:3
             description: PCI bridge
             product: Panther Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:c1000000-c1ffffff ioport:c0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 07
                serial: 4c:72:b9:70:ed:ea
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff
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
             resources: irq:23 memory:c3118000-c31183ff
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
             logical name: scsi0
             logical name: scsi2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:4048(size=8) ioport:4054(size=4) ioport:4040(size=8) ioport:4050(size=4) ioport:4020(size=32) memory:c3117000-c31177ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MQ01ABD0
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AX00
                serial: 62R9S9G3S
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004daec
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 387a-985c
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-12-25 13:29:26 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 4ab2cd62-a745-5549-b083-18fc9ac2b64f
                   size: 270GiB
                   capacity: 270GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-25 13:29:28 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 195GiB
                   capacity: 195GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 189GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 6102MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SN-208AB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: TO03
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
             resources: memory:c3115000-c31150ff ioport:4000(size=32)
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 07/07/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
aleksa@SATELLITE-L850-18T:~$ 
```

```
lsusb
```
```
aleksa@SATELLITE-L850-18T:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 005: ID 04f2:b307 Chicony Electronics Co., Ltd 
aleksa@SATELLITE-L850-18T:~$ 

```


Thank you :)

---

### Post by Mijuca on 2013-01-16
Please help and i cant find graphic card drivers too, my card is ati 7670m, please help...

---

### Post by greenwapiti on 2013-03-04
The AMD Catalyst&#8482; 13.1 Proprietary Linux x86 Display Driver is available at [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) and Ask Ubuntu has some install directions that may help at [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)

---

