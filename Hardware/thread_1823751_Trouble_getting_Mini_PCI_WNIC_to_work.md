---
title: "Trouble getting Mini PCI WNIC to work"
date: 2011-08-12
forum: Hardware
---

### Post by tadpowle on 2011-08-12
I'm trying to upgrade my IBM T30 laptop and just replaced the original Mini PCI WNIC (which was 802.11b only) with an "AIRONET Wireless Communications Cisco Aironet Mini PCI b/g" card and am having problems getting it so work. (I've never used the new card, so I have no proof that it's "good.") 

Anyway here's what I see. from lswh 
(Note: I plug in a Cisco PCMCIA card to get connectivity while trying to fix the Mini PCI card issue, but removed if for the below info.)

lshw returns the below...
.
.
.
[COLOR=Black] *-generic UNCLAIMED
                description: Non-VGA unclassified device
                product: Cisco Aironet Mini PCI b/g
                vendor: AIRONET Wireless Communications[/COLOR]
.
.
.
...and I get no network connectivity.

Any ideas on what I need to do? (is there a good place to find the boot/up sequence where the PCI bus is sized and corresponding driver modules loaded?) 

More info below.

root@tommy-laptop:~# uname -a
Linux tommy-laptop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

root@tommy-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@tommy-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:50:b3:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6784 (6.7 KB)  TX bytes:6784 (6.7 KB)

root@tommy-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Non-VGA unclassified device: AIRONET Wireless Communications Cisco Aironet Mini PCI b/g
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
root@tommy-laptop:~# lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
snd_intel8x0           33213  2 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
snd_ac97_codec        105614  1 snd_intel8x0
airo_cs                12642  0 
airo                   73165  1 airo_cs
ac97_bus               12642  1 snd_ac97_codec
thinkpad_acpi          73750  0 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
ppdev                  12849  0 
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  1 airo_cs
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 radeon,ttm,drm_kms_helper
snd                    55295  12 snd_intel8x0,snd_ac97_codec,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  185091  0 
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
video                  18951  0 
parport_pc             32111  1 
serio_raw              12990  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
nvram                  14035  1 thinkpad_acpi
i2c_algo_bit           13184  1 radeon
crc_ccitt              12595  1 irda
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 

root@tommy-laptop:~# lshw
tommy-laptop              
    
  *-core
       description: Motherboard
       product: 236685U
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: 
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1IET70WW (2.09 )
          date: 08/08/2005
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 Mobile CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 15.2.4
          slot: None
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 2
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:d0100000-d01fffff memory:e8000000-efffffff
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e8000000-efffffff ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
        *-usb:0
             description: USB Controller
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
             description: USB Controller
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
             description: USB Controller
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
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:4000(size=20480) memory:d0200000-dfffffff memory:f0000000-f80fffff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:50000000-50000fff ioport:4000(size=256) ioport:4400(size=256) memory:f0000000-f3ffffff memory:d4000000-d7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:5 memory:51000000-51000fff ioport:4800(size=256) ioport:4c00(size=256) memory:f4000000-f7ffffff memory:d8000000-dbffffff
      [COLOR=Black] [/COLOR][COLOR=Black]   [COLOR=Red] *-generic UNCLAIMED
                description: Non-VGA unclassified device
                product: Cisco Aironet Mini PCI b/g
                vendor: AIRONET Wireless Communications[/COLOR][/COLOR]
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=4
                resources: ioport:8000(size=256) memory:f8000000-f800ffff memory:d0200000-d023ffff memory:0-ffff
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 42
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 memory:d0240000-d0240fff ioport:8400(size=64)
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
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
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
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: HTS541060G9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB3O
                serial: MPB3LAX5K128ZM
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d3904
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   size: 54GiB
                   capacity: 54GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-05 18:18:56 filesystem=ext4 lastmountpoint=/ modified=2011-08-10 15:10:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-08-12 09:02:21 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1021MiB
                   capacity: 1021MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1021MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SR-8177
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NB19
                serial: [
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:1c00(size=256) ioport:18c0(size=64)
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
root@tommy-laptop:~#

---

### Post by tadpowle on 2011-08-15
Just for info in case someone else stumbles upon one of these. 
I've checked this Mini PCI card out and I think I know why it won't function. It's an upgrade for certain Cisco 802.11b Access points (Mini PCI is used in the AP's) but was never sold as a client device. 

It's part number is AIR-MP21G-A-K9

---

