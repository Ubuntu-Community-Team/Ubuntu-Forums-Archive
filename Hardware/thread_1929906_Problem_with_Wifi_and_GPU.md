---
title: "Problem with Wifi and GPU"
date: 2012-02-22
forum: Hardware
---

### Post by mitherdil on 2012-02-22
In Ubuntu 11.10, video works well, but wifi dont (wlanX interface doesnt exists). In Ubuntu 10.04, with a little effort, wifi works, but video dont (only one low res mode is allowed).
I've tried to upgrade kernel in 10.04 (to 3.0.0-15, with oneiric-backports-modules-headers), and it got 11.10 issues, but solved video problem.

I know thats not a hardware problem, since both works well, natively, under Window$7.](*,)

Thanks a lot, in advance... and sorry for my grammar mistakes. :tongue:



lspci:
```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
02:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
04:00.0 USB Controller: Device 1b21:1042
```lsmod:
```
Module                  Size  Used by
usbhid                 46754  0 
hid                    95075  1 usbhid
nls_utf8               12557  1 
isofs                  40065  1 
binfmt_misc            17498  1 
ppdev                  17180  0 
snd_hda_codec_hdmi     31787  1 
snd_hda_codec_idt      70187  1 
snd_hda_intel          32995  2 
snd_hda_codec         104241  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13652  1 snd_hda_codec
snd_pcm                96468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30385  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
jme                    40472  0 
rtl8192ce              84590  0 
rtl8192c_common        75767  1 rtl8192ce
i915                  531973  2 
rtlwifi               110110  1 rtl8192ce
sdhci_pci              13966  0 
drm_kms_helper         42261  1 i915
drm                   235841  2 i915,drm_kms_helper
i2c_algo_bit           13368  1 i915
mei                    40857  0 
jmb38x_ms              17458  0 
memstick               16563  1 jmb38x_ms
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              451310  3 rtl8192ce,rtl8192c_common,rtlwifi
sparse_keymap          13890  0 
psmouse                73608  0 
sdhci                  31611  1 sdhci_pci
serio_raw              13208  0 
xhci_hcd               81897  0 
snd                    68011  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
wmi                    19141  0 
cfg80211              194116  2 rtlwifi,mac80211
video                  19280  1 i915
lp                     17789  0 
parport                46360  2 ppdev,lp
ahci                   26002  5 
libahci                30767  1 ahci
```lshw:
```
    description: Desktop Computer
    product: O.E.M
    vendor: O.E.M
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: HURONRIVER
       vendor: INTEL Corporation
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.03.Qbex Test (04/01/2011)
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal unified
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: J1115-0052-QBEX...
             vendor: 0000
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: DIMM1
        *-bank:2
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: J1115-0052-QBEX...
             vendor: 0000
             physical id: 2
             serial: 00000000
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: DIMM3
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f6400000-f67fffff memory:e0000000-efffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:f7e0a000-f7e0a00f
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7e08000-f7e083ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f7e00000-f7e03fff
        *-pci:0
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f7200000-f7bfffff ioport:f0a00000(size=10485760)
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:e000(size=256) memory:f7200000-f7203fff
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:f7d00000-f7dfffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:f7d06000-f7d060ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f7d05000-f7d050ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:f7d04000-f7d040ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:02:00.5
                logical name: eth0
                version: 03
                serial: 80:ee:73:15:f5:c3
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=10.62.6.175 latency=0 link=yes multicast=yes port=MII speed=1GB/s
                resources: irq:48 memory:f7d00000-f7d03fff ioport:d100(size=128) ioport:d000(size=256)
        *-pci:2
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) memory:f6800000-f71fffff ioport:f0000000(size=10485760)
        *-pci:3
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f7c00000-f7cfffff
           *-usb
                description: USB Controller
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:f7c00000-f7c07fff
        *-usb:1
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7e07000-f7e073ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Cougar Point 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e06000-f7e067ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HN-M500M
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AR1
                serial: S2R7J9CB504622
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0d13dbc5
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   size: 68GiB
                   capacity: 68GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 15GiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 53GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 5a02-100b
                   size: 81MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-01-11 10:21:00 filesystem=ntfs label=Reservado pelo Sistema state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /windows
                   version: 3.1
                   serial: 9299492d-a523-3943-9bd5-7bbcf1aab2ab
                   size: 70GiB
                   capacity: 70GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-11 10:21:28 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: 4db18c31-16f2-47c9-acfc-b1502e97e1c7
                   size: 327GiB
                   capacity: 327GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-02-21 23:36:53 filesystem=ext4 lastmountpoint=/home!&#456;&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;!&#456;&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;(&#1925;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;!&#456;&#65533;&#65533;@5 modified=2012-02-22 20:31:20 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-02-22 20:31:20 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633F
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Mp3 #8
                version: TM00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Mp3 #8
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: Cougar Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7e05000-f7e050ff ioport:f040(size=32)
  *-battery:0
       description: Nickel Cadmium Battery
       product: Battery Name
       vendor: Battery Manufacturer
       physical id: 1
       version: 01/01/2007
       serial: Serial Number
       slot: Location of the battery
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-battery:1
       description: Nickel Cadmium Battery
       product: BATT 1
       vendor: Battery Manufacturer
       physical id: 3
       version: 01/01/2007
       serial: Serial Number
       slot: Location of the battery
       capacity: 232mWh
       configuration: voltage=5.0V
```dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #26~lucid1-Ubuntu SMP Wed Jan 25 15:37:10 UTC 2012 (Ubuntu 3.0.0-15.26~lucid1-generic 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=82e39416-7198-4b33-bbbd-1729e44b9bb0 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a800 (usable)
[    0.000000]  BIOS-e820: 000000000009a800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000da842000 (usable)
[    0.000000]  BIOS-e820: 00000000da842000 - 00000000da885000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da885000 - 00000000dac5c000 (usable)
[    0.000000]  BIOS-e820: 00000000dac5c000 - 00000000dade8000 (reserved)
[    0.000000]  BIOS-e820: 00000000dade8000 - 00000000dafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dafe8000 - 00000000db000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f80f8000 - 00000000f80f9000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: O.E.M               O.E.M                   /HURONRIVER, BIOS 1.03.Qbex Test 04/01/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 21FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 8702MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8118M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8702MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdac5c max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcdb0] fcdb0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dac5c000
[    0.000000]  0000000000 - 00dac00000 page 2M
[    0.000000]  00dac00000 - 00dac5c000 page 4k
[    0.000000] kernel direct mapping tables up to dac5c000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021fe00000
[    0.000000]  0100000000 - 021fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 21fe00000 @ dac52000-dac5c000
[    0.000000] RAMDISK: 17765000 - 18040000
[    0.000000] ACPI: RSDP 00000000000f0430 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000dafd3068 00054 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000dafdd618 000F4 (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000dafd3150 0A4C4 (v02 AHV000 AHV00000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dafdff80 00040
[    0.000000] ACPI: APIC 00000000dafdd710 00072 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000dafdd788 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000dafdd7c8 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT 00000000dafdd800 007B3 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000dafddfb8 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000021fe00000
[    0.000000]   NODE_DATA [000000021fdfb000 - 000000021fdfffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217400000-ffff88021e5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000da842
[    0.000000]     0: 0x000da885 -> 0x000dac5c
[    0.000000]     0: 0x00100000 -> 0x0021fe00
[    0.000000] On node 0 totalpages: 2074019
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3917 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 876625 pages, LIFO batch:31
[    0.000000]   Normal zone: 16121 pages used for memmap
[    0.000000]   Normal zone: 1163015 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da842000 - 00000000da885000
[    0.000000] PM: Registered nosave memory: 00000000dac5c000 - 00000000dade8000
[    0.000000] PM: Registered nosave memory: 00000000dade8000 - 00000000dafe8000
[    0.000000] PM: Registered nosave memory: 00000000dafe8000 - 00000000db000000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000f80f8000
[    0.000000] PM: Registered nosave memory: 00000000f80f8000 - 00000000f80f9000
[    0.000000] PM: Registered nosave memory: 00000000f80f9000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at db000000 (gap: db000000:1d0f8000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021fa00000 s79680 r8192 d22720 u524288
[    0.000000] pcpu-alloc: s79680 r8192 d22720 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2043557
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=82e39416-7198-4b33-bbbd-1729e44b9bb0 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8090188k/8910848k available (6120k kernel code, 614772k absent, 205888k reserved, 4864k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2294.526 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4589.05 BogoMIPS (lpj=9178104)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000799] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002607] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003359] Mount-cache hash table entries: 256
[    0.003451] Initializing cgroup subsys cpuacct
[    0.003455] Initializing cgroup subsys memory
[    0.003461] Initializing cgroup subsys devices
[    0.003463] Initializing cgroup subsys freezer
[    0.003464] Initializing cgroup subsys net_cls
[    0.003466] Initializing cgroup subsys blkio
[    0.003471] Initializing cgroup subsys perf_event
[    0.003495] CPU: Physical Processor ID: 0
[    0.003496] CPU: Processor Core ID: 0
[    0.003501] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003502] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003505] mce: CPU supports 7 MCE banks
[    0.003516] CPU0: Thermal monitoring enabled (TM1)
[    0.003523] using mwait in idle threads.
[    0.006267] ACPI: Core revision 20110413
[    0.019557] ftrace: allocating 24417 entries in 96 pages
[    0.029407] x2apic not enabled, IRQ remapping init failed
[    0.029841] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069501] CPU0: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz stepping 07
[    0.175135] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.175141] ... version:                3
[    0.175143] ... bit width:              48
[    0.175144] ... generic registers:      4
[    0.175145] ... value mask:             0000ffffffffffff
[    0.175146] ... max period:             000000007fffffff
[    0.175148] ... fixed-purpose events:   3
[    0.175149] ... event mask:             000000070000000f
[    0.175284] Booting Node   0, Processors  #1
[    0.175286] smpboot cpu 1: start_ip = 95000
[    0.283276]  #2
[    0.283278] smpboot cpu 2: start_ip = 95000
[    0.391179]  #3 Ok.
[    0.391181] smpboot cpu 3: start_ip = 95000
[    0.499007] Brought up 4 CPUs
[    0.499010] Total of 4 processors activated (18357.15 BogoMIPS).
[    0.501622] devtmpfs: initialized
[    0.501736] PM: Registering ACPI NVS region at da842000 (274432 bytes)
[    0.501742] PM: Registering ACPI NVS region at dade8000 (2097152 bytes)
[    0.503111] print_constraints: dummy: 
[    0.503144] Time: 20:31:07  Date: 02/22/12
[    0.503170] NET: Registered protocol family 16
[    0.503257] Trying to unpack rootfs image as initramfs...
[    0.503264] ACPI: bus type pci registered
[    0.503313] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.503316] PCI: not using MMCONFIG
[    0.503317] PCI: Using configuration type 1 for base access
[    0.503931] bio: create slab <bio-0> at 0
[    0.505689] ACPI: EC: Look up EC in DSDT
[    0.507315] ACPI: Executed 1 blocks of module-level executable AML code
[    0.542981] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.543308] ACPI: SSDT 00000000dadd1698 00615 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.543733] ACPI: Dynamic OEM Table Load:
[    0.543736] ACPI: SSDT           (null) 00615 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.575158] ACPI: SSDT 00000000dadd2a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.575614] ACPI: Dynamic OEM Table Load:
[    0.575616] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.599005] ACPI: SSDT 00000000dadd0d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.599428] ACPI: Dynamic OEM Table Load:
[    0.599430] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.629028] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.654930] ACPI: Interpreter enabled
[    0.654934] ACPI: (supports S0 S1 S3 S4 S5)
[    0.654960] ACPI: Using IOAPIC for interrupt routing
[    0.654985] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.655416] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.675986] Freeing initrd memory: 9068k freed
[    0.715076] ACPI: Power Resource [FN00] (off)
[    0.715149] ACPI: Power Resource [FN01] (off)
[    0.715222] ACPI: Power Resource [FN02] (off)
[    0.715292] ACPI: Power Resource [FN03] (off)
[    0.715361] ACPI: Power Resource [FN04] (off)
[    0.715657] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.715865] ACPI: No dock devices found.
[    0.715866] HEST: Table not found.
[    0.715869] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.716107] \_SB_.PCI0:_OSC invalid UUID
[    0.716108] _OSC request data:1 8 1f 
[    0.716112] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.716508] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.716510] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.716512] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.716515] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.716517] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.716519] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.716521] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.716523] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.716525] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.716527] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    0.716529] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.716541] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.716576] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    0.716586] pci 0000:00:02.0: reg 10: [mem 0xf6400000-0xf67fffff 64bit]
[    0.716593] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.716598] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.716668] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.716703] pci 0000:00:16.0: reg 10: [mem 0xf7e0a000-0xf7e0a00f 64bit]
[    0.716797] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.716803] pci 0000:00:16.0: PME# disabled
[    0.716853] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.716884] pci 0000:00:1a.0: reg 10: [mem 0xf7e08000-0xf7e083ff]
[    0.716995] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.717000] pci 0000:00:1a.0: PME# disabled
[    0.717034] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.717060] pci 0000:00:1b.0: reg 10: [mem 0xf7e00000-0xf7e03fff 64bit]
[    0.717156] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.717161] pci 0000:00:1b.0: PME# disabled
[    0.717193] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.717293] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.717298] pci 0000:00:1c.0: PME# disabled
[    0.717331] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.717433] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.717438] pci 0000:00:1c.1: PME# disabled
[    0.717472] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    0.717573] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.717578] pci 0000:00:1c.2: PME# disabled
[    0.717613] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.717713] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.717718] pci 0000:00:1c.4: PME# disabled
[    0.717764] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.717794] pci 0000:00:1d.0: reg 10: [mem 0xf7e07000-0xf7e073ff]
[    0.717907] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.717912] pci 0000:00:1d.0: PME# disabled
[    0.717945] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    0.718109] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.718143] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.718155] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.718169] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.718183] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.718197] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.718211] pci 0000:00:1f.2: reg 24: [mem 0xf7e06000-0xf7e067ff]
[    0.718273] pci 0000:00:1f.2: PME# supported from D3hot
[    0.718278] pci 0000:00:1f.2: PME# disabled
[    0.718305] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.718331] pci 0000:00:1f.3: reg 10: [mem 0xf7e05000-0xf7e050ff 64bit]
[    0.718369] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.718527] pci 0000:01:00.0: [10ec:8176] type 0 class 0x000280
[    0.718572] pci 0000:01:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.718650] pci 0000:01:00.0: reg 18: [mem 0xf7200000-0xf7203fff 64bit]
[    0.718809] pci 0000:01:00.0: supports D1 D2
[    0.718810] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.718821] pci 0000:01:00.0: PME# disabled
[    0.726868] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.726879] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.726889] pci 0000:00:1c.0:   bridge window [mem 0xf7200000-0xf7bfffff]
[    0.726903] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf13fffff 64bit pref]
[    0.727017] pci 0000:02:00.0: [197b:2382] type 0 class 0x000880
[    0.727045] pci 0000:02:00.0: reg 10: [mem 0xf7d06000-0xf7d060ff]
[    0.727259] pci 0000:02:00.2: [197b:2381] type 0 class 0x000805
[    0.727288] pci 0000:02:00.2: reg 10: [mem 0xf7d05000-0xf7d050ff]
[    0.727497] pci 0000:02:00.3: [197b:2383] type 0 class 0x000880
[    0.727526] pci 0000:02:00.3: reg 10: [mem 0xf7d04000-0xf7d040ff]
[    0.727738] pci 0000:02:00.5: [197b:0250] type 0 class 0x000200
[    0.727765] pci 0000:02:00.5: reg 10: [mem 0xf7d00000-0xf7d03fff]
[    0.727804] pci 0000:02:00.5: reg 18: [io  0xd100-0xd17f]
[    0.727825] pci 0000:02:00.5: reg 1c: [io  0xd000-0xd0ff]
[    0.727937] pci 0000:02:00.5: PME# supported from D0 D3hot D3cold
[    0.727943] pci 0000:02:00.5: PME# disabled
[    0.734857] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.734867] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    0.734876] pci 0000:00:1c.1:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.734892] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.734985] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.734990] pci 0000:00:1c.2:   bridge window [io  0xc000-0xcfff]
[    0.734995] pci 0000:00:1c.2:   bridge window [mem 0xf6800000-0xf71fffff]
[    0.735004] pci 0000:00:1c.2:   bridge window [mem 0xf0000000-0xf09fffff 64bit pref]
[    0.735108] pci 0000:04:00.0: [1b21:1042] type 0 class 0x000c03
[    0.735144] pci 0000:04:00.0: reg 10: [mem 0xf7c00000-0xf7c07fff 64bit]
[    0.735304] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.735310] pci 0000:04:00.0: PME# disabled
[    0.742842] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
[    0.742852] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.742862] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.742877] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.742932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.743062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.743094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.743128] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.743160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.743251] \_SB_.PCI0:_OSC invalid UUID
[    0.743252] _OSC request data:1 1f 1f 
[    0.743256]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.743284] \_SB_.PCI0:_OSC invalid UUID
[    0.743286] _OSC request data:1 0 1d 
[    0.743289]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.743290] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.746734] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.746779] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.746825] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.746867] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.746910] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.746957] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.746999] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.747040] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.747126] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.747133] vgaarb: loaded
[    0.747134] vgaarb: bridge control possible 0000:00:02.0
[    0.747271] SCSI subsystem initialized
[    0.747318] libata version 3.00 loaded.
[    0.747349] usbcore: registered new interface driver usbfs
[    0.747358] usbcore: registered new interface driver hub
[    0.747378] usbcore: registered new device driver usb
[    0.747442] PCI: Using ACPI for IRQ routing
[    0.750587] PCI: pci_cache_line_size set to 64 bytes
[    0.750685] reserve RAM buffer: 000000000009a800 - 000000000009ffff 
[    0.750687] reserve RAM buffer: 00000000da842000 - 00000000dbffffff 
[    0.750689] reserve RAM buffer: 00000000dac5c000 - 00000000dbffffff 
[    0.750692] reserve RAM buffer: 000000021fe00000 - 000000021fffffff 
[    0.750764] NetLabel: Initializing
[    0.750766] NetLabel:  domain hash size = 128
[    0.750767] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.750775] NetLabel:  unlabeled traffic allowed by default
[    0.750818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.750824] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.753840] Switching to clocksource hpet
[    0.754815] Switched to NOHz mode on CPU #0
[    0.754871] Switched to NOHz mode on CPU #3
[    0.754916] Switched to NOHz mode on CPU #2
[    0.754956] Switched to NOHz mode on CPU #1
[    0.758531] AppArmor: AppArmor Filesystem Enabled
[    0.758551] pnp: PnP ACPI init
[    0.758563] ACPI: bus type pnp registered
[    0.758789] pnp 00:00: [bus 00-3e]
[    0.758792] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.758793] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.758795] pnp 00:00: [io  0x0d00-0xffff window]
[    0.758797] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.758799] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.758801] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.758803] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.758804] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.758806] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.758808] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.758810] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.758814] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.758816] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.758818] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.758820] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.758822] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.758823] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.758825] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    0.758827] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.758901] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.758913] pnp 00:01: [io  0x0000-0x001f]
[    0.758915] pnp 00:01: [io  0x0081-0x0091]
[    0.758917] pnp 00:01: [io  0x0093-0x009f]
[    0.758918] pnp 00:01: [io  0x00c0-0x00df]
[    0.758920] pnp 00:01: [dma 4]
[    0.758938] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.758946] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.758961] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.759028] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.759047] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.759057] pnp 00:04: [io  0x002e-0x002f]
[    0.759058] pnp 00:04: [io  0x004e-0x004f]
[    0.759060] pnp 00:04: [io  0x0061]
[    0.759061] pnp 00:04: [io  0x0063]
[    0.759063] pnp 00:04: [io  0x0065]
[    0.759064] pnp 00:04: [io  0x0067]
[    0.759065] pnp 00:04: [io  0x0070]
[    0.759067] pnp 00:04: [io  0x0080]
[    0.759068] pnp 00:04: [io  0x0092]
[    0.759070] pnp 00:04: [io  0x00b2-0x00b3]
[    0.759071] pnp 00:04: [io  0x0680-0x069f]
[    0.759073] pnp 00:04: [io  0x1000-0x100f]
[    0.759074] pnp 00:04: [io  0xffff]
[    0.759076] pnp 00:04: [io  0xffff]
[    0.759077] pnp 00:04: [io  0x0400-0x0453]
[    0.759079] pnp 00:04: [io  0x0458-0x047f]
[    0.759080] pnp 00:04: [io  0x0500-0x057f]
[    0.759082] pnp 00:04: [io  0x164e-0x164f]
[    0.759122] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.759124] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.759127] system 00:04: [io  0xffff] has been reserved
[    0.759129] system 00:04: [io  0xffff] has been reserved
[    0.759131] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.759133] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.759135] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.759137] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.759139] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.759146] pnp 00:05: [io  0x0070-0x0077]
[    0.759156] pnp 00:05: [irq 8]
[    0.759173] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.759198] pnp 00:06: [io  0x0454-0x0457]
[    0.759226] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.759229] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.759248] pnp 00:07: [io  0x0010-0x001f]
[    0.759249] pnp 00:07: [io  0x0022-0x003f]
[    0.759251] pnp 00:07: [io  0x0044-0x005f]
[    0.759253] pnp 00:07: [io  0x0072-0x007f]
[    0.759254] pnp 00:07: [io  0x0080]
[    0.759255] pnp 00:07: [io  0x0084-0x0086]
[    0.759258] pnp 00:07: [io  0x0088]
[    0.759260] pnp 00:07: [io  0x008c-0x008e]
[    0.759261] pnp 00:07: [io  0x0090-0x009f]
[    0.759263] pnp 00:07: [io  0x00a2-0x00bf]
[    0.759264] pnp 00:07: [io  0x00e0-0x00ef]
[    0.759266] pnp 00:07: [io  0x04d0-0x04d1]
[    0.759297] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.759299] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.759306] pnp 00:08: [io  0x00f0-0x00ff]
[    0.759311] pnp 00:08: [irq 13]
[    0.759330] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.759348] pnp 00:09: [io  0x0060]
[    0.759350] pnp 00:09: [io  0x0064]
[    0.759355] pnp 00:09: [irq 1]
[    0.759374] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.759417] pnp 00:0a: [irq 12]
[    0.759436] pnp 00:0a: Plug and Play ACPI device, IDs STLc043 PNP0f13 (active)
[    0.759649] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    0.759651] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    0.759653] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    0.759654] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    0.759656] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    0.759658] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    0.759659] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    0.759661] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    0.759663] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    0.759664] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.759666] pnp 00:0b: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.759668] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    0.759721] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.759723] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.759725] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.759727] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.759730] system 00:0b: [mem 0xf8000000-0xfbffffff] could not be reserved
[    0.759732] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.759734] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.759737] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.759739] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.759741] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.759743] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.759746] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.759858] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.759859] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    0.759908] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.759910] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    0.759913] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.773904] pnp: PnP ACPI: found 13 devices
[    0.773909] ACPI: ACPI bus type pnp unregistered
[    0.779459] PCI: max bus depth: 1 pci_try_num: 2
[    0.779508] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.779512] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.779519] pci 0000:00:1c.0:   bridge window [mem 0xf7200000-0xf7bfffff]
[    0.779525] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf13fffff 64bit pref]
[    0.779534] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.779537] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    0.779544] pci 0000:00:1c.1:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.779549] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.779558] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.779561] pci 0000:00:1c.2:   bridge window [io  0xc000-0xcfff]
[    0.779568] pci 0000:00:1c.2:   bridge window [mem 0xf6800000-0xf71fffff]
[    0.779574] pci 0000:00:1c.2:   bridge window [mem 0xf0000000-0xf09fffff 64bit pref]
[    0.779583] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
[    0.779584] pci 0000:00:1c.4:   bridge window [io  disabled]
[    0.779591] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.779596] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.779617] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.779623] pci 0000:00:1c.0: setting latency timer to 64
[    0.779635] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.779640] pci 0000:00:1c.1: setting latency timer to 64
[    0.779650] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.779656] pci 0000:00:1c.2: setting latency timer to 64
[    0.779664] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.779669] pci 0000:00:1c.4: setting latency timer to 64
[    0.779673] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.779675] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.779677] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.779679] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.779681] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.779683] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.779685] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.779686] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.779688] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.779690] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.779692] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    0.779694] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.779696] pci_bus 0000:01: resource 1 [mem 0xf7200000-0xf7bfffff]
[    0.779698] pci_bus 0000:01: resource 2 [mem 0xf0a00000-0xf13fffff 64bit pref]
[    0.779700] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.779702] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.779704] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.779706] pci_bus 0000:03: resource 1 [mem 0xf6800000-0xf71fffff]
[    0.779708] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf09fffff 64bit pref]
[    0.779710] pci_bus 0000:04: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.779733] NET: Registered protocol family 2
[    0.779955] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.780917] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.782218] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.782347] TCP: Hash tables configured (established 524288 bind 65536)
[    0.782349] TCP reno registered
[    0.782364] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.782399] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.782485] NET: Registered protocol family 1
[    0.782498] pci 0000:00:02.0: Boot video device
[    1.037810] PCI: CLS 64 bytes, default 64
[    1.037812] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.037815] Placing 64MB software IO TLB between ffff8800d6842000 - ffff8800da842000
[    1.037817] software IO TLB at phys 0xd6842000 - 0xda842000
[    1.038201] audit: initializing netlink socket (disabled)
[    1.038208] type=2000 audit(1329942666.872:1): initialized
[    1.065152] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.082623] VFS: Disk quotas dquot_6.5.2
[    1.082670] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.083160] fuse init (API version 7.16)
[    1.083228] msgmni has been set to 15818
[    1.083606] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.083637] io scheduler noop registered
[    1.083639] io scheduler deadline registered
[    1.083669] io scheduler cfq registered (default)
[    1.084024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.084041] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.084075] intel_idle: MWAIT substates: 0x21120
[    1.084077] intel_idle: v0.4 model 0x2A
[    1.084078] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.121713] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.161721] ACPI: AC Adapter [AC0] (on-line)
[    1.161822] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.161827] ACPI: Power Button [PWRB]
[    1.161856] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.161859] ACPI: Sleep Button [SLPB]
[    1.161889] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.161930] ACPI: Lid Switch [LID0]
[    1.161961] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.161964] ACPI: Power Button [PWRF]
[    1.189716] ACPI: Fan [FAN0] (off)
[    1.189743] ACPI: Fan [FAN1] (off)
[    1.189767] ACPI: Fan [FAN2] (off)
[    1.189790] ACPI: Fan [FAN3] (off)
[    1.189813] ACPI: Fan [FAN4] (off)
[    1.189819] ACPI: acpi_idle yielding to intel_idle
[    1.205946] thermal LNXTHERM:00: registered as thermal_zone0
[    1.205948] ACPI: Thermal Zone [TZ00] (28 C)
[    1.206090] thermal LNXTHERM:01: registered as thermal_zone1
[    1.206091] ACPI: Thermal Zone [TZ01] (30 C)
[    1.206110] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.206122] ERST: Table is not found!
[    1.206161] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.525582] Linux agpgart interface v0.103
[    1.525654] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.525783] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.526946] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.527042] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.527801] brd: module loaded
[    1.528144] loop: module loaded
[    1.528461] Fixed MDIO Bus: probed
[    1.528478] PPP generic driver version 2.4.2
[    1.528504] tun: Universal TUN/TAP device driver, 1.6
[    1.528506] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.528569] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.528586] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.528602] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.528606] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.528629] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.528657] ehci_hcd 0000:00:1a.0: debug port 2
[    1.532527] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.532544] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    1.545434] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.545584] hub 1-0:1.0: USB hub found
[    1.545588] hub 1-0:1.0: 2 ports detected
[    1.545644] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.545656] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.545659] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.545686] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.545710] ehci_hcd 0000:00:1d.0: debug port 2
[    1.549607] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.549619] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    1.565427] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.565561] hub 2-0:1.0: USB hub found
[    1.565564] hub 2-0:1.0: 2 ports detected
[    1.565607] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.565616] uhci_hcd: USB Universal Host Controller Interface driver
[    1.565675] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:AVC0] at 0x60,0x64 irq 1,12
[    1.572182] i8042: Detected active multiplexing controller, rev 1.0
[    1.573068] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.573074] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.573095] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.573110] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.573127] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.573200] mousedev: PS/2 mouse device common for all mice
[    1.573322] rtc_cmos 00:05: RTC can wake from S4
[    1.573434] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.573467] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.573544] device-mapper: uevent: version 1.0.3
[    1.573602] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.573710] cpuidle: using governor ladder
[    1.573855] cpuidle: using governor menu
[    1.573856] EFI Variables Facility v0.08 2004-May-17
[    1.574064] TCP cubic registered
[    1.574164] NET: Registered protocol family 10
[    1.574554] NET: Registered protocol family 17
[    1.574574] Registering the dns_resolver key type
[    1.574645] PM: Hibernation image not present or could not be loaded.
[    1.574653] registered taskstats version 1
[    1.583107] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.588704]   Magic number: 0:229:549
[    1.588719] tty ttyS25: hash matches
[    1.588745] pci_link PNP0C0F:00: hash matches
[    1.588804] rtc_cmos 00:05: setting system clock to 2012-02-22 20:31:08 UTC (1329942668)
[    1.666401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.666403] EDD information not available.
[    1.667629] Freeing unused kernel memory: 988k freed
[    1.667721] Write protecting the kernel read-only data: 10240k
[    1.667918] Freeing unused kernel memory: 4k freed
[    1.671004] Freeing unused kernel memory: 1416k freed
[    1.681210] udev: starting version 151
[    1.681247] udevd (84): /proc/84/oom_adj is deprecated, please use /proc/84/oom_score_adj instead.
[    1.717631] ACPI: Battery Slot [BAT0] (battery present)
[    1.771712] ahci 0000:00:1f.2: version 3.0
[    1.771735] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.771793] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.771854] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.771858] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.771865] ahci 0000:00:1f.2: setting latency timer to 64
[    1.777784] scsi0 : ahci
[    1.777906] scsi1 : ahci
[    1.777967] scsi2 : ahci
[    1.778025] scsi3 : ahci
[    1.778147] scsi4 : ahci
[    1.778285] scsi5 : ahci
[    1.778450] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 40
[    1.778453] ata2: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06180 irq 40
[    1.778455] ata3: DUMMY
[    1.778456] ata4: DUMMY
[    1.778457] ata5: DUMMY
[    1.778458] ata6: DUMMY
[    1.857376] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.990267] hub 1-1:1.0: USB hub found
[    1.990358] hub 1-1:1.0: 6 ports detected
[    2.037267] Refined TSC clocksource calibration: 2294.790 MHz.
[    2.037280] Switching to clocksource tsc
[    2.097254] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.097304] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.099425] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633F, TM00, max UDMA/100
[    2.101234] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.101984] ata2.00: configured for UDMA/100
[    2.103465] ata1.00: ATA-8: SAMSUNG HN-M500MBB, 2AR10001, max UDMA/133
[    2.103475] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.109750] ata1.00: configured for UDMA/133
[    2.109915] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M500M 2AR1 PQ: 0 ANSI: 5
[    2.110043] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.110048] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.110095] sd 0:0:0:0: [sda] Write Protect is off
[    2.110098] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.110116] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.110803] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  TM00 PQ: 0 ANSI: 5
[    2.113698] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.113708] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.113844] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.113901] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.145121]  sda: sda1 < sda5 sda6 > sda2 sda3 sda4
[    2.145470] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.234001] hub 2-1:1.0: USB hub found
[    2.234100] hub 2-1:1.0: 6 ports detected
[    2.660955] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.646499] udev: starting version 151
[   10.647900] Adding 15999996k swap on /dev/sda5.  Priority:-1 extents:1 across:15999996k 
[   10.827776] lp: driver loaded but no devices found
[   11.034888] cfg80211: Calling CRDA to update world regulatory domain
[   11.046658] type=1400 audit(1329949877.959:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=457 comm="apparmor_parser"
[   11.047094] type=1400 audit(1329949877.959:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=457 comm="apparmor_parser"
[   11.047333] type=1400 audit(1329949877.959:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=457 comm="apparmor_parser"
[   11.090396] wmi: Mapper loaded
[   11.223711] cfg80211: World regulatory domain updated:
[   11.223713] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.223716] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.223717] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.223719] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.223721] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.223723] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.314784] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.314814] xhci_hcd 0000:04:00.0: setting latency timer to 64
[   11.314819] xhci_hcd 0000:04:00.0: xHCI Host Controller
[   11.314876] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[   11.321883] xhci_hcd 0000:04:00.0: irq 16, io mem 0xf7c00000
[   11.321946] xhci_hcd 0000:04:00.0: irq 41 for MSI/MSI-X
[   11.321950] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
[   11.321954] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[   11.321957] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[   11.321961] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[   11.322137] xHCI xhci_add_endpoint called for root hub
[   11.322140] xHCI xhci_check_bandwidth called for root hub
[   11.322171] hub 3-0:1.0: USB hub found
[   11.322181] hub 3-0:1.0: 2 ports detected
[   11.322249] xhci_hcd 0000:04:00.0: xHCI Host Controller
[   11.322278] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[   11.327123] xHCI xhci_add_endpoint called for root hub
[   11.327126] xHCI xhci_check_bandwidth called for root hub
[   11.327153] hub 4-0:1.0: USB hub found
[   11.327163] hub 4-0:1.0: 2 ports detected
[   11.434696] sdhci: Secure Digital Host Controller Interface driver
[   11.434699] sdhci: Copyright(c) Pierre Ossman
[   11.553713] jmb38x_ms 0000:02:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   11.553723] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[   11.566280] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   11.566502] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.566509] mei 0000:00:16.0: setting latency timer to 64
[   11.606770] [drm] Initialized drm 1.1.0 20060810
[   11.622667] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 80)
[   11.622691] sdhci-pci 0000:02:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   11.622739] sdhci-pci 0000:02:00.0: setting latency timer to 64
[   11.622752] mmc0: no vmmc regulator found
[   11.622788] Registered led device: mmc0::
[   11.622947] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[   11.622956] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 80)
[   11.622970] sdhci-pci 0000:02:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   11.622974] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[   11.622982] sdhci-pci 0000:02:00.2: PCI INT B disabled
[   11.635573] asus_wmi: Asus Management GUID not found
[   11.679602] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.679606] i915 0000:00:02.0: setting latency timer to 64
[   11.690021] rtl8192ce 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.690034] rtl8192ce 0000:01:00.0: setting latency timer to 64
[   11.737748] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[   11.737753] rtlwifi:rtl_pci_probe():<0-0> Can't init_sw_vars.
[   11.737780] rtl8192ce 0000:01:00.0: PCI INT A disabled
[   11.740477] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   11.740482] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.740483] [drm] Driver supports precise vblank timestamp query.
[   11.740510] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.757133] jme: JMicron JMC2XX ethernet driver version 1.0.8
[   11.757165] jme 0000:02:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.757177] jme 0000:02:00.5: setting latency timer to 64
[   11.758172] jme 0000:02:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:80:ee:73:15:f5:c3
[   11.919478] Finger Sensing Pad, hw: 13.2.1, sw: 1.0.0-K, buttons: 4
[   11.932298] fbcon: inteldrmfb (fb0) is primary device
[   12.108929] Console: switching to colour frame buffer device 170x48
[   12.111095] fb0: inteldrmfb frame buffer device
[   12.111096] drm: registered panic notifier
[   12.228012] acpi device:48: registered as cooling_device9
[   12.228189] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   12.228272] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.228372] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.228416] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.228500] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   12.228536] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.348037] input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio2/input/input6
[   12.688153] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   12.912204] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   12.912345] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.912482] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.912585] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.312972] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   13.707581] jme 0000:02:00.5: irq 48 for MSI/MSI-X
[   13.708075] jme 0000:02:00.5: eth0: Link is down
[   13.708596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.716227] type=1400 audit(1329949880.631:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=776 comm="apparmor_parser"
[   13.716623] type=1400 audit(1329949880.631:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=777 comm="apparmor_parser"
[   13.717223] type=1400 audit(1329949880.631:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=777 comm="apparmor_parser"
[   13.717563] type=1400 audit(1329949880.631:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=777 comm="apparmor_parser"
[   13.718661] type=1400 audit(1329949880.631:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=780 comm="apparmor_parser"
[   13.719253] type=1400 audit(1329949880.635:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=780 comm="apparmor_parser"
[   13.719477] type=1400 audit(1329949880.635:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=781 comm="apparmor_parser"
[   13.999517] ppdev: user-space parallel port driver
[  263.283881] ISO 9660 Extensions: Microsoft Joliet Level 3
[  264.282440] ISOFS: changing to secondary root
[  320.860815] jme 0000:02:00.5: eth0: Link is up at ANed: 1000 Mbps, Full-Duplex, MDI
[  320.862824] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  331.200756] eth0: no IPv6 routers present
[  608.762786] usb 3-1: new low speed USB device number 2 using xhci_hcd
[  608.783739] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  608.786666] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  608.787851] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
[  608.788116] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  608.850426] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
[  608.860578] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb3/3-1/3-1:1.0/input/input10
[  608.860936] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:04:00.0-1/input0
[  608.860992] usbcore: registered new interface driver usbhid
[  608.860998] usbhid: USB HID core driver
```


--------------------------------------------------------------
I've tried LinuxMint 12, with a bootable pendrive, and everything fine! =D

But... I wanted to understand the reasons why over purely Ubuntu (since LinuxMint is a Ubuntu-flavor distro) my laptop doesnt work.

---

