---
title: "Graphics driver &amp; Xorg"
date: 2012-11-04
forum: Hardware
---

### Post by komarx6 on 2012-11-04
I have many problems with my IBM X30. I can't run some DE, like Openbox. I use Lubuntu with LXDE, but it's too slow. I think that problem is about Xorg or graphics driver. It's old machine but I'm sure it should be faster when using Lubuntu. And CPU usage is 100% all the time. I think it's too much even for this machine.
I tried installing this:
[http://www.ubuntuupdates.org/package/xorg-edgers/oneiric/main/base/libgl1-mesa-dri-legacy](http://www.ubuntuupdates.org/package/xorg-edgers/oneiric/main/base/libgl1-mesa-dri-legacy)

but it didn't work.
I heard that possibly some software rendering is used instead of hardware, so proper driver should make it OK. Or that I should have older version of X.
Are there any experts in this area who can help?

---

### Post by komarx6 on 2012-11-04
This is output from lswh:

```
marko@aca-ibmx30:~$ sudo lshw
[sudo] password for marko: 
aca-ibmx30                
    description: Notebook
    product: 26721BU
    vendor: IBM
    version: Not Available
    serial: 78KFM31
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=9363D801-463B-11CB-99F0-CBC2444CCBBB
  *-core
       description: Motherboard
       product: 26721BU
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1NLD2BM10N
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1KET42WW (1.03 )
          date: 12/02/2002
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) III CPU - M  1066MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.11.4
          slot: None
          size: 1064MHz
          capacity: 1066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 384MiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830M/MG/MP Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82830M/MG Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e0000000-e7ffffff memory:d0000000-d007ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830M/MG Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=11
             resources: memory:e8000000-efffffff memory:d0080000-d00fffff
        *-usb:0
             description: USB controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1800(size=32)
        *-usb:1
             description: USB controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:2
             description: USB controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=20480) memory:d0200000-dfffffff memory:f0000000-f80fffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a8
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00502010-b0050200f irq:11 memory:50000000-50000fff ioport:3000(size=256) ioport:3400(size=256) memory:f0000000-f3ffffff memory:d4000000-d7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a8
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00606010-b0060600f irq:11 memory:50100000-50100fff ioport:3800(size=256) ioport:3c00(size=256) memory:f4000000-f7ffffff memory:d8000000-dbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:11 memory:d0201000-d02017ff
           *-network:0 UNCLAIMED
                description: Network controller
                product: ISL3874 [Prism 2.5]/ISL3872 [Prism 3]
                vendor: Intersil Corporation
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:f8000000-f8000fff
           *-network:1
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 42
                serial: 00:09:6b:60:ef:e5
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 memory:d0200000-d0200fff ioport:7000(size=64)
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:18000000-180003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-network
          description: Wireless interface
          product: AR5212/AR5213 Wireless Network Adapter
          vendor: Atheros Communications Inc.
          physical id: 1
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 01
          serial: 00:0c:41:fc:82:36
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ath5k driverversion=3.5.0-17-generic firmware=N/A ip=192.168.1.4 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
          resources: irq:11 memory:d4000000-d400ffff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IC25N020ATCS04-0
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CA2O
             serial: CSH204DMGHREKF
             size: 18GiB (20GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0005b01f
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f9467022-20ee-479b-abb8-6cd9947542ca
                size: 18GiB
                capacity: 18GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-19 02:04:19 filesystem=ext4 lastmountpoint=/ modified=2012-11-03 17:59:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-11-03 17:59:50 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 559MiB
                capacity: 559MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 559MiB
                   capabilities: nofs

```

---

### Post by Bashing-om on 2012-11-04
hi ! komarx6;

Your submitted info shows the display driver loaded as the i915 driver.
Try disabling KMS with the kernel boot option "i915modeset=0"
instructions to do so:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

lots of background info:
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915)

can be a very long read if you get interested !
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2012-11-04
Please post your /var/log/Xorg.0.log
Lubuntu 12.04 should run smoothly on such a machine. When you notice CPU is 100%, you should look at htop to see what's using the CPU.
```
sudo apt-get install htop
htop
```

---

### Post by steeldriver on 2012-11-04
I've been running Xubuntu 12.04 on an 1.2GHz X30 for a while (just blown it away to try Enlightenment on a bare Ubuntu) - my guess is your main problem is lack of RAM (mine has 2x512MB sticks) - 384MB is not much, especially once you take out a chunk for shared video

Maybe the excessive CPU usage is swap activity?

AFAIK the i915 doesn't actually support user-mode setting - when I tried i915.modeset in the past all that happens is it unloads i915 and defaults to an unaccelerated VESA driver

---

### Post by komarx6 on 2012-11-06
> **Temüjin said:**
> Please post your /var/log/Xorg.0.log
Lubuntu 12.04 should run smoothly on such a machine. When you notice CPU is 100%, you should look at htop to see what's using the CPU.
```
sudo apt-get install htop
htop
```

I know, I know:
[IMG]http://www.dodaj.rs/f/3L/12o/1IVPYQEC/htop.png[/IMG]

---

### Post by komarx6 on 2012-11-06
> **Bashing-om said:**
> hi ! komarx6;

Your submitted info shows the display driver loaded as the i915 driver.
Try disabling KMS with the kernel boot option "i915modeset=0"
instructions to do so:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

lots of background info:
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915)

can be a very long read if you get interested !
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

this is how my /etc/default/grub look like now:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet i915modeset=0"
GRUB_CMDLINE_LINUX=""
...

```
but now changes (I did sudo update-grub) :
```
marko@aca-ibmx30:~$ sudo lswh -C display
[sudo] password for marko: 
sudo: lswh: command not found
marko@aca-ibmx30:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: 82830M/MG Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff memory:d0000000-d007ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82830M/MG Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=11
       resources: memory:e8000000-efffffff memory:d0080000-d00fffff

```

---

### Post by Bashing-om on 2012-11-06
komarx6;

As I presently understand -> UMS (user mode setting (i915nomodeset=0)) is no longer recognized in the kernel using KMS (kernel mode setting) using newer drivers. I do not know how this applies if a newer driver is incorporated with older hardware ???

What results if you boot without the "i915nomoeset=0" option in the grub file ?

As ,if at all possible, booting with KMS enabled is desirable; Boot up and see if KMS is in effect.
[INDENT]tyn'n to help <== BDQ
 
[/INDENT]

---

