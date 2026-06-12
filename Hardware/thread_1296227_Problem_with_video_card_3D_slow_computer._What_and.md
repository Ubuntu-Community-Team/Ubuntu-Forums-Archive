---
title: "Problem with video card 3D: slow computer. What and How to do?"
date: 2009-10-20
forum: Hardware
---

### Post by crixtiano on 2009-10-20
Hi, 

I have a computer with the following configuration:

> 

[COLOR="Red"]**Ubuntu Version**[/COLOR]

[INDENT]**$ cat /etc/issue**
Ubuntu 8.04.3 LTS \n \l[/INDENT]

[COLOR="Red"]**Video card:**[/COLOR]

[INDENT]**$ lspci | grep Display**
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

**$ lspci -n | grep 01:00.1**
01:00.1 0380: 1002:5940 (rev 01)[/INDENT]

[COLOR="Red"]**Disks and Memory**[/COLOR]

```

**$ df**
Sist. Arq.           1K-blocos      Usad Dispon.   Uso% Montado em
/dev/sda3              9709100   6119188   3096720  67% /
varrun                  517436       132    517304   1% /var/run
varlock                 517436         0    517436   0% /var/lock
procbususb              517436        76    517360   1% /proc/bus/usb
udev                    517436        76    517360   1% /dev
devshm                  517436        52    517384   1% /dev/shm
lrm                     517436     40508    476928   8% /lib/modules/2.6.24-24-386/volatile
/dev/sda6             24027596   2852980  19954084  13% /home
/dev/sda7              5724172   1437592   3995808  27% /opt
/dev/sda2              5844248   1840640   4003608  32% /media/hda2
/dev/sdb1             19922912   4651936  15270976  24% /media/hdb1
/dev/sdc1             76920416  33666456  39346552  47% /media/hdc1

**$ free -m**
             total       used       free     shared    buffers     cached
Mem:          1010        873        137          0         47        543
-/+ buffers/cache:        282        727
Swap:         1427          0       1427
```

[COLOR="Red"]**lshw output**[/COLOR]

```

**$ sudo lshw**
luizinho
description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4VP-MX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: USB1
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1011.007 (01/10/2005)
          size: 64KiB
          capacity: 320KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2800MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: P4M266 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 PRO] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-24-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-24-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.24-24-386 ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=4 speed=480.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-24-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: WebCam NX [PD1110]
                   vendor: Creative Technology, Ltd
                   physical id: 2
                   bus info: usb@3:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=gspca maxpower=80mA speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-24-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   vendor: Belkin
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=1.5MB/s
        *-usb:5
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.24-24-386 uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y22WA2HE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ec63ec63
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 5802-6d27
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/hda2
                   version: FAT32
                   serial: d734-d278
                   size: 5706MiB
                   capacity: 5718MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 0b4f5d1b-4488-48bc-96cc-a4a5de051292
                   size: 9632MiB
                   capacity: 9632MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: filesystem=ext3 label=/ modified=2009-10-20 08:56:08 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-10-20 08:56:08 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1427MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 23GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /opt
                      capacity: 5679MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: SAMSUNG SV2042H
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: PK10
                serial: 0263J1AR151261
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8f5a8f5a
              *-volume
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/hdb1
                   version: FAT32
                   serial: 682e-f982
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 state=mounted
           *-disk:2
                description: ATA Disk
                product: MAXTOR STM380215
                vendor: Maxtor
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 9QZ7Z08L
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a3be3539
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /media/hdc1
                   version: 1.0
                   serial: 0f8833fc-fae8-4111-8d1c-39fe9fa6d0cc
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-12 16:59:10 filesystem=ext3 modified=2009-10-20 11:54:25 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2009-10-20 11:54:25 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H10A
                vendor: HL-DT-ST
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom2
                logical name: /dev/dvd2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:11:2f:d8:af:7b
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.3.120 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
```




**Problem**

I have the feeling that my computer is slow. When I choice "Visual Efects - Extra" everything I do in computer is very slow.

Please, how can I tell if my 3D card is properly installed? And if not, how can I properly install my 3D card?

Thank you very much.

Cristiano

---

### Post by markbuntu on 2009-10-21
Have you seen this?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

