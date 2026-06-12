---
title: "Internal microphone used to be recognized, but not anymore."
date: 2010-01-27
forum: Hardware
---

### Post by leorolla on 2010-01-27
I have an Acer Aspire One D150.

Sound has always worked well. From a fresh Karmic install I add 
```
alias snd-card-0 snd-hda-intel
echo options snd-hda-intel model=acer

```to
/etc/modprobe.d/alsa-base.co

and after rebooting I have the options "Microphone 1" and "Microphone 2" for the sound input.
But a few weeks ago they disappeared and now I only have external microphone.

Have no idea what can be causing this...

A few outputs below.

Thanks for the help!




```
~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
~$ sudo lshw
leorolla-netbook
    description: Computer
    product: Aspire one
    vendor: Acer
    version: V1.05
    serial: LUS570B146911193C41601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal uuid=3A0C840E-6786-726D-0491-00235A5747ED
  *-core
       description: Motherboard
       product: Aspire one
       vendor: Acer
       physical id: 0
       version: V1.05
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.05 (02/20/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305432383634515A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0x63891DCC
             slot: J2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 19
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1a
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1b
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
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
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:56280000-562fffff ioport:50f0(size=8) memory:40000000-4fffffff(prefetchable) memory:56300000-5633ffff
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
             resources: memory:56200000-5627ffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:56340000-56343fff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:4000(size=4096) memory:55100000-561fffff ioport:50000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2b:a2:1a:e7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,02/20/2008, 4.170. ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: irq:16 memory:55100000-55103fff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:3000(size=4096) memory:54100000-550fffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:1000(size=8192) memory:53000000-540fffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:23:5a:57:47:ed
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:53000000-5303ffff ioport:1000(size=128)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5080(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5060(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5040(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:56344400-563447ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             configuration: latency=0
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:50c0(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:50d8(size=8) ioport:50fc(size=4) ioport:50d0(size=8) ioport:50f8(size=4) ioport:5020(size=16) memory:56344000-563443ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54321
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FB2O
                serial: 090227FB2201LCK2BK5B
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d2107a38
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8ca7-5841
                   size: 6149MiB
                   capacity: 6149MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-03-11 10:31:14 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: a4d64a0a-2b27-e449-9422-6cf5b91b07be
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-15 21:50:46 filesystem=ntfs label=ACER state=clean
              *-volume:2
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/DATA
                   version: FAT32
                   serial: 6db2-d24f
                   size: 85GiB
                   capacity: 85GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DATA mount.fstype=vfat mount.options=rw,nosuid,nodev,noexec,relatime,uid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1804MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=32)
~$ sudo lsmod
Module                  Size  Used by
usbhid                 38208  0 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   202336  1 
iptable_filter          3100  0 
snd_hda_intel          26560  4 
snd_hda_codec          78300  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_pcm_oss            37312  0 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                74976  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29280  0 
snd_seq_midi            6624  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                51088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56500  0 
led_class               4096  0 
serio_raw               5280  0 
snd                    60900  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           185532  0 
soundcore               7264  1 snd
snd_page_alloc          9060  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
atl1e                  31824  0 
i915                  221320  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
~$ sudo dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ef000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ef000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  modified: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  modified: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f6bf000 - 000000003f6ef000 (usable)
[    0.000000]  modified: 000000003f6ef000 - 000000003f6ff000 (ACPI data)
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f0ce000 - 2f8584bc
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACER  )
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACER   ACER     00000001      01000013)
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f6f1000 06D91 (v01 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f688000 00040
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f6f0000 00180 (v01 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f6ef000 00028 (v01 ACER   ACER     00000001 1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [002f0ce000 - 002f8584bc]          RAMDISK ==> [002f0ce000 - 002f8584bc]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac148]              BRK ==> [00008a9000 - 00008ac148]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f576
[    0.000000]     0: 0x0003f5bf -> 0x0003f66d
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ef
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259568
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32088 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257537
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=d7324b72-3d0e-418b-b6be-6089cec4068d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1008088k/1039360k available (4566k kernel code, 29736k reserved, 2142k data, 540k init, 129372k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.130 MHz processor.
[    0.001938] Console: colour VGA+ 80x25
[    0.001945] console [tty0] enabled
[    0.002200] hpet clockevent registered
[    0.002208] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002220] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.26 BogoMIPS (lpj=6384520)
[    0.002259] Security Framework initialized
[    0.002298] AppArmor: AppArmor initialized
[    0.002313] Mount-cache hash table entries: 512
[    0.002544] Initializing cgroup subsys ns
[    0.002554] Initializing cgroup subsys cpuacct
[    0.002564] Initializing cgroup subsys memory
[    0.002577] Initializing cgroup subsys freezer
[    0.002582] Initializing cgroup subsys net_cls
[    0.002607] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002613] CPU: L2 cache: 512K
[    0.002618] CPU: Physical Processor ID: 0
[    0.002622] CPU: Processor Core ID: 0
[    0.002629] mce: CPU supports 5 MCE banks
[    0.002643] CPU0: Thermal monitoring enabled (TM2)
[    0.002651] using mwait in idle threads.
[    0.002662] Performance Counters: Atom events, Intel PMU driver.
[    0.002676] ... version:                 3
[    0.002681] ... bit width:               40
[    0.002685] ... generic counters:        2
[    0.002689] ... value mask:              000000ffffffffff
[    0.002694] ... max period:              000000007fffffff
[    0.002699] ... fixed-purpose counters:  3
[    0.002703] ... counter mask:            0000000700000003
[    0.002712] Checking 'hlt' instruction... OK.
[    0.020016] ACPI: Core revision 20090521
[    0.040509] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082403] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383863)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.169009] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.169045] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172051] Brought up 2 CPUs
[    0.172059] Total of 2 processors activated (6384.19 BogoMIPS).
[    0.172128] CPU0 attaching sched-domain:
[    0.172134]  domain 0: span 0-1 level SIBLING
[    0.172141]   groups: 0 1
[    0.172152] CPU1 attaching sched-domain:
[    0.172157]  domain 0: span 0-1 level SIBLING
[    0.172162]   groups: 1 0
[    0.172321] Booting paravirtualized kernel on bare hardware
[    0.172473] regulator: core version 0.5
[    0.172473] Time:  9:43:54  Date: 01/27/10
[    0.172473] NET: Registered protocol family 16
[    0.172473] EISA bus registered
[    0.172473] ACPI: bus type pci registered
[    0.172600] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172607] PCI: MCFG area at e0000000 reserved in E820
[    0.172612] PCI: Using MMCONFIG for extended config space
[    0.172617] PCI: Using configuration type 1 for base access
[    0.176988] bio: create slab <bio-0> at 0
[    0.177948] ACPI: EC: Look up EC in DSDT
[    0.215329] ACPI: BIOS _OSI(Linux) query ignored
[    0.216186] ACPI: Interpreter enabled
[    0.216197] ACPI: (supports S0 S3 S4 S5)
[    0.216250] ACPI: Using IOAPIC for interrupt routing
[    0.248053] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.358282] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.360628] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.360635] ACPI: EC: driver started in interrupt mode
[    0.360774] ACPI: Power Resource [FN00] (on)
[    0.361237] ACPI: No dock devices found.
[    0.362492] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.362508] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.362526] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.362582] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.362733] pci 0000:00:02.0: reg 10 32bit mmio: [0x56280000-0x562fffff]
[    0.362743] pci 0000:00:02.0: reg 14 io port: [0x50f0-0x50f7]
[    0.362753] pci 0000:00:02.0: reg 18 32bit mmio: [0x40000000-0x4fffffff]
[    0.362762] pci 0000:00:02.0: reg 1c 32bit mmio: [0x56300000-0x5633ffff]
[    0.362818] pci 0000:00:02.1: reg 10 32bit mmio: [0x56200000-0x5627ffff]
[    0.362958] pci 0000:00:1b.0: reg 10 64bit mmio: [0x56340000-0x56343fff]
[    0.363032] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.363040] pci 0000:00:1b.0: PME# disabled
[    0.363144] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.363153] pci 0000:00:1c.0: PME# disabled
[    0.363261] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.363269] pci 0000:00:1c.1: PME# disabled
[    0.363375] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.363383] pci 0000:00:1c.2: PME# disabled
[    0.363466] pci 0000:00:1d.0: reg 20 io port: [0x50a0-0x50bf]
[    0.363545] pci 0000:00:1d.1: reg 20 io port: [0x5080-0x509f]
[    0.363625] pci 0000:00:1d.2: reg 20 io port: [0x5060-0x507f]
[    0.363704] pci 0000:00:1d.3: reg 20 io port: [0x5040-0x505f]
[    0.363789] pci 0000:00:1d.7: reg 10 32bit mmio: [0x56344400-0x563447ff]
[    0.363864] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.363873] pci 0000:00:1d.7: PME# disabled
[    0.364090] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.364100] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.364111] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.364119] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.364187] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.364200] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.364212] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.364224] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.364237] pci 0000:00:1f.1: reg 20 io port: [0x50c0-0x50cf]
[    0.364317] pci 0000:00:1f.2: reg 10 io port: [0x50d8-0x50df]
[    0.364330] pci 0000:00:1f.2: reg 14 io port: [0x50fc-0x50ff]
[    0.364342] pci 0000:00:1f.2: reg 18 io port: [0x50d0-0x50d7]
[    0.364355] pci 0000:00:1f.2: reg 1c io port: [0x50f8-0x50fb]
[    0.364367] pci 0000:00:1f.2: reg 20 io port: [0x5020-0x502f]
[    0.364380] pci 0000:00:1f.2: reg 24 32bit mmio: [0x56344000-0x563443ff]
[    0.364426] pci 0000:00:1f.2: PME# supported from D3hot
[    0.364434] pci 0000:00:1f.2: PME# disabled
[    0.364511] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x501f]
[    0.364685] pci 0000:01:00.0: reg 10 64bit mmio: [0x55100000-0x55103fff]
[    0.364793] pci 0000:01:00.0: supports D1 D2
[    0.364798] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.364808] pci 0000:01:00.0: PME# disabled
[    0.364907] pci 0000:00:1c.0: bridge io port: [0x4000-0x4fff]
[    0.364916] pci 0000:00:1c.0: bridge 32bit mmio: [0x55100000-0x561fffff]
[    0.364929] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.365003] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.365012] pci 0000:00:1c.1: bridge 32bit mmio: [0x54100000-0x550fffff]
[    0.365025] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.365115] pci 0000:03:00.0: reg 10 64bit mmio: [0x53000000-0x5303ffff]
[    0.365131] pci 0000:03:00.0: reg 18 io port: [0x1000-0x107f]
[    0.365222] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.365232] pci 0000:03:00.0: PME# disabled
[    0.365319] pci 0000:00:1c.2: bridge io port: [0x1000-0x2fff]
[    0.365328] pci 0000:00:1c.2: bridge 32bit mmio: [0x53000000-0x540fffff]
[    0.365341] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]
[    0.365421] pci 0000:00:1e.0: transparent bridge
[    0.365468] pci_bus 0000:00: on NUMA node 0
[    0.365480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.365885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.366129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.366308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.366704] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.366719] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.373848] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.374102] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.374353] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.374602] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.374851] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.375103] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.375356] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.375607] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.376033] SCSI subsystem initialized
[    0.376115] libata version 3.00 loaded.
[    0.376125] usbcore: registered new interface driver usbfs
[    0.376125] usbcore: registered new interface driver hub
[    0.376144] usbcore: registered new device driver usb
[    0.376244] ACPI: WMI: Mapper loaded
[    0.376249] PCI: Using ACPI for IRQ routing
[    0.388023] Bluetooth: Core ver 2.15
[    0.388068] NET: Registered protocol family 31
[    0.388068] Bluetooth: HCI device and connection manager initialized
[    0.388068] Bluetooth: HCI socket layer initialized
[    0.388068] NetLabel: Initializing
[    0.388068] NetLabel:  domain hash size = 128
[    0.388068] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.388079] NetLabel:  unlabeled traffic allowed by default
[    0.388148] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.388160] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.408025] pnp: PnP ACPI init
[    0.408066] ACPI: bus type pnp registered
[    0.472728] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.2 BAR 13 (0x1000-0x2fff), disabling
[    0.474353] pnp: PnP ACPI: found 9 devices
[    0.474359] ACPI: ACPI bus type pnp unregistered
[    0.474366] PnPBIOS: Disabled by ACPI PNP
[    0.474393] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.474401] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.474408] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.474415] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.474422] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.474429] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.474437] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.474446] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.474454] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.474461] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.474469] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.474477] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.474484] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.474492] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.501079] Switched to high resolution mode on CPU 1
[    0.503986] Switched to high resolution mode on CPU 0
[    0.509369] AppArmor: AppArmor Filesystem Enabled
[    0.509452] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.509460] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    0.509471] pci 0000:00:1c.0:   MEM window: 0x55100000-0x561fffff
[    0.509480] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.509493] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.509500] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.509510] pci 0000:00:1c.1:   MEM window: 0x54100000-0x550fffff
[    0.509519] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.509533] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.509540] pci 0000:00:1c.2:   IO window: 0x1000-0x2fff
[    0.509550] pci 0000:00:1c.2:   MEM window: 0x53000000-0x540fffff
[    0.509559] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff
[    0.509572] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.509577] pci 0000:00:1e.0:   IO window: disabled
[    0.509586] pci 0000:00:1e.0:   MEM window: disabled
[    0.509593] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.509615]   alloc irq_desc for 16 on node -1
[    0.509620]   alloc kstat_irqs on node -1
[    0.509632] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.509642] pci 0000:00:1c.0: setting latency timer to 64
[    0.509656] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.509664]   alloc irq_desc for 17 on node -1
[    0.509669]   alloc kstat_irqs on node -1
[    0.509677] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.509687] pci 0000:00:1c.1: setting latency timer to 64
[    0.509702]   alloc irq_desc for 18 on node -1
[    0.509706]   alloc kstat_irqs on node -1
[    0.509714] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.509723] pci 0000:00:1c.2: setting latency timer to 64
[    0.509736] pci 0000:00:1e.0: setting latency timer to 64
[    0.509746] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.509752] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.509758] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.509765] pci_bus 0000:01: resource 1 mem: [0x55100000-0x561fffff]
[    0.509771] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.509778] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.509784] pci_bus 0000:02: resource 1 mem: [0x54100000-0x550fffff]
[    0.509791] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.509799] pci_bus 0000:03: resource 0 io:  [0x1000-0x2fff]
[    0.509805] pci_bus 0000:03: resource 1 mem: [0x53000000-0x540fffff]
[    0.509811] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.509818] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.509824] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.509900] NET: Registered protocol family 2
[    0.510107] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.510767] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.511738] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512240] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512250] TCP reno registered
[    0.512466] NET: Registered protocol family 1
[    0.512612] Trying to unpack rootfs image as initramfs...
[    0.886154] Freeing initrd memory: 7721k freed
[    0.893480] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.893489] Simple Boot Flag at 0x44 set to 0x1
[    0.893894] cpufreq-nforce2: No nForce2 chipset.
[    0.893954] Scanning for low memory corruption every 60 seconds
[    0.894173] audit: initializing netlink socket (disabled)
[    0.894204] type=2000 audit(1264585433.892:1): initialized
[    0.911639] highmem bounce pool size: 64 pages
[    0.911653] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.914891] VFS: Disk quotas dquot_6.5.2
[    0.915020] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.916304] fuse init (API version 7.12)
[    0.916492] msgmni has been set to 1732
[    0.916985] alg: No test for stdrng (krng)
[    0.917023] io scheduler noop registered
[    0.917029] io scheduler anticipatory registered
[    0.917034] io scheduler deadline registered
[    0.917145] io scheduler cfq registered (default)
[    0.917171] pci 0000:00:02.0: Boot video device
[    0.917616]   alloc irq_desc for 24 on node -1
[    0.917622]   alloc kstat_irqs on node -1
[    0.917643] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.917659] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.917881]   alloc irq_desc for 25 on node -1
[    0.917886]   alloc kstat_irqs on node -1
[    0.917900] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.917916] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.918131]   alloc irq_desc for 26 on node -1
[    0.918136]   alloc kstat_irqs on node -1
[    0.918150] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.918166] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.918351] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.918569] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.918585] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.918847] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.918862] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.919112] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.919126] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.919418] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.919432] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.919684] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.919698] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.919950] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.919965] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7014a50), AE_ALREADY_EXISTS
[    0.920088] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.984160] ACPI: AC Adapter [AC] (on-line)
[    0.984311] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.984319] ACPI: Power Button [PWRF]
[    0.984444] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.984451] ACPI: Power Button [PWRB]
[    0.984545] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.984632] ACPI: Lid Switch [LID0]
[    0.984734] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.984741] ACPI: Sleep Button [SLPB]
[    0.985047] fan PNP0C0B:00: registered as cooling_device0
[    0.985060] ACPI: Fan [FAN] (on)
[    0.986405] ACPI: SSDT 3f592c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.987218] ACPI: SSDT 3f591e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.988864] Marking TSC unstable due to TSC halts in idle
[    0.988898] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.988944] processor LNXCPU:00: registered as cooling_device1
[    0.988953] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.989705] ACPI: SSDT 3f592f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.990436] ACPI: SSDT 3f590f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.992211] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.992263] processor LNXCPU:01: registered as cooling_device2
[    0.992272] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.055046] thermal LNXTHERM:01: registered as thermal_zone0
[    1.055063] ACPI: Thermal Zone [THRM] (27 C)
[    1.055207] isapnp: Scanning for PnP cards...
[    1.409426] isapnp: No Plug & Play device found
[    1.716208] ACPI: Battery Slot [BAT0] (battery present)
[    1.716523] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.719142] brd: module loaded
[    1.720196] loop: module loaded
[    1.720375] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.720544] ahci 0000:00:1f.2: version 3.0
[    1.720574] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.720639]   alloc irq_desc for 27 on node -1
[    1.720644]   alloc kstat_irqs on node -1
[    1.720664] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.720728] ahci: SSS flag set, parallel bus scan disabled
[    1.720777] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.720786] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    1.720795] ahci 0000:00:1f.2: setting latency timer to 64
[    1.721172] scsi0 : ahci
[    1.721419] scsi1 : ahci
[    1.721558] scsi2 : ahci
[    1.721688] scsi3 : ahci
[    1.722070] ata1: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344100 irq 27
[    1.722076] ata2: DUMMY
[    1.722082] ata3: SATA max UDMA/133 abar m1024@0x56344000 port 0x56344200 irq 27
[    1.722088] ata4: DUMMY
[    1.722239] ata_piix 0000:00:1f.1: version 2.13
[    1.722269] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.722351] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.722499] scsi4 : ata_piix
[    1.722642] scsi5 : ata_piix
[    1.723702] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50c0 irq 14
[    1.723710] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50c8 irq 15
[    1.724086] ata6: port disabled. ignoring.
[    1.725758] Fixed MDIO Bus: probed
[    1.725845] PPP generic driver version 2.4.2
[    1.726052] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.726097] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.726128] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.726135] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.726232] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.730149] ehci_hcd 0000:00:1d.7: debug port 1
[    1.730161] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.730193] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56344400
[    1.744030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.744195] usb usb1: configuration #1 chosen from 1 choice
[    1.744266] hub 1-0:1.0: USB hub found
[    1.744283] hub 1-0:1.0: 8 ports detected
[    1.744420] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.744463] uhci_hcd: USB Universal Host Controller Interface driver
[    1.744533] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.744546] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.744553] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.744632] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.744674] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000050a0
[    1.744848] usb usb2: configuration #1 chosen from 1 choice
[    1.744911] hub 2-0:1.0: USB hub found
[    1.744940] hub 2-0:1.0: 2 ports detected
[    1.745035] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.745047] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.745054] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.745132] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.745184] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005080
[    1.745356] usb usb3: configuration #1 chosen from 1 choice
[    1.745418] hub 3-0:1.0: USB hub found
[    1.745432] hub 3-0:1.0: 2 ports detected
[    1.745535] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.745547] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.745554] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.745621] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.745670] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005060
[    1.745842] usb usb4: configuration #1 chosen from 1 choice
[    1.745905] hub 4-0:1.0: USB hub found
[    1.745920] hub 4-0:1.0: 2 ports detected
[    1.746013]   alloc irq_desc for 19 on node -1
[    1.746019]   alloc kstat_irqs on node -1
[    1.746031] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.746042] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.746049] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.746122] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.746172] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00005040
[    1.746337] usb usb5: configuration #1 chosen from 1 choice
[    1.746399] hub 5-0:1.0: USB hub found
[    1.746414] hub 5-0:1.0: 2 ports detected
[    1.746610] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.779128] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.779143] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.779314] mice: PS/2 mouse device common for all mice
[    1.779598] rtc_cmos 00:03: RTC can wake from S4
[    1.779692] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.779741] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.780034] device-mapper: uevent: version 1.0.3
[    1.780261] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.780451] device-mapper: multipath: version 1.1.0 loaded
[    1.780458] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.780762] EISA: Probing bus 0 at eisa.0
[    1.780774] Cannot allocate resource for EISA slot 1
[    1.780779] Cannot allocate resource for EISA slot 2
[    1.780784] Cannot allocate resource for EISA slot 3
[    1.780789] Cannot allocate resource for EISA slot 4
[    1.780794] Cannot allocate resource for EISA slot 5
[    1.780814] EISA: Detected 0 cards.
[    1.781178] cpuidle: using governor ladder
[    1.781376] cpuidle: using governor menu
[    1.782509] TCP cubic registered
[    1.782866] NET: Registered protocol family 10
[    1.783806] lo: Disabled Privacy Extensions
[    1.784529] NET: Registered protocol family 17
[    1.784594] Bluetooth: L2CAP ver 2.13
[    1.784598] Bluetooth: L2CAP socket layer initialized
[    1.784605] Bluetooth: SCO (Voice Link) ver 0.6
[    1.784609] Bluetooth: SCO socket layer initialized
[    1.784715] Bluetooth: RFCOMM TTY layer initialized
[    1.784723] Bluetooth: RFCOMM socket layer initialized
[    1.784727] Bluetooth: RFCOMM ver 1.11
[    1.786545] Using IPI No-Shortcut mode
[    1.786709] PM: Resume from disk failed.
[    1.786735] registered taskstats version 1
[    1.786988]   Magic number: 10:634:728
[    1.787119] rtc_cmos 00:03: setting system clock to 2010-01-27 09:43:55 UTC (1264585435)
[    1.787127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.787131] EDD information not available.
[    1.805423] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.040107] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.041494] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.041707] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
[    2.041723] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.043340] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.043627] ata1.00: configured for UDMA/133
[    2.056108] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.056446] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.056760] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.056889] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.057039] sd 0:0:0:0: [sda] Write Protect is off
[    2.057046] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.057115] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.057472]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.134356] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.362400] usb 1-2: configuration #1 chosen from 1 choice
[    2.376094] ata3: SATA link down (SStatus 0 SControl 300)
[    2.392310] Freeing unused kernel memory: 540k freed
[    2.392847] Write protecting the kernel text: 4568k
[    2.392927] Write protecting the kernel read-only data: 1836k
[    2.665195] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    2.665855] acpi device:1a: registered as cooling_device3
[    2.666309] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input6
[    2.666428] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    2.730947] Linux agpgart interface v0.103
[    2.810776] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    2.811140] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.814206] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    2.931204] [drm] Initialized drm 1.1.0 20060810
[    2.963010] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.963027] i915 0000:00:02.0: setting latency timer to 64
[    2.972121] ATL1E 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.972148] ATL1E 0000:03:00.0: setting latency timer to 64
[    3.196735] [drm] fb0: inteldrmfb frame buffer device
[    3.196752] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.524484] [drm] LVDS-8: set mode 1024x600 e
[    3.982460] Console: switching to colour frame buffer device 128x37
[    4.272923] xor: automatically using best checksumming function: pIII_sse
[    4.289023]    pIII_sse  :  4787.000 MB/sec
[    4.289032] xor: using function: pIII_sse (4787.000 MB/sec)
[    4.295440] device-mapper: dm-raid45: initialized v0.2594b
[    4.807028] PM: Starting manual resume from disk
[    4.807037] PM: Resume from partition 8:6
[    4.807042] PM: Checking hibernation image.
[    4.807331] PM: Resume from disk failed.
[    4.831019] EXT4-fs (sda5): barriers enabled
[    4.848965] kjournald2 starting: pid 379, dev sda5:8, commit interval 5 seconds
[    4.849027] EXT4-fs (sda5): delayed allocation enabled
[    4.849047] EXT4-fs: file extents enabled
[    4.850255] EXT4-fs: mballoc enabled
[    4.850286] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.661140] type=1505 audit(1264585439.372:2): operation="profile_load" pid=402 name=/usr/share/gdm/guest-session/Xsession
[    5.666014] type=1505 audit(1264585439.376:3): operation="profile_load" pid=403 name=/sbin/dhclient3
[    5.666680] type=1505 audit(1264585439.376:4): operation="profile_load" pid=403 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.667012] type=1505 audit(1264585439.376:5): operation="profile_load" pid=403 name=/usr/lib/connman/scripts/dhclient-script
[    5.725952] type=1505 audit(1264585439.436:6): operation="profile_load" pid=404 name=/usr/bin/evince
[    5.735238] type=1505 audit(1264585439.444:7): operation="profile_load" pid=404 name=/usr/bin/evince-previewer
[    5.740970] type=1505 audit(1264585439.452:8): operation="profile_load" pid=404 name=/usr/bin/evince-thumbnailer
[    5.768439] type=1505 audit(1264585439.480:9): operation="profile_load" pid=406 name=/usr/lib/cups/backend/cups-pdf
[    5.769197] type=1505 audit(1264585439.480:10): operation="profile_load" pid=406 name=/usr/sbin/cupsd
[    5.794999] type=1505 audit(1264585439.504:11): operation="profile_load" pid=407 name=/usr/sbin/ntpd
[   19.285551] Adding 1847432k swap on /dev/sda6.  Priority:-1 extents:1 across:1847432k 
[   19.291019] udev: starting version 147
[   19.334195] lp: driver loaded but no devices found
[   19.542841] EXT4-fs (sda5): internal journal on sda5:8
[   19.784594] intel_rng: FWH not detected
[   19.789741] Disabling lock debugging due to kernel taint
[   19.892676] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   20.129156] Linux video capture interface: v2.00
[   20.140074] uvcvideo: Found UVC 1.00 device Webcam (04f2:b084)
[   20.154087] acer-wmi: Acer Laptop ACPI-WMI Extras
[   20.176855] input: Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   20.177008] usbcore: registered new interface driver uvcvideo
[   20.177019] USB Video Class driver (v0.1.0)
[   20.340306] acer-wmi: Unable to detect available WMID devices
[   20.463674] ndiswrapper: driver bcmwl5 (Broadcom,02/20/2008, 4.170.75.0) loaded
[   20.464348] ndiswrapper 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.464575] ndiswrapper 0000:01:00.0: setting latency timer to 64
[   20.476982] ndiswrapper: using IRQ 16
[   20.677195]   alloc irq_desc for 28 on node -1
[   20.677208]   alloc kstat_irqs on node -1
[   20.677246] ATL1E 0000:03:00.0: irq 28 for MSI/MSI-X
[   20.678060] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.967376] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.099843] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.099934]   alloc irq_desc for 29 on node -1
[   21.099941]   alloc kstat_irqs on node -1
[   21.099966] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
[   21.100098] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.255139] wlan0: ethernet device 00:24:2b:a2:1a:e7 using NDIS driver: bcmwl5, version: 0x4aa4b00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4315.5.conf
[   21.255283] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   21.255518] usbcore: registered new interface driver ndiswrapper
[   21.304124] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.341187] hda_codec: ALC272: BIOS auto-probing.
[   21.342531] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   21.616033] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   21.755491] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   21.924292] __ratelimit: 3 callbacks suppressed
[   21.924303] type=1505 audit(1264592655.636:13): operation="profile_replace" pid=951 name=/usr/share/gdm/guest-session/Xsession
[   21.932726] type=1505 audit(1264592655.644:14): operation="profile_replace" pid=952 name=/sbin/dhclient3
[   21.933661] type=1505 audit(1264592655.644:15): operation="profile_replace" pid=952 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.934151] type=1505 audit(1264592655.644:16): operation="profile_replace" pid=952 name=/usr/lib/connman/scripts/dhclient-script
[   21.992427] type=1505 audit(1264592655.704:17): operation="profile_replace" pid=953 name=/usr/bin/evince
[   22.005424] type=1505 audit(1264592655.716:18): operation="profile_replace" pid=953 name=/usr/bin/evince-previewer
[   22.013368] type=1505 audit(1264592655.724:19): operation="profile_replace" pid=953 name=/usr/bin/evince-thumbnailer
[   22.048614] type=1505 audit(1264592655.760:20): operation="profile_replace" pid=958 name=/usr/lib/cups/backend/cups-pdf
[   22.049659] type=1505 audit(1264592655.760:21): operation="profile_replace" pid=958 name=/usr/sbin/cupsd
[   22.080046] type=1505 audit(1264592655.792:22): operation="profile_replace" pid=964 name=/usr/sbin/ntpd
[   23.605799] ppdev: user-space parallel port driver
[   24.314343] CPU0 attaching NULL sched-domain.
[   24.314356] CPU1 attaching NULL sched-domain.
[   24.328138] CPU0 attaching sched-domain:
[   24.328147]  domain 0: span 0-1 level SIBLING
[   24.328154]   groups: 0 1
[   24.328166] CPU1 attaching sched-domain:
[   24.328171]  domain 0: span 0-1 level SIBLING
[   24.328177]   groups: 1 0
[   25.809530] CPU0 attaching NULL sched-domain.
[   25.809546] CPU1 attaching NULL sched-domain.
[   25.828166] CPU0 attaching sched-domain:
[   25.828178]  domain 0: span 0-1 level SIBLING
[   25.828188]   groups: 0 1
[   25.828204] CPU1 attaching sched-domain:
[   25.828212]  domain 0: span 0-1 level SIBLING
[   25.828220]   groups: 1 0
[   41.337680] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   41.893058] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.004047] wlan0: no IPv6 routers present
[ 1691.425044] ALSA hda_intel.c:684: No response from codec, disabling MSI: last cmd=0x018f0900
[ 1692.429022] ALSA hda_intel.c:699: azx_get_response timeout, switching to polling mode: last cmd=0x018f0900
[ 5362.928279] __ratelimit: 3 callbacks suppressed
[ 5362.928295] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 5363.428100] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[ 5363.428150] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC_.BAT0._BST] (Node f7014f18), AE_TIME
[ 5363.428289] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385
[11097.831870] CPU0 attaching NULL sched-domain.
[11097.831882] CPU1 attaching NULL sched-domain.
[11097.845221] CPU0 attaching sched-domain:
[11097.845233]  domain 0: span 0-1 level SIBLING
[11097.845240]   groups: 0 1
[11097.845252]   domain 1: span 0-1 level MC
[11097.845260]    groups: 0-1 (__cpu_power = 2048)
[11097.845276] CPU1 attaching sched-domain:
[11097.845282]  domain 0: span 0-1 level SIBLING
[11097.845289]   groups: 1 0
[11097.845300]   domain 1: span 0-1 level MC
[11097.845306]    groups: 0-1 (__cpu_power = 2048)
[11138.138288] CPU0 attaching NULL sched-domain.
[11138.138303] CPU1 attaching NULL sched-domain.
[11138.156216] CPU0 attaching sched-domain:
[11138.156234]  domain 0: span 0-1 level SIBLING
[11138.156247]   groups: 0 1
[11138.156351] CPU1 attaching sched-domain:
[11138.156358]  domain 0: span 0-1 level SIBLING
[11138.156365]   groups: 1 0
[11147.240131] usb 3-1: new low speed USB device using uhci_hcd and address 2
[11147.408449] usb 3-1: configuration #1 chosen from 1 choice
[11157.192145] usb 3-1: USB disconnect, address 2
[11159.380136] usb 3-2: new low speed USB device using uhci_hcd and address 3
[11159.547546] usb 3-2: configuration #1 chosen from 1 choice
[11159.764369] usbcore: registered new interface driver hiddev
[11159.779615] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input10
[11159.780203] generic-usb 0003:04F3:0210.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-2/input0
[11159.780332] usbcore: registered new interface driver usbhid
[11159.780353] usbhid: v2.6:USB HID core driver
[11424.247249] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
```

---

### Post by leorolla on 2010-01-29
Actually it is now auto-detecting and auto-switching between internal and external microphones.

Amazing.

The only problem is with Skype: for some reason when it is running it prevents the internal mic from recording at all.

---

### Post by Stuart42 on 2010-01-29
When adjusting the sound levels of the mic, try unlocking the channels and adjusting left to 90% and right to 5%

---

### Post by leorolla on 2010-01-30
> **Stuart42 said:**
> When adjusting the sound levels of the mic, try unlocking the channels and adjusting left to 90% and right to 5%

What?!?!?!

It works!!! It works as well for the internal mic as for the external one.

How do you know that?

And why is it so?

Thank you so much.

---

