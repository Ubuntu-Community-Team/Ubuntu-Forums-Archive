---
title: "Machine to slow"
date: 2012-11-03
forum: Hardware
---

### Post by komarx6 on 2012-11-03
I have old IBM X30 and I run Lubuntu. I tried few other light weight distros: Puppy, Cruchbang, Knoppix. I also tried Debian, but as soon as I install graphical environment and reboot I get black screen I can't even just start CLI recovery mode. Distros with openbox didn't work, including lucid puppy. Only time when Openbox worked was when I installed Openbox on Slacko puppy.
This was introduction. Know real problem is that everything thing is so slow. I use Lubuntu, and CPU is, I think, always 100% used.
Could installing Xvesa solve the problem? Would I be able to play video when using Xvesa?
Any expert advices on this?
Here some info:

```
Tasks: 122 total,   1 running, 121 sleeping,   0 stopped,   0 zombie
%Cpu(s): 64.6 us, 33.4 sy,  0.0 ni,  1.7 id,  0.0 wa,  0.0 hi,  0.3 si,  0.0 st
KiB Mem:    369864 total,   346936 used,    22928 free,    11928 buffers
KiB Swap:   572412 total,       92 used,   572320 free,   189280 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                                         
 1002 root      20   0 42252  10m 6044 S  11.2  2.8   3:51.51 Xorg                                                            
 1645 marko     20   0 47844 6072 4860 S   3.0  1.6   1:26.07 lxsession                                                       
 1014 root      20   0 25420 7108 2004 S   1.0  1.9   0:17.04 wicd                                                            
 1073 root      20   0 15160 7700 3664 S   0.7  2.1   0:07.14 wicd-monitor                                                    
21268 root      20   0  5196 1332  968 R   0.7  0.4   0:00.24 top                                                             
  474 messageb  20   0  3844 1596  876 S   0.3  0.4   0:08.89 dbus-daemon                                                     
  628 root      20   0     0    0    0 S   0.3  0.0   0:03.75 ktpacpi_nvramd                                                  
  713 root      20   0 33184 5456 4460 S   0.3  1.5   0:01.38 NetworkManager                                                  
 2499 root      20   0     0    0    0 S   0.3  0.0   0:01.20 kworker/u:0                                                     
13960 marko     20   0  172m  13m 9856 S   0.3  3.6   0:04.79 x-terminal-emul                                                 
22911 marko     20   0  3904 1084  740 S   0.3  0.3   0:00.01 setxkbmap                                                       
    1 root      20   0  3624 1972 1232 S   0.0  0.5   0:01.12 init                                                            
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd                                                        
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.14 ksoftirqd/0                                                     
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0                                                     
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.16 watchdog/0                                                      
    8 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset                                                          
    9 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper                                                         
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs                                                       
   11 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns                                                           
   12 root      20   0     0    0    0 S   0.0  0.0   0:00.02 sync_supers                                                     
   13 root      20   0     0    0    0 S   0.0  0.0   0:00.00 bdi-default                                                     
   14 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kintegrityd                                                     
   15 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kblockd                                                         
   16 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ata_sff                                                         
   17 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khubd                                                           
   18 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 md                                                              
   20 root      20   0     0    0    0 S   0.0  0.0   0:02.23 kworker/0:1                                                     
   21 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khungtaskd                                                      
   22 root      20   0     0    0    0 S   0.0  0.0   0:00.34 kswapd0                                                         
   23 root      25   5     0    0    0 S   0.0  0.0   0:00.00 ksmd                                                            
   24 root      20   0     0    0    0 S   0.0  0.0   0:00.00 fsnotify_mark                                                   
   25 root      20   0     0    0    0 S   0.0  0.0   0:00.00 ecryptfs-kthrea  
```

[IMG]http://www.dodaj.rs/f/3L/12o/1IVPYQEC/htop.png[/IMG]

---

### Post by komarx6 on 2012-11-03
Data from previous post were taken during normal systen state. No special programs were running or loading.

I think that graphics are the main problem, but I have no idea. It has been slow on all distros I tried, more or less.
I think this laptop should be faster, I'm sure. Here's some hardware info:
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

### Post by snowpine on 2012-11-03
>  product: Mobile Intel(R) Pentium(R) III CPU - M  1066MHz

That's your problem there. Upgrading your hardware to newer than Pentium 3 will give you more performance "bang for your buck" than any software solution.

That being said the following article has some fun project ideas for ancient hardware. (Keep in mind the article is 5 years old so while there might have been some debate in 2007 whether yours is "old" or just "aging" there's no question now.)

[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by komarx6 on 2012-11-03
I don't believe that not even Lubuntu can run normaly on this machine.
CPU is 100% almost all the time. This muchine had some adjusted version on Windows XP on it, but it was to slow. I thought that reason is viruses, which were present. But now I think that it might be something else. Maybe some physical damage, if software can't solve the problem.
I'll try to do something about it, and if I succeed I let you know.

---

