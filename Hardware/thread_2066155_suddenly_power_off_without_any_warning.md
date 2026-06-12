---
title: "suddenly power off without any warning"
date: 2012-10-03
forum: Hardware
---

### Post by agzathot on 2012-10-03
hello people from a week ago my laptop suddently power off without any warning my laptop its an Alienware M11x on windows works like a charm and on ubuntu even better :p

I have a dual boot with burg Win7 Ultimate x64 & Ubuntu 12.04 LTS(x64)

i install Jupiter 0.1.7 since a month ago but the problem start a week ago (already remove jupiter but problem persist)

on which log file i can find why was the power off ?
(its not a shutdown, its like when u remove power cord to a desktop) the laptops battery last for 3 hours with no problem 

or what to check ?

thanks in advance


if needed her is some info about my system:
[HTML]azathoth@Cthulu:~$ lscpu 
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              5
CPU MHz:               1200.000
BogoMIPS:              2393.95
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3
azathoth@Cthulu:~$ [/HTML]
[HTML]azathoth@Cthulu:~$ lsmod 
Module                  Size  Used by
pl2303                 17993  0 
usbserial              47077  1 pl2303
mmc_block              27300  0 
des_generic            21415  0 
md4                    12595  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
usb_storage            49198  0 
michael_mic            12612  8 
arc4                   12529  4 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
dm_crypt               23125  1 
vboxdrv               282587  4 vboxpci,vboxnetadp,vboxnetflt
btusb                  18288  1 
bbswitch               13396  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
joydev                 17693  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 47604  12 
lib80211_crypt_tkip    17390  0 
bnep                   18281  2 
bluetooth             180104  23 btusb,rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_seq_midi           13324  0 
wl                   2568210  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97362  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13211  0 
jmb38x_ms              17646  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
intel_ips              18174  0 
nls_utf8               12557  0 
memstick               16569  1 jmb38x_ms
snd_timer              29990  2 snd_pcm,snd_seq
cifs                  287317  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17540  1 
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uvesafb                29304  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  473240  9 
atl1c                  41718  0 
sdhci_pci              18826  0 
firewire_ohci          41000  0 
sdhci                  33205  1 sdhci_pci
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
drm_kms_helper         46978  1 i915
drm                   242038  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mxm_wmi                12979  0 
wmi                    19256  2 dell_wmi,mxm_wmi
video                  19596  1 i915
azathoth@Cthulu:~$ [/HTML]
[HTML]azathoth@Cthulu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 335M] (rev ff)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
azathoth@Cthulu:~$ [/HTML]
[HTML]azathoth@Cthulu:~$ sudo lshw 
cthulu                    
    description: Portable Computer
    product: M11x R2 (xxx123x#ABA)
    vendor: Alienware
    version: A04
    serial: XXXXXXX
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=portable family=103C_5335KV sku=xxx123x#ABA uuid=44454C4C-3400-104B-8042-C6C04F5A4E31
  *-core
       description: Motherboard
       product: M11x R2
       vendor: Alienware
       physical id: 0
       version: A04
       serial: .       .              .
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Alienware
          physical id: 0
          version: A04
          date: 11/23/2010
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
          vendor: Intel Corp.
          physical id: da01
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU       U 640  @ 1.20GHz
          slot: CPU
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: da02
             slot: L3 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: da04
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: da05
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: da03
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:b0000000-b10fffff ioport:80000000(size=301989888)
           *-generic UNCLAIMED
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:b0000000-b0ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:b1000000-b107ffff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:b1400000-b17fffff memory:a0000000-afffffff ioport:50a8(size=8)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:b7806400-b78067ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel CorporationSeries
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:b7800000-b7803fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05Series
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:b6800000-b77fffff ioport:b1800000(size=16777216)
           *-network DISABLED
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 12:34:56:78:90:ab
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:b6800000-b683ffff ioport:3000(size=128)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:b5800000-b67fffff ioport:b2800000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM43224 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 12:34:56:78:90:ab
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.7.196 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:17 memory:b5800000-b5803fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:b4800000-b57fffff ioport:b3800000(size=16777216)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:b4800000-b48007ff memory:b4800c00-b4800cff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:b4800b00-b4800bff
           *-generic:1
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:b4800900-b48009ff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b7806000-b78063ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series/3400 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:5088(size=8) ioport:50bc(size=4) ioport:5080(size=8) ioport:50b8(size=4) ioport:5050(size=16) ioport:5040(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200BEKT-7
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX61A9067922
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4a7b50b8
              *-volume:0
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 3030-3030
                   size: 39MiB
                   capacity: 39MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 067e-1424
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-08-29 07:05:36 filesystem=ntfs label=RECOVERY state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/Win7
                   version: 3.1
                   serial: e6dd8449-de35-a340-9b46-3c6ab5414ee3
                   size: 140GiB
                   capacity: 140GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-11-19 18:04:10 filesystem=ntfs label=Win7 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 142GiB
                   capacity: 142GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/Data
                      capacity: 122GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 5939MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b7806800-b78068ff ioport:5000(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:5078(size=8) ioport:50b4(size=4) ioport:5070(size=8) ioport:50b0(size=4) ioport:5030(size=16) ioport:5020(size=16)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:21 memory:b7804000-b7804fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: Alienware
       vendor: Alienware
       physical id: 1
       slot: System Battery Bay
       capacity: 43600mWh
       configuration: voltage=14.8V
azathoth@Cthulu:~$[/HTML]

---

### Post by Bucky Ball on 2012-10-03
Just a tip: Use the # code tag instead of the HTML icon. You can also select the code in a quick edit, hit the quote icon then replace where it puts [quote] with [code] at both ends. 

I would be thinking a hardware issue. Does it happen in all OSs and how old is the computer?

---

### Post by 2F4U on 2012-10-04
On first sight, I would be thinking of several things that can cause this:
- power outage with empty batteries
- overheating and emergency shutdown

If it is not too long ago, you might find more information about the issue in the system log file /var/log/syslog, which is also accessible through the Unity GUI.

---

### Post by agzathot on 2012-10-04
ty for the tip Bucky, this isnt happens on windows, i try using a day windows and didnt power off its only happens when use the pure battery (dont happens on windows) its pretty random it could happens on 5 min or on 1 hour, 2f4u i should read syslog on single user mode or when full linux boots ?

---

### Post by TenPlus1 on 2012-10-04
This may sound crazy, but have you setup the proper keyboard during install...  Maybe an incorrect key layout is either sending your laptop to sleep or powering down...

---

