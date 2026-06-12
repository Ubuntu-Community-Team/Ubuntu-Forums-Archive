---
title: "Crying fans in laptop futjitsu siemens amilo with ubuntu 12.04 lts"
date: 2014-12-22
forum: Hardware
---

### Post by Burkhard_Salz on 2014-12-22
Dear ALL, sorry for my english pronunciation while I am European and a User only. Few minutes ago I bought a used Futjitsu Siemens Laptop Amilo having installed Windows Vista 7. Installed ubuntu 12.04 lts with flash drive plus complete update. Runs well but => It is nerve-racking that the fans are starting all 10 seconds very loudly. Where ist the prob and what to do to avoid? Thanks for your help. Stay splendid! Burkhard

---

### Post by mörgæs on 2014-12-23
Hi, welcome to the fora.
We need to know more about the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Burkhard_Salz on 2014-12-24
Hello mörgaes, thanks for your reply. I did as recommended: sudo lshw -sanitize > lshw.txtsudo lshw -sanitize > lshw.txt => in terminal and for 3 seconds it was shown:  PCI (sys fs).  Three times same result. What to do know and thanks for your help. Burkhard and Merry Christmas

---

### Post by oldfred on 2014-12-24
the > lshw.txt
means it redirects the output to a file. You should have lshw.txt in /home. Open it and copy & paste to reply. If you use advanced reply then you can easily add the code tags by hightligting text like copy and click the # icon.

Also what is shown in display in the report. Often video driver controls fans.

---

### Post by Burkhard_Salz on 2014-12-28
Hallo oldfred, thanks and Merry Christmas. Done and file was stored in home and inside is:computer
    ```
description: Notebook
    product: AMILO Li 1818 ()
    vendor: FUJITSU SIEMENS
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: AMILO Li 1818
       vendor: FUJITSU SIEMENS
       physical id: 0
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS
          physical id: 0
          version: 1.13C
          date: 03/15/2007
          size: 1MiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.2
          serial: [REMOVED]
          slot: U2E1
          size: 1733MHz
          capacity: 2048MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1536MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.2
          serial: [REMOVED]
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0040000-b007ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:b0100000-b017ffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f0000000-f0003fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:f000(size=4096) memory:fac00000-febfffff ioport:60000000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:60200000-603fffff ioport:60400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f7000000-f70fffff ioport:60600000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f0004000-f00043ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:f0200000-f02fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:16 ioport:2000(size=256) memory:b0200000-b02000ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:18d0(size=8) ioport:18c4(size=4) ioport:18c8(size=8) ioport:18c0(size=4) ioport:18b0(size=16) memory:f0004400-f00047ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-T10N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PW03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVS-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 04.0
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0009c695
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 147GiB
                capacity: 147GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-22 16:19:26 filesystem=ext4 lastmountpoint=/ modified=2014-12-22 17:30:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-28 15:49:47 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1525MiB
                capacity: 1525MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1525MiB
                   capabilities: nofs
     *-scsi:2
          physical id: 5
          bus info: usb@1:1
          logical name: scsi37
          logical name: scsi38
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@37:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/sr1
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 31KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: [REMOVED]
                   size: 3030KiB
                   capacity: 3030KiB
                   capabilities: hfsplus initialized
                   configuration: checked=2011-09-14 10:45:58 created=2011-09-14 10:45:58 filesystem=hfsplus lastmountedby=cerd modified=2011-09-14 10:45:58 state=clean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@38:0.0.0
             logical name: /dev/sdb
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes
```
**Wow and now?**

---

### Post by oldfred on 2014-12-28
Looks like a standard core2 with Intel Video.

My desktop used to start with fans at max for just a few seconds until Video driver (I think) kicked-in. 

Since a laptop not sure how much applies. This is more for a system that totally crashes because of errors.
 Overheating, too much overclock, bad power supply, memory errors
[http://en.wikipedia.org/wiki/Machine-check_exception](http://en.wikipedia.org/wiki/Machine-check_exception)

---

### Post by mörgæs on 2014-12-29
Is there any change in a live boot of 14.10?

---

### Post by Burkhard_Salz on 2014-12-29
Hello mörgaes, what do you mean? Upgrading to 14.10 will solve the prob?!? (Only to let you know: I am running the amilo in ubuntu 12.04 without  the rechargeable battery (the same with my asus eee pc netbook without any probs and no crying fans ).
(Sorry oldfred, your recommendations a bid to far for me as a user only).

---

### Post by mörgæs on 2014-12-29
No upgrade but a fresh install of 14.10 if the live boot shows a difference. 
How 12.04 behaves on other hardware is not relevant.

---

### Post by Burkhard_Salz on 2015-01-18
Hello mörgaes, sorry unforeseen had to stay in hospital for days. Meanwhile I upgraded to Ubuntu 14.10 and it's the same. Starting a new web page or program or time by time the fan is starting himself very loudly for a few seconds - also at looking  dvd (Grrrh!).

---

### Post by mörgæs on 2015-01-18
Then we should take a look at physical problems. Do you know how to clean the fan and heat-sink for dust which could be clogging the air flow?

---

### Post by Burkhard_Salz on 2015-01-22
Hello mörgaes and All, thanks for your help. Meanwhile I got an answer from an amilo specialist. This behaviour can not be changed in amilo li 1818. AUA! But it is so.

---

### Post by Mike_Walsh on 2015-01-22
Oldfred's probably right about the video driver controlling the fans.

My old Compaq desktop (AMD Athlon 64, 3 GB DDR1 RAM, ATI Radeon Xpress 200 integrated graphics) does precisely the same on start up. It's usually while post is being carried out, and while the machine's splash screen is showing, with the options for boot, utilities, recovery mode, etc; it always shuts down to normal just as GRUB comes up.

As far as I can tell, this is perfectly normal behaviour for the HP/Compaq Presario desktops of the time, so I've long since given up worrying about it!


Regards,

Mike. ;)

---

