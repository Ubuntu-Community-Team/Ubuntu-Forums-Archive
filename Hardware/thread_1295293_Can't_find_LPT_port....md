---
title: "Can't find LPT port..."
date: 2009-10-19
forum: Hardware
---

### Post by Jannes. on 2009-10-19
Hello my pc can't recognize my parallel port (lp0) thats quite shitty because so i can't plug in my printeR...

Some info:
Printers: Laserjet HP 1100, Deskjet HP 720c (this one does not work in ubuntu 9.04)
OS: UBUNTU 9.04

Some quotes from a dutch ubuntu forum:
I had to do *sudo  lshw*
```
jannes@jannes-desktop:~$ sudo  lshw
[sudo] password for jannes: 
jannes-desktop            
    description: Desktop Computer
    product: DY137A-B14 a540.be
    vendor: HP Pavilion 061
    version: 0b]0211RE101NEON 10
    serial: CZB4160KKY BE420
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=40C672F2-4092-D811-AA01-B227481E86CA
  *-core
       description: Motherboard
       product: Gamila/Giovani/Neon series
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 030
       serial: 4A11407641
       slot: &#65533;PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.09 (03/25/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
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
             version: 02
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
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant Systems, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 10
                serial: 00:0c:76:e1:38:d5
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST3120022A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: 5JT1P9WL
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8a5cbe3c
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 688d15b9-a3e2-46ae-b24b-a24109674f73
                   size: 110GiB
                   capacity: 110GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-06-15 19:48:06 filesystem=ext3 modified=2009-09-07 20:32:09 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-07 20:32:09 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1451MiB
                   capacity: 1451MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=open
           *-cdrom:1
                description: DVD reader
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio dvd
                configuration: status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             size: 249MiB (261MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=9ffe71f2
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/disk
                version: FAT16
                serial: 1030-2714
                size: 249MiB
                capacity: 249MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:8b:c1:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.17 firmware=1.101.2-84 ip=192.168.1.5 link=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:c8:51:c2:12:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jannes@jannes-desktop:~$ 
```

I had to do *LSMOD*
```
jannes@jannes-desktop:~$ lsmod
µModule                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
apm                    25436  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_usb_audio          90528  1 
snd_usb_lib            24320  1 snd_usb_audio
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_hwdep              15108  1 snd_usb_audio
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62756  20 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore              15200  1 snd
pcspkr                 10496  0 
psmouse                61972  0 
nvidia               7097928  34 
intel_agp              34108  1 
quickcam_messenger     21512  0 
usbvideo               34180  1 quickcam_messenger
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
agpgart                42696  2 nvidia,intel_agp
videodev               41600  1 usbvideo
v4l1_compat            21764  1 videodev
serio_raw              13444  0 
shpchp                 40212  0 
at76_usb               77532  0 
usb_storage            99648  1 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
jannes@jannes-desktop:~$ 
```

Also this... *ls  -l  /dev/l**
```
jannes@jannes-desktop:~$ ls  -l  /dev/l*
srw-rw-rw- 1 root root    0 2009-10-18 17:34 /dev/log
brw-rw---- 1 root disk 7, 0 2009-07-21 18:37 /dev/loop0
brw-rw---- 1 root disk 7, 1 2009-10-18 17:34 /dev/loop1
brw-rw---- 1 root disk 7, 2 2009-10-18 17:34 /dev/loop2
brw-rw---- 1 root disk 7, 3 2009-10-18 17:34 /dev/loop3
brw-rw---- 1 root disk 7, 4 2009-10-18 17:34 /dev/loop4
brw-rw---- 1 root disk 7, 5 2009-10-18 17:34 /dev/loop5
brw-rw---- 1 root disk 7, 6 2009-10-18 17:34 /dev/loop6
brw-rw---- 1 root disk 7, 7 2009-10-18 17:34 /dev/loop7
jannes@jannes-desktop:~$ 
```

and again no lp0 recognized.

So plz help me...

---

### Post by Giblet5 on 2009-10-19
Do you have a 25-pin parallel port on your motherboard?

Is the port enabled in BIOS?

Some vendors disable it in BIOS - this frees up one primary IRQ and only those of us who dabble in parallel I/O gadgets ever use them in this millenium.

Parallel is so ... 1960. ;) Do you have single-side 8-inch floppy drives too? :)

---

### Post by Jannes. on 2009-10-19
My pc is from 2003...

Yeah got floppy hole and the parallel one is one with 25 holes...
and its stuck on my motherboard... built in...

i dont know how to check if its loaded in bios... i know that there are some options in my bios... for lpt but i don't know the difference...

---

### Post by Jannes. on 2009-10-19
Problem solved !!!

I did this...

- sudo modprobe parport_pc
- lsmod | grep -e parport

---

