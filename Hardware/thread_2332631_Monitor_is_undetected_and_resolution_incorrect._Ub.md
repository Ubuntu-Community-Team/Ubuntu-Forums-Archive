---
title: "Monitor is undetected and resolution incorrect. Ubuntu 14.04"
date: 2016-08-02
forum: Hardware
---

### Post by joesalmon1985 on 2016-08-02
Monitor is undetected and resolution incorrect. I know nothing about the monitor beyond it being a Toshiba one.

Below is all the output I can dredge up. Any ideas?

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550]


lgp-inspiron-545          
    description: Desktop Computer
    product: Inspiron 545 ()
    vendor: Dell Inc.
    version: 00
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop uuid=44454C4C-2000-1020-8020-A0C04F202020
  *-core
       description: Motherboard
       product: 0N826N
       vendor: Dell Inc.
       physical id: 0
       version: A03
       serial: ..CN7360499I003R.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A12
          date: 11/17/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 8HTF12864AY-800J1
             vendor: Micron Technology
             physical id: 0
             serial: 941A8818
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 8HTF12864AY-800J1
             vendor: Micron Technology
             physical id: 1
             serial: 96DA8818
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 8HTF12864AY-800J1
             vendor: Micron Technology
             physical id: 2
             serial: 602A8818
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2015-02-19 11:31+0000X-Generator: Launchpad (build 17341) [empty]
             physical id: 3
             slot: DIMM4
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV710 [Radeon HD 4350/4550]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:44 memory:d0000000-dfffffff memory:fdce0000-fdceffff ioport:ae00(size=256) memory:fdc00000-fdc1ffff
           *-multimedia
                description: Audio device
                product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:46 memory:fdcfc000-fdcfffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff00(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fe00(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fd00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fdfff000-fdfff3ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:fdff8000-fdffbfff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:25:64:db:65:fb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:ce00(size=256) memory:fddff000-fddfffff memory:fdde0000-fddeffff memory:fdd00000-fdd1ffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fc00(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fa00(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fdffe000-fdffe3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
           *-multimedia
                description: Multimedia audio controller
                product: CA0106 Soundblaster
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_ca0106 latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:bf00(size=32)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=16) ioport:f400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffd000-fdffd0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f200(size=8) ioport:f100(size=4) ioport:f000(size=8) ioport:ef00(size=4) ioport:ee00(size=16) ioport:ed00(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD6400AAKS-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCASY8377917
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=18000000
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/lgp/1298B72C98B70CEB
                version: 3.1
                serial: ae47e0d7-ace0-e545-9dd7-14e8e1138d42
                size: 187GiB
                capacity: 187GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-09-27 14:31:07 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 408GiB
                capacity: 408GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8851MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 400GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW TS-H653G
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: DW10
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1c:df:a0:2c:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.13.0-88-generic firmware=1.7 ip=192.168.1.162 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by joesalmon1985 on 2016-08-02
I've tried messing about with "xrandr". This doesn't help. I end up with an even more messed up looking display, not matter how I change the resolution. These are the commands I've run

lgp@lgp-Inspiron-545:~$ xrandr --newmode "1600x900_60.00"  172.80  1600 2040 2248 2576  900 1081 1084 1118  -HSync +Vsync
lgp@lgp-Inspiron-545:~$ xrandr --addmode VGA-0 1600x900_60.00lgp@lgp-Inspiron-545:~$ xrandr --output VGA-0 --mode 1600x900_60.00lgp@lgp-Inspiron-545:~$ 
lgp@lgp-Inspiron-545:~$ xrandr --output VGA-0 --mode 1600x900_60.00

This doesn't help. Neither does any substitution of numbers instead of 1600x900 (but maybe I need to change more things).

---

### Post by Bucky Ball on 2016-08-02
You need to be careful if you are not sure what you are doing. Things can get messy. 

Please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Have you manually installed a driver for your GPU? The reason you don't see the correct resolutions available may be that you don't have the correct driver installed for your card.

---

### Post by joesalmon1985 on 2016-08-02
Haha, that explains why most of my life is messy. This is the output I get.

I haven't manually installed any drivers so far following the installation of Ubuntu 14.04. That sounds like a good guess, but I'm stuck as to how I'd find out what drivers I'm missing or how to install them. 

Thanks for the very speedy response
code:
lgp@lgp-Inspiron-545:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:db:65:fb
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:ce00(size=256) memory:fddff000-fddfffff memory:fdde0000-fddeffff memory:fdd00000-fdd1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1c:df:a0:2c:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.13.0-88-generic firmware=1.7 ip=192.168.1.162 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Bucky Ball on 2016-08-02
Eeek! My mistake. Make that:

```
sudo lshw -C video
```

My mistake. Also, check in 'Additional Drivers'. Give it a minute or two to think. Do you see a video driver offered there?

(Please use [code] tags for the terminal output. See the green link in my signature at bottom of my post. ;))

---

### Post by joesalmon1985 on 2016-08-03
ah, thanks for the formatting help.

Output is 

```

 *-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:d0000000-dfffffff memory:fdce0000-fdceffff ioport:ae00(size=256) memory:fdc00000-fdc1ffff


```

Now I guess this means my driver is a Radeon. Where I'm running Ubuntu 14.04 for the specific model I have (RV710) I should already have the correct driver right? 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Not sure where to go from here. The monictor is a Toshiba LCD colour TV 19BV501B if that helps

---

### Post by gordintoronto on 2016-08-04
The resolution of the TV is 1366 by 768. Is it connected using an HDMI cable? If there is some kind of adapter between the computer and the TV, that would explain why it is not detected properly.

---

### Post by joesalmon1985 on 2016-08-04
It's connected by a VGA cable (I think it that is the right term). The funky ones with screws that you can tighten so if you trip over you pull the whole desktop PC off the table and go flying at the same time.

---

### Post by mörgæs on 2016-08-04
Here is a thread in which the poster found a solution for a similar graphics card. Might give some inspiration:
[https://ubuntuforums.org/showthread.php?t=2322659](https://ubuntuforums.org/showthread.php?t=2322659)
In the thread I suggested staying with 14.04 but luckily the poster didn't pay attention.

---

### Post by Bucky Ball on 2016-08-04
> **joesalmon1985 said:**
> It's connected by a VGA cable (I think it that is the right term). The funky ones with screws that you can tighten so if you trip over you pull the whole desktop PC off the table and go flying at the same time.

Ha! :) At least with laptops there are no screw holes, but there's still a good chance of some breakage.

---

