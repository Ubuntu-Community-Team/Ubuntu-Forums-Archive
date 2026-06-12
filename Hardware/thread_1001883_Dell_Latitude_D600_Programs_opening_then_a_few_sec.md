---
title: "Dell Latitude D600: Programs opening then a few seconds later, crashing."
date: 2008-12-04
forum: Hardware
---

### Post by jimmio on 2008-12-04
Hello all,

Ubuntu 8.10 is causing lots of unfun issues. I'll open Pidgin, ans 20 seconds later, it crashes. I'll open RhythmBox and it will crash...

The programs go into something called futex_wait... any ideas?

Below is my lshw output for those who are wondering the specs of the laptop:


```
jimmio-laptop
    description: Portable Computer
    product: Latitude D600
    vendor: Dell Computer Corporation
    serial: ________
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4700-1032-8048-B1C04F313431
  *-core
       description: Motherboard
       vendor: Dell Computer Corporation
       physical id: 0
       serial: ._______.              .
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A15 (01/26/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1400MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.9.5
          slot: Microprocessor
          size: 1400MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5705M Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:12:3f:13:51:4d
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.16 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
           *-pcmcia:0
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
              *-pccard UNCLAIMED
                   description: SmartCardBus Reader
                   vendor: O2Micro
                   physical id: 0
                   version: V1.0
                   slot: Socket 1
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=b43-pci-bridge latency=32 module=ssb
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: HTS541060G9AT00
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB3O
                serial: MPB3LAX5JRSK2M
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eacceacc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 951e8e6a-8423-4f9d-b05e-216729038789
                   size: 54GiB
                   capacity: 54GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-04 01:17:32 filesystem=ext3 modified=2008-12-04 02:27:47 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-12-04 01:30:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1474MiB
                   capacity: 1474MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MiB
                      capabilities: nofs
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
  *-battery:0
       product: DELL 4M01071
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52170mWh
       configuration: voltage=11.1V
  *-battery:1
       product: DELL 0000M78
       vendor: Sony
       physical id: 2
       slot: Sys. Module Bay
       capacity: 46620mWh
       configuration: voltage=11.1V
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0b:cd:56:a9:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.104 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: fa:cc:a6:66:1a:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Really odd issue... hey, at least the wireless works with the bcmcutter...

---

### Post by andreasis on 2008-12-04
Hi,

I have a D600 running Hardy (I just thought Intrepid was overkill for Hardy), but I'm not familiar with your problem.  I found a linux user suffering from a futex_wait problem [http://bugs.mysql.com/bug.php?id=25232](http://bugs.mysql.com/bug.php?id=25232) , and, if you scroll down to the very bottom, what fixed it in the end were the latest updates.

Does this problem happen after a fresh install, or after you've been tweaking/updating/changing around the system?  Do you have the latest updates? Does the system log tell you anything useful? Is it any different when you start a program from the command line, or under sudo? Do you have mysql running, or any other programs that you've installed on top of the ones that come with intrepid?

---

### Post by jimmio on 2008-12-04
Latest updates, no new programs other than simple-ccsm and compizconfig-settings-manager... Mp3 pack, ffmpeg pack... that's about it. Doesn't even have flash on it yet. Only thing I can think of is that it was installed from Flash Drive made with the "Create a USB Startup Disk" Option under System>Administration.

I had plenty of issues getting that to work, and it finally did... but it booted fine, no issues anywhere... so I don't get how that could have caused it. 

The CD Drive of the laptop went, so Flash Drive was the only way to go... and I tried fixing the drive, there's a metal cover on it, I took the screws out, and put my finger under it and slid and pulled to try to pop the tabs... sliced my finger open pretty good... and the drive still doesn't work >_<.

System log is located where? Haven't tried starting from command line *tries that now*. MySQL? Nah, I used to use my laptop as a server using Xubuntu 8.04, but the drive is wiped.

Not sure if the issue is fixed or not, opened Pidgin and RhythmBox from terminal, works perfect.

---

### Post by andreasis on 2008-12-04
Upper Panel >  System > Admninistration > System Log

If it's a hardware issue it could show up in the system log.

So the issue seems to be fixed now? Or do programs just run only when you start them from the terminal, or only as sudo? Does the terminal give you any messages after opening any files?

[EDIT] while you're in the System Log window, you can check out the user.log from the drop down list on the left hand side, too.

---

### Post by jimmio on 2008-12-04
Holy crud! Millions of "b43legacy-phy0 ERROR: PHY transmission error" in syslog... and yet the wireless works perfect... kern.log is filled with them too, and messages states ratelimit =P

user.log has many many errors, some about pulseaudio, some about the X Session Manager not running... sound works fine... everything works, even Compiz...

---

### Post by lykwydchykyn on 2008-12-04
Check the basics:

 - disk space on / and /var (if it's a seperate partition).  Running out of space on these partitions can cause really weird errors
 - test the memory by booting to memtest.  You can install it via synaptic to add it as a boot option.
 - test the drive with badblocks or better yet (if you can boot to your flash device again) fsck

---

### Post by jimmio on 2008-12-04
Disk space is fine.

Memory is fine.

The harddrive is probably going. It occasionally states no boot device found. Oh well, I'll replace the drive when it fails.

It's working fine at the moment... Rhythmbox has been playing music for over an hour without crashing. Seems there are wireless issues though, as the music cuts out and comes back randomly. (Listening to [http://67.18.213.166:8000](http://67.18.213.166:8000) - XRM Radio Alternative)

Pidgin isn't running, as I'm using it on my desktop PC.

really weird issue either way.

---

### Post by jimmio on 2008-12-04
It seems to be switching very often from 600 Mhz to 1.4 Ghz... is this bad for the CPU in any way?

Laptop still working okay by the way, I guess an ATI Mobility Radeon 9000 is sufficient for Compiz? Even the desktop cube is working perfectly.

---

### Post by jimmio on 2008-12-04
Nevermind, issue is still here =( Any other ideas?

---

### Post by sunta on 2008-12-21
Hello,

I got the same problem after switching from hardy -> intrepid.

The connection is kinda "slow" but works. though those messages fill up my logs. Will now try to use the windows-driver along ndiswrapper.

will leave a note when im done;)

---

