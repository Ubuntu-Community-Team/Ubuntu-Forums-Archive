---
title: "Dell PC running hot!"
date: 2008-05-21
forum: Hardware
---

### Post by wcunkefe on 2008-05-21
Hello All,
   I am in the process of completely switching from windows xp to ubuntu and am loving it!!  Have only one problem at the moment and it is not a show stopper.

Problem:
     The fans in my desktop pc are running faster than normal when the computer is idle.  I do not have this problem in windows and bias temps read perfectly normal.  I suppose the pc is running hotter in Ubuntu than it did with winxp.

Below is the output of lshw for my Dell E510 box... any help or suggestions to help me solve this problem would be excellent!!

Thanks in advance,
     Wayne


LSHW:
```
wcunkefe@Wayner-Ubuntu:~$ sudo lshw
wayner-ubuntu             
    description: Mini Tower Computer
    product: Dell DM051
    vendor: Dell Inc.
    serial: FZRTX91
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=2 power-on_password=enabled uuid=44454C4C-5A00-1052-8054-C6C04F583931
  *-core
       description: Motherboard
       product: 0HJ054
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN6986162L0003.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (03/31/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          slot: Microprocessor
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
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
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F7F7F7F7F9BFFFF
             physical id: 0
             serial: 7F0FF5B8
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: M3 78T3354CZ3-CD5
             vendor: CE00000000000000
             physical id: 1
             serial: F329339E
             slot: DIMM_3
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F7F7F7F7F9BFFFF
             physical id: 2
             serial: 8A6D5830
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: M3 78T3354CZ3-CD5
             vendor: CE00000000000000
             physical id: 3
             serial: F32933AA
             slot: DIMM_4
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 18EHz
          capabilities: ht
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
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
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7900 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Wireless interface
                product: 88w8335 [Libertas] 802.11b/g Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: 2
                bus info: pci@0000:03:02.0
                logical name: wlan0
                version: 03
                serial: 00:18:4d:6d:f7:32
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.52+NETGEAR,02/22/2005,3.1.1.7 ip=192.168.1.100 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12 module=ohci1394
           *-network:1
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 01
                serial: 00:13:72:bf:b2:30
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
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
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD writer
                product: IDE1008
                vendor: DVDRW
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0052
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: DVD writer
                product: DVD+-RW GWA4164B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: D108
                serial: [HL-DT-STDVD+-RW GWA4164BD10805/07/14
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD080HJ/
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: ZH10
                serial: S0DEJ1IL383703
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e686f016
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/sda1
                   version: 3.1
                   serial: 9050dc09-b63f-544d-81c9-ae158773b26a
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-01-23 08:09:38 filesystem=ntfs mount.fstype=fuseblk mount.options=ro,nosuid,nodev,noexec,noatime,user_id=0,group_id=0,default_permissions,allow_other state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: c2d787a3-0ab1-46e4-aceb-ecd9d2a0f0a4
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-09 11:03:22 filesystem=ext3 modified=2008-05-19 01:07:05 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-19 01:07:05 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: b2c212ae-4ad7-4d54-a9fb-2d93a85a922f
                   size: 1906MiB
                   capacity: 1906MiB
                   capabilities: primary extended partitioned partitioned:extended swap initialized
                   configuration: filesystem=swap pagesize=4096
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1906MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD2500KS-00M
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sdb
                version: 02.0
                serial: WD-WCANKA549868
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=56eabb36
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/sdb1
                   version: 3.1
                   serial: 5a502b24-a944-314c-85dd-9102086225a9
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-02-22 15:51:00 filesystem=ntfs label=250 Gig mount.fstype=fuseblk mount.options=ro,nosuid,nodev,noexec,noatime,user_id=0,group_id=0,default_permissions,allow_other state=mounted
        *-serial
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0 module=i2c_i801
```

---

### Post by adult swim on 2008-05-21
you could use gkrellm and the dell i8k fan plugin to set the temperatures at which your fans come on and shut off.  to do that try this
go system/administation/synaptic package manager
search for i8k
the first thing on the list should be gkrellm-i8k
click on the box and check mark for installation, once you do this it should automatically select all of the dependencies you will need for gkrellm and i8k
click apply
open a terminal and run
```
sudo modprobe i8k force=1
```

then run
```
sudo gedit /etc/modules
```

when the text editor pops up at the end of the file go to a new line and type in
```
i8k force=1
```
save the file and close it

to get gkrellm running hit alt-F2 and type in grkellm
if you want this to run on startup go to system/preferences/sessions
when you get there click add, at the name type in fans or whatever you want, at command type in gkrellm
to configure gkrellm to run your fans, you will need to right click it towards where it displays your computer name and select configuraion. go to plugins and make sure that i8k is enabled. once you do that you can select i8k from the menu on the left that drops down beneath plugins. then you can set your fans to turn on/off at specifc temperatures

---

### Post by wcunkefe on 2008-05-21
Thanks for the help!  I have done everything that was suggested and the fans still run constantly.  the CPU sensor reads 59C for the CPU in gkrellm, but the fans still run constantly.  I have set the thresholds to the following:

plugins/Dell I8K Plugin:
     AC Power Temperature Triggers:
          Left Fan: 40 Low  70 High
          Right Fan: 40 Low 70 High
          Hysteresis: 5
     Battery Power Temperature Triggers
          Left Fan: 40 Low  70 High
          Right Fan: 40 Low 70 High
          Hysteresis: 5

Any more suggestions would be greatly appreciated

Thanks for the help,
     Wayne

---

### Post by wcunkefe on 2008-07-08
Any more suggestions?  I have not solved the problem, so I am forced to use Windows at the moment... ugh!

---

