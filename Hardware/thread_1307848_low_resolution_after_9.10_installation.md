---
title: "low resolution after 9.10 installation"
date: 2009-10-31
forum: Hardware
---

### Post by agivati on 2009-10-31
I have Intel **945G** gfx, and an Samsung SyncMaster 931bw widescreen monitor (**1440x900**). 
After a fresh install of Karmic (full format) - display went down to 800x600, and higher resolutions are not available on Display Preferences dialog. 
I noticed that [COLOR="Red"]no xorg.conf file exists[/COLOR] in /etc/X11.
I had Jaunty until yesterday but reformatted, so i don't have the original xorg.conf file. also - the prev. one was not perfect, i was never able to get to 1440x900.
Seems like i am missing a great OS upgrade. Please help me get it back (my wife is impatient, that's her PC...)
:(

Dump of lshw:
lulu-desktop              
    description: Desktop Computer
    product: 945GCM-S2L
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-001D7D4CBE74
  *-core
       description: Motherboard
       product: 945GCM-S2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6b (01/25/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 2200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
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
          physical id: 17
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
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
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e2000000-e207ffff ioport:c000(size=8) memory:d0000000-dfffffff(prefetchable) memory:e2080000-e20bffff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:e20c0000-e20c3fff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:9000(size=4096)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bc00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e20c4000-e20c43ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:a000(size=4096) memory:e0000000-e1ffffff memory:40000000-400fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NC100 Network Everywhere Fast Ethernet 10/100
                vendor: ADMtek
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 11
                serial: 00:10:a7:29:90:5b
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.108 latency=64 maxlatency=255 mingnt=255 multicast=yes
                resources: irq:20 ioport:a000(size=256) memory:e1000000-e10003ff memory:40000000-4001ffff(prefetchable)
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
        *-ide
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMAT10943835
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9bf99bf9
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2bed5f10-def8-4b1e-abd2-525c18e51778
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-31 10:58:40 filesystem=ext4 lastmountpoint=/target?&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;^&#65533;&#65533;iW&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;u modified=2009-10-31 12:00:23 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-10-31 12:01:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2910MiB
                   capacity: 2910MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2910MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DRW-2014L1
                vendor: ASUS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)

---

### Post by agivati on 2009-11-05
Issue solved!
1. fyi - in Karmic the xorg.conf file is not always required, and it will not be created in some cases. If the file is manually added though, it will be used.
2. I somwhere found an xorg.conf which more-or-less fits my monitor/gfx. Installed it, reboot and vualla!! I have 1440x900 on my Karmic with Intel 945GM gfx!

Content of my xorg.conf - below:
--------------------------------------------------------------
Section  "Device"
    Identifier "Intel 945G"
    Driver     "intel"
    BusID      "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier "SyncMaster"
    Option "DPMS"
    Horizsync 30-81
    Vertrefresh 60-75
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Intel 945G"
    Monitor "SyncMaster"
    Defaultdepth 24
    SubSection "Display"
        Modes "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
--------------------------------------------------------------

---

### Post by fatkhulloh on 2009-11-05
I have Sis 672 and widescreen monitor (1280x800)..
After install ubuntu 9.10, the resolution only 800x600..
please help me..
Give me the driver..
:-|

---

### Post by agivati on 2009-11-05
> **fatkhulloh said:**
> I have Sis 672 and widescreen monitor (1280x800)..
After install ubuntu 9.10, the resolution only 800x600..
please help me..
Give me the driver..
:-|
What is the graphics card - Intel? nVidia? If Intel (integrated) then driver is part of Karmic (9.10) and it's probably an issue with xorg.conf file (or the lack of it...). If you have nVidia - you will need to install nVidia drivers.

---

### Post by mario.almeida on 2009-11-06
Hi agivati,

I have SyncMaster 551v 14" monitor how do find the current Horizsync and Vertrefresh 

With ubuntu 9.04 I could use 1024x768 but now not more then 800x600

Graphic card Intel 945G

//Remy

---

### Post by agivati on 2009-11-06
To know monitor timing download service manual from [here]("http://online.manualspace.com/computer-monitors-free-ebooks/samsung-monitor-service-manual/2811/samsung-syncmaster-551v-crt-monitor-service-manual-116.html")

---

### Post by lallalla on 2009-11-06
have you tried this?
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

worked for me and I have no more problems using 1680x1050 on external monitor

---

### Post by mario.almeida on 2009-11-06
> **lallalla said:**
> have you tried this?
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

worked for me and I have no more problems using 1680x1050 on external monitor

Hi lallalla,

Before posting here I followed the steps mentioned in the above URL but for some reason even after making entry in the xorg.conf file a reboot would not maintain 1024x768

After giving a closer look to the configuration in the above URL and compared it with my xorg.conf. I made 2 entries

Under Section "Monitor"
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
and
Option "PreferredMode" "1024x768_60.00"

log out from gui

X failed to start

from CLI executed startx

error reported for Option "PreferredMode" "1024x768_60.00"
replace Option "PreferredMode" "1024x768_60.00" with Option "DPMS"

and GUI came back

now even after reboot I get 1024x768 resolution

Thanks guys for all the help

//Remy

---

### Post by Uadebisi on 2009-12-13
Remy,

I am new to Linux & it seems as though I have the same problem that you had, for the most part. My screen rez reverts back to a lower rez on reboot...every time!

I too have Intel Graphics Controller (82945G/GZ) but I do not fully understand how to do what you did. Can you explain it to me in more detail? Thnaks.

---

### Post by Uadebisi on 2009-12-14
Nevermind :-)

Here's what I did to fix my problem... keeping in mind that I use Grub2 so all I had to do was download "Startup Manager" from the "Software Center" & adjust the settings in the GUI. Also, I have no /etc/X11/xorg.conf file:

> originally posted by** trx64: **I've solved the problem by disabling KMS (Kernel Mode Setting) in Intel driver, leaving the detection of my screen resolution just with X. There is no need to change xorg.conf, just leave it at default values.
 
 Edit the file /boot/grub/menu.lst (if you have GRUB 2, use [Startup Manager]("apt:startupmanager")). In the end of the "kernel" line of the OS entry, add "nomodesetting":
 
    [quote]  Code:
     title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,4)                              
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=92583a31-1693-438c-ae3f-61ab9b8ca13a ro quiet splash locale=pt_BR **nomodesetting**                                       
initrd          /boot/initrd.img-2.6.31-14-generic                                   
quiet 
[/quote]

See [http://ubuntuforums.org/showthread.php?t=1308745](http://ubuntuforums.org/showthread.php?t=1308745)

---

### Post by fatkhulloh on 2009-12-22
My Graphics Card is SIS (Silicon Integrated Systems) 672..
Sometimes The driver for SIS 672 and SIS 671 is same..
Please help me to solve this problem..

Sorry my english is not good..

---

### Post by fatkhulloh on 2009-12-22
> **agivati said:**
> What is the graphics card - Intel? nVidia? If Intel (integrated) then driver is part of Karmic (9.10) and it's probably an issue with xorg.conf file (or the lack of it...). If you have nVidia - you will need to install nVidia drivers.

My graphics Card is SIS 672 (Silicon Integrated Systems)..
Sometimes the driver SIS 672 and SIS 671 is same..
please help me to solve this problem..
Thanx..
:neutral:

Sorry, my english is not good..
:roll:

---

### Post by aeing on 2010-01-03
to agivate...

your the MAN men.....!!!!

i solved same issue with my synmaster 743nx...i am tired of thinking and searching how to adjust the resolution.....

after applying what you did....I DID it men....thanks a LOOOOOOTTT...

hope person like never tired in sahring IDEAS and HELP....

Godspeed.....

---

### Post by lipos on 2010-01-03
Maybe try to revert to 8.10 drivers.
It worked for me: 

[http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html]("http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html")

---

### Post by StuartinFiji on 2010-01-24
Changing my xorg.conf worked perfectly for me! I had to create one as suggested, but thanks for the help! :D


> **agivati said:**
> Issue solved!
1. fyi - in Karmic the xorg.conf file is not always required, and it will not be created in some cases. If the file is manually added though, it will be used.
2. I somwhere found an xorg.conf which more-or-less fits my monitor/gfx. Installed it, reboot and vualla!! I have 1440x900 on my Karmic with Intel 945GM gfx!

Content of my xorg.conf - below:
--------------------------------------------------------------
Section  "Device"
    Identifier "Intel 945G"
    Driver     "intel"
    BusID      "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier "SyncMaster"
    Option "DPMS"
    Horizsync 30-81
    Vertrefresh 60-75
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Intel 945G"
    Monitor "SyncMaster"
    Defaultdepth 24
    SubSection "Display"
        Modes "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
--------------------------------------------------------------

---

