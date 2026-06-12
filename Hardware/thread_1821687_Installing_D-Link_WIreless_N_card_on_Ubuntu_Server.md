---
title: "Installing D-Link WIreless N card on Ubuntu Server"
date: 2011-08-09
forum: Hardware
---

### Post by Droopy_Snowmen on 2011-08-09
I have been trying to install a D-Link Wireless N card on my Ubuntu Server (10.04) and am having some trouble. The card is a brand-new DWA-552. I have tried both madwifi and ndiswrapper with no luck. The card doesn't appear as an interface and shows up as (UNCLAIMED) in lshw.

Help is appreciated.

---

### Post by Droopy_Snowmen on 2011-08-18
It has been more than a week since I posted this query, and still I have no replies. This has not been a lone occurrence for me, and I am wondering what I can do to improve my visibility or clarity or whatever it is that is impeding me from being recognized or responded to.

I DO understand that this is a forum, and not every question will be given attention, but I've watched on several occasions my threads' reply counts remain at zero while all the others posted at the same time received responses. So my conclusion is, therefore, that there must be something I am doing that makes my posts unattractive. If I could get some guidance in this matter, I would be most grateful.

Of course...
I am posting in an old thread...

---

### Post by fdrake on 2011-08-18
did you try to follow this how-to?
[http://forums.linuxmint.com/viewtopic.php?f=53&t=10209](http://forums.linuxmint.com/viewtopic.php?f=53&t=10209)

post here if you encounter problems.

---

### Post by Droopy_Snowmen on 2011-08-18
Thanks for the help.

I had not tried that guide yet, but had tried a few similar to it. I got to the point where it said to run ifconfig to view the new interface, but mine does not show up there.

It still shows up as "UNCLAIMED" in lshw

---

### Post by fdrake on 2011-08-19
> **Droopy_Snowmen said:**
> Thanks for the help.

I had not tried that guide yet, but had tried a few similar to it. I got to the point where it said to run ifconfig to view the new interface, but mine does not show up there.

It still shows up as "UNCLAIMED" in lshw

well a working device my be still show unclaimed if it works. I do have one unclaimed device too but it works.

post here

```
lshw -numeric | kess
ifconfig
iwconfig
```

---

### Post by Droopy_Snowmen on 2011-08-19
I've got my full lshw output here. I see you directed me to use kess (I assumed you meant less) but that seemed like an in-console display choice. I'm not sure I understand its purpose here. 
Anyway, here is the output

lshw: 
```

                  ubuntu-server
    description: Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal uuid=9010F1EC-9EF1-11DA-AF32-000C6E080286
  *-core
       description: Motherboard
       product: D945GTP
       vendor: Intel Corporation
       physical id: 0
       version: AAC97834-303
       serial: BQTP60709614
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Pentium(R) D CPU 2.80GHz
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: NT94510J.86A.2487.2005.0906.1451 (09/06/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x202020202020202020202020202020202020
             vendor: 0x7FBA000000000000
             physical id: 0
             serial: 0x00000000
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x202020202020202020202020202020202020
             vendor: 0x7FBA000000000000
             physical id: 2
             serial: 0x00000000
             slot: J6J1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:90000000-92ffffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:92000000-92ffffff memory:80000000-8fffffff(prefetchable) memory:90000000-91ffffff ioport:2000(size=128)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:93300000-93303fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:93400000-934fffff memory:93700000-938fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:93500000-935fffff memory:93900000-93afffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:93600000-936fffff memory:93b00000-93cfffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:93304000-933043ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:1000(size=4096) memory:93000000-932fffff
           *-network:0 UNCLAIMED
                description: Network controller
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:93000000-9300ffff
           *-network:1
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: wlan0
                version: 02
                serial: 00:22:75:18:7f:26
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,03/23/2006, 4.40.1 ip=192.168.0.101 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
                resources: irq:22 memory:93210000-93211fff
           *-network:2 DISABLED
                description: Ethernet interface
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 01
                serial: 00:16:76:31:52:fa
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:20 memory:93212000-93212fff ioport:1000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30b0(size=16)
           *-cdrom:0
                description: DVD writer
                product: DVD RW DRU-710A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BY03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:30c8(size=8) ioport:30e4(size=4) ioport:30c0(size=8) ioport:30e0(size=4) ioport:30a0(size=16)
           *-disk:0
                description: ATA Disk
                product: ST380817AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 9.01
                serial: 4MR46CVP
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b9c47
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 19f5326b-72ff-4a42-9f36-d52c16bd18c0
                   size: 219GiB
                   capabilities: primary bootable multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-07-04 20:55:00 filesystem=ext4 lastmountpoint=/0.'[FONT=&quot]&#8745;&#9488;&#9564;[/FONT](][FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]O7[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]M}[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT] P}[FONT=&quot]&#8745;&#9488;&#9564;[/FONT] modified=2011-08-07 01:41:43 mounted=2011-08-14 05:48:48 state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD800JD-23JN
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sdb
                version: 06.0
                serial: WD-WCAM98804146
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000de8c4
              *-volume
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 74GiB
                   capabilities: primary multi
           *-disk:2
                description: ATA Disk
                product: WDC WD800JD-22LS
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 06.0
                serial: WD-WMAM9AV37004
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000ac05
              *-volume:0
                   description: Linux swap / Solaris partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   capacity: 3814MiB
                   capabilities: primary nofs
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdc2
                   logical name: /boot
                   version: 1.0
                   serial: 77efab0d-8b60-4974-936e-533dc623c89e
                   size: 488MiB
                   capacity: 488MiB
                   capabilities: primary journaled extended_attributes huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-04 20:48:46 filesystem=ext4 lastmountpoint=/boot8=[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]i(=[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]+z[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]7[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]@[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]}[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT] [FONT=&quot]&#8745;&#9488;&#9564;[/FONT] modified=2011-08-18 21:50:37 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-08-18 21:50:37 state=mounted
              *-volume:2
                   description: Linux raid autodetect partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdc3
                   capacity: 70GiB
                   capabilities: primary multi
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:3000(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdd
             size: 2794GiB (3TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0004df06
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdd1
                capacity: 349GiB
                capabilities: primary multi
     *-scsi:1
          physical id: 2
          bus info: usb@1:2
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sde
             size: 2794GiB (3TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000363a4
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sde1
                capacity: 349GiB
                capabilities: primary multi
     *-scsi:2
          physical id: 4
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdf
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=4b4c366b
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdf1
                version: 1.0
                serial: 1f0856f1-201f-4513-9d78-51fcca8146e6
                size: 298GiB
                capacity: 298GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2011-05-24 18:42:46 filesystem=ext3 modified=2011-08-02 12:12:07 mounted=2011-08-02 12:11:49 state=clean   

```
ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10012 (10.0 KB)  TX bytes:10012 (10.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:18:7f:26  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe18:7f26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:831138 (831.1 KB)  TX bytes:788737 (788.7 KB)
          Interrupt:22 Memory:93210000-93212000 

```
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"router"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:5F:07:2C   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:363  Invalid misc:372454   Missed beacon:0

```
For the record, just to avoid confusion, I have a working wireless card in there now (wlan0). This new card has wireless n and will be used to replace the old one.

---

### Post by fdrake on 2011-08-19
> **Droopy_Snowmen said:**
> I've got my full lshw output here. I see you directed me to use kess (I assumed you meant less) but that seemed like an in-console display choice. I'm not sure I understand its purpose here. 
Anyway, here is the output

lshw: 
```

                  ubuntu-server
    description: Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal uuid=9010F1EC-9EF1-11DA-AF32-000C6E080286
  *-core
       description: Motherboard
       product: D945GTP
       vendor: Intel Corporation
       physical id: 0
       version: AAC97834-303
       serial: BQTP60709614
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Pentium(R) D CPU 2.80GHz
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: NT94510J.86A.2487.2005.0906.1451 (09/06/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x202020202020202020202020202020202020
             vendor: 0x7FBA000000000000
             physical id: 0
             serial: 0x00000000
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x202020202020202020202020202020202020
             vendor: 0x7FBA000000000000
             physical id: 2
             serial: 0x00000000
             slot: J6J1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:90000000-92ffffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:92000000-92ffffff memory:80000000-8fffffff(prefetchable) memory:90000000-91ffffff ioport:2000(size=128)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:93300000-93303fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:93400000-934fffff memory:93700000-938fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:93500000-935fffff memory:93900000-93afffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:93600000-936fffff memory:93b00000-93cfffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:93304000-933043ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:1000(size=4096) memory:93000000-932fffff
           *-network:0 UNCLAIMED
                description: Network controller
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:93000000-9300ffff
           *-network:1
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: wlan0
                version: 02
                serial: 00:22:75:18:7f:26
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,03/23/2006, 4.40.1 ip=192.168.0.101 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
                resources: irq:22 memory:93210000-93211fff
           *-network:2 DISABLED
                description: Ethernet interface
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 01
                serial: 00:16:76:31:52:fa
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:20 memory:93212000-93212fff ioport:1000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30b0(size=16)
           *-cdrom:0
                description: DVD writer
                product: DVD RW DRU-710A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BY03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:30c8(size=8) ioport:30e4(size=4) ioport:30c0(size=8) ioport:30e0(size=4) ioport:30a0(size=16)
           *-disk:0
                description: ATA Disk
                product: ST380817AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 9.01
                serial: 4MR46CVP
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b9c47
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 19f5326b-72ff-4a42-9f36-d52c16bd18c0
                   size: 219GiB
                   capabilities: primary bootable multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-07-04 20:55:00 filesystem=ext4 lastmountpoint=/0.'[FONT=&quot]&#8745;&#9488;&#9564;[/FONT](][FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]O7[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]M}[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT] P}[FONT=&quot]&#8745;&#9488;&#9564;[/FONT] modified=2011-08-07 01:41:43 mounted=2011-08-14 05:48:48 state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD800JD-23JN
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sdb
                version: 06.0
                serial: WD-WCAM98804146
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000de8c4
              *-volume
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 74GiB
                   capabilities: primary multi
           *-disk:2
                description: ATA Disk
                product: WDC WD800JD-22LS
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 06.0
                serial: WD-WMAM9AV37004
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000ac05
              *-volume:0
                   description: Linux swap / Solaris partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   capacity: 3814MiB
                   capabilities: primary nofs
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdc2
                   logical name: /boot
                   version: 1.0
                   serial: 77efab0d-8b60-4974-936e-533dc623c89e
                   size: 488MiB
                   capacity: 488MiB
                   capabilities: primary journaled extended_attributes huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-04 20:48:46 filesystem=ext4 lastmountpoint=/boot8=[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]i(=[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]|[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]+z[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]7[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT]@[FONT=&quot]&#8745;&#9488;&#9564;[/FONT]}[FONT=&quot]&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;&#8745;&#9488;&#9564;[/FONT] [FONT=&quot]&#8745;&#9488;&#9564;[/FONT] modified=2011-08-18 21:50:37 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-08-18 21:50:37 state=mounted
              *-volume:2
                   description: Linux raid autodetect partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdc3
                   capacity: 70GiB
                   capabilities: primary multi
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:3000(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdd
             size: 2794GiB (3TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0004df06
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdd1
                capacity: 349GiB
                capabilities: primary multi
     *-scsi:1
          physical id: 2
          bus info: usb@1:2
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sde
             size: 2794GiB (3TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000363a4
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sde1
                capacity: 349GiB
                capabilities: primary multi
     *-scsi:2
          physical id: 4
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdf
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=4b4c366b
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdf1
                version: 1.0
                serial: 1f0856f1-201f-4513-9d78-51fcca8146e6
                size: 298GiB
                capacity: 298GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2011-05-24 18:42:46 filesystem=ext3 modified=2011-08-02 12:12:07 mounted=2011-08-02 12:11:49 state=clean   

```
ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10012 (10.0 KB)  TX bytes:10012 (10.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:18:7f:26  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe18:7f26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:831138 (831.1 KB)  TX bytes:788737 (788.7 KB)
          Interrupt:22 Memory:93210000-93212000 

```
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"router"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:5F:07:2C   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:363  Invalid misc:372454   Missed beacon:0

```
For the record, just to avoid confusion, I have a working wireless card in there now (wlan0). This new card has wireless n and will be used to replace the old one.

are you able to test your drive with a live cd (32bit and 64 bit) and see if it works with both. I may be wrong, but the 64bit has hard time finding or using the right driver. 
that's all i can thing of. sorry.

---

### Post by Droopy_Snowmen on 2011-08-22
I appreciate the reply. I have been away from my server for several days now, so that's why it's taken me so long to reply. I have the 64 bit live cd but i'll have to download the 32 bit one tonight and try it.

 If it is the case that it is an issue with finding/loading the 64 bit driver, what can be done about it?

---

### Post by Droopy_Snowmen on 2011-08-24
Alright, so I am still faced with the task of checking out if the 32 bit version will load the driver, but as I do not have direct access to the machine, it may take a while. As I am only equipped with the server and my laptop, I need to find a monitor somewhere that I can move to my basement, etc. etc. 

Is there some way I could compile and boot a 32-bit kernel just to check this? Doing something of this nature would actually be easier for me than using the live cd. I'm guessing that the modules and daemons that are installed along side the system are probably also 64-bit, so this may not be possible, but if there were something of this nature I could do, that would be incredibly helpful.

---

