---
title: "no 3d Support on Intel GMA 950 onboard-card"
date: 2008-11-04
forum: Hardware
---

### Post by alecz20 on 2008-11-04
I have been using an Nvidia card on this desktop ever since installing Ubuntu on it.

I decided to remove the Nvidia card in favor of the on-board Intel GMA 950 card (the nvidia card was noisy, the intel card is supposed to have an opensource driver)

Now, Ubuntu does not "detect" the video card properly. While I can see it in lshw output, I have no 3D capabilities. What I really need is OpenGL support for the waveform in Mixxx.

I tried modifying the xorg.conf file, by manually putting Driver "intel", but to no avail.

Here is my lshw output:
```

    description: Desktop Computer
    product: RK575AAR-ABA a1740n
    vendor: HP-Pavilion
    version: 1111
    serial: MX27010M1G
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=80F5F4DC-369C-1210-8DD7-F64ECF848E93
  *-core
       description: Motherboard
       product: LEONITE
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 5.00
       serial: MS1C6BS31501843
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.17 (04/20/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 1867MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: c
             slot: L3 Cache
             capabilities: synchronous internal varies
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
          physical id: 14
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 16HTF12864AY-53ED4
             vendor: 2CFFFFFFFFFFFFFF
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 16HTF12864AY-53ED4
             vendor: 2CFFFFFFFFFFFFFF
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
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
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
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
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
           *-network
                description: Wireless interface
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                logical name: wifi0
                version: 01
                serial: 00:11:95:fa:d8:e2
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.0.102 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-multimedia
                description: Multimedia controller
                product: DSP56361 Digital Signal Processor
                vendor: Motorola
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=Echoaudio Echo3G latency=192 module=snd_echo3g
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
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
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             logical name: scsi6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-H653L
                vendor: TSSTcorp
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0414
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
           *-disk
                description: ATA Disk
                product: ST3320820AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@6:0.0.0
                logical name: /dev/sda
                version: 3.AH
                serial: 9QF11FWD
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cc697c7b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@6:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0e8ff934-26cb-654f-9170-505962f84e06
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-05-17 15:24:55 filesystem=ntfs label=HP state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@6:0.0.0,2
                   logical name: /dev/sda2
                   size: 270GiB
                   capacity: 270GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/data
                      capacity: 248GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 20GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 941MiB
                      capabilities: nofs
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
     *-scsi
          physical id: 2
          bus info: usb@5:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: Compact Flash
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: SM/xD-Picture
             vendor: Generic-
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: SD/MMC
             vendor: Generic-
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: MS/MS-Pro
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde


```

And my glxinfo output:
```

glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x51 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


```

I even tried to boot in recovery mode, and reconfigure the X server, but it didn put the driver in the xorg.conf file.
I remember that in 7.04 (i think) there was an option to manually choose the driver using an applet for changing the resolution.

I know the intel card has an open-source driver, but for some reason Ubuntu does not use it. Setting Driver "intel" in xorg.conf does not help either.

Any help is appreaciated, otherwise I think I might have to do a complete re-install.

---

### Post by vreppeto on 2008-12-13
I have a fresh install of Hardy on an Intel 945gclf2 board with atom 330 cpu,gc945 chipset and gma950 integrated video.  Flash player cannot play full screen w/o dropping frames.  I suspect we are looking for the same solution.  I do not think a fresh install will help you.  I am still searching and will post what I find here.

     Well, I was wrong. For me the solution was Flash player ver 10. Several posts report that hw accel is enabled by default.  Flash player ver 9 does not tap hw accel.

     If I find more info on tweaking this driver I will post it here.

---

### Post by MonkeyPaw on 2008-12-14
Not to rain on the situation, but Intel's integrated graphics aren't the most spectacular, and Intel's own drivers aren't usually very good either. It's not uncommon for Intel's IGP to launch with features disabled in software, with those features never getting enabled with future updates. While I'm sure the open source community can help, the hardware is still limited. My GMA 950 graphics are okay on my machine, but there are occasional artifacts when switching windows, and youtube full screen is a bad experience. I just don't think the power is there to tap. 

Perhaps a less frustrating experience might be to replace the cooler on your video card? Depending on what GPU you have there are aftermarket coolers that would fit, and they should be pretty cheap. If not that, you might be able to put a different fan on it, or even make your own cooler. I've done all of the above, and it can really give your old stuff new life and purpose.

---

### Post by jrusso2 on 2008-12-14
This is why open source is not always the best model for drivers.  The Windows drivers work well.

---

### Post by Baggers on 2008-12-18
Its seems that there is no hardware acceleration with the gma 950 under Ubuntu. Even when compositing is working fine and glxinfo reports direct rendering to be on, it isn't. 
'Tis a real bugger as it means my eeepc 701 totally outperforms my 901 for gaming!
I've been hunting around but can't find any threads that explain it.

---

### Post by alecz20 on 2009-01-16
Well, it turns out a fresh install did "fix" the problem.

Maybe there is no "true" hardware acceleration, but at least now I can use some 3D features, and OpenGL waveforms in Mixxx.

Still not sure what the problem was... somehow installing the OS with the on-board disabled, makes it behave strange when the on-board is enabled again.

Eventually, I installed an ATI X800 XT card, and enabled the proprietary drivers without which running Mixxx with OpenGL waveforms would cause 50% CPU usage (on dual core machine; i.e. 100% cpu use of one core).


So the solution for the initial problem in my case was a fresh install with the on-board card only!

---

### Post by jespdj on 2009-01-16
Note that you can also get a fast and quiet nVidia card. I have a passively cooled nVidia 8600 GTS in my desktop computer. It has a big metal heatsink, but ofcourse it makes no noise at all. And it's much faster than an Intel GMA 950.

---

### Post by qewrtyuiop on 2009-01-24
I have a similar problem, my aspire one has a GMA950 and it even has trouble scrolling through the simplest of web pages.  It seems as though the graphics card isn't even being used at all as the processor load is much higher then it should be.

---

### Post by mnml on 2009-01-30
If you use 16bit depth it might help to activate the 3d acceleration.

---

