---
title: "need help in pinpointing the faulty hardware"
date: 2016-08-24
forum: Hardware
---

### Post by mastablasta on 2016-08-24
my frankestein PC is acting up again. only this time i can't figure out what component is acting up. 

Situation: i updated on monday and rebooted. We played minecraft for a while and wife did some work onher website after that. Then Yesterday my wife booted and it froze two time but worked ok after that. then we tried to play minecraft and after a short while it froze. rebooting solved it for a short while until it froze again. after another reboot it froze on desktop. had to reboot again this time i dropped into one of TTY consoles, to check the logs. just as i was checkign dmesg it froze again. in console. after another reboot i received numerous beeps. couldn't count them well as kids were loud. it was 7 or 8. if ti's 8 it's the GPU  if it's 7 it's motherboard. problem was i couldn't reproduce it. the darn thing booted into desktop and worked just fine for the next 4 or 5 hours. i asked the family to do more testing today and to stress the GPU a bit. 

possible issues:
GPU - it's an old AGP one. once before it was causing freezes when i stressed it. i believe it was overheating. cleaning up the card solved the issue. it doesn't have any temp sensor it seems. however this time it froze in console (text mode). there was no stress on GPU in text mode and it doesn't appear it is overheating (not too hot on touch).

Motherboard/CPU - it caused freezing before due to overheating, once cleaned of dust all was good. i also applied new thermal paste to the CPU. i monitor the temp there (CPU motherboard), and it was normal.

computer: 
**CPU:** Celeron dual core E3300
**GPU: **ATI Radeon 9600XT 256 MB
**Motherboard:** Asrock 4CoreDual-Sata2 with latest BIOS installed
**RAM: **Crucial 2 GB DDR - clocked at 333 Mhz i belive. it is relatively new
Hard disks are also quite new. System disk is 1TB seagate baracuda

Operating system: Kubuntu 14.04

LSHW output:
```
 
computer                  
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 4CoreDual-SATA2.
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P2.20
          date: 09/22/2009
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Celeron(R) CPU        E3300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          slot: CPUSocket
          size: 2500MHz
          capacity: 2500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
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
          physical id: 10
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 6.7.10
          serial: [REMOVED]
          size: 2500MHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: PT880 Ultra/PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d0000000-dfffffff
        *-generic UNCLAIMED
             description: PIC
             product: PT894 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fea00000-feafffff memory:b0000000-cfffffff
           *-display:0
                description: VGA compatible controller
                product: RV350 [Radeon 9550/9600/X1050 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:b0000000-bfffffff ioport:e000(size=256) memory:feae0000-feaeffff memory:feac0000-feadffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350/M10 [Mobility Radeon 9600] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:c0000000-cfffffff memory:feaf0000-feafffff
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:1000(size=4096) memory:80000000-803fffff memory:fdf00000-fdffffff
        *-ide:0
             description: IDE interface
             product: VT8237/8251 Serial ATA Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) ioport:d000(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-usb:0
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:c480(size=32)
        *-usb:1
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:c800(size=32)
        *-usb:2
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:c880(size=32)
        *-usb:3
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:cc00(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:fe9ffc00-fe9ffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:c000(size=256) memory:fe9ff800-fe9ff8ff
        *-pci:2
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
     *-pci:1
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:7
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:65 memory:febfc000-febfffff
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD7500AARX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 51.0
             serial: [REMOVED]
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=b84ab84a
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 698GiB
                capacity: 698GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-03-10 18:35:31 filesystem=ext4 label=DATA lastmountpoint=/media/tatie/DATA modified=2016-08-22 07:40:51 mounted=2016-08-22 07:40:51 state=clean
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM003-1ER1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CC45
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0001b2d8
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 506GiB
                capacity: 506GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-04-27 11:06:01 filesystem=ext4 lastmountpoint=/ modified=2016-08-23 20:01:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-08-23 20:01:54 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 1
                serial: [REMOVED]
                size: 2055MiB
                capacity: 2055MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sdb3
                version: 1.0
                serial: [REMOVED]
                size: 423GiB
                capacity: 423GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-03-06 19:55:02 filesystem=ext4 label=podatki lastmountpoint=/media/tatie/podatki modified=2016-08-12 15:01:56 mounted=2016-08-12 15:01:56 state=clean
     *-scsi:2
          physical id: 6
          logical name: scsi2
          capabilities: emulated
        *-cdrom:0
             description: DVD-RAM writer
             product: CDDVDW SH-S222A
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc
```

the only thing i could find is the sound chip acting up again ( i use a workarround for this issue-->reload ALSA modules):
```
[   24.977320] type=1400 audit(1471974424.647:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=602 comm="apparmor_parser"
[   24.977330] type=1400 audit(1471974424.647:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=602 comm="apparmor_parser"
[   24.977335] type=1400 audit(1471974424.647:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=602 comm="apparmor_parser"
[   24.977848] type=1400 audit(1471974424.647:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=602 comm="apparmor_parser"
[   24.977855] type=1400 audit(1471974424.647:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=602 comm="apparmor_parser"
[   24.978104] type=1400 audit(1471974424.647:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=602 comm="apparmor_parser"
[   25.053890] hda-intel 0000:80:01.0: Using VIACOMBO position fix
[   25.053951] snd_hda_intel 0000:80:01.0: irq 65 for MSI/MSI-X
[   25.053997] snd_hda_intel 0000:80:01.0: PCI: Disallowing DAC for device
[   25.153219] hda-codec: out of range cmd 0:20:400:10ec0662
[   25.153280] SKU: Nid=0x1d sku_cfg=0x40041e01
[   25.153281] SKU: port_connectivity=0x1
[   25.153282] SKU: enable_pcbeep=0x0
[   25.153284] SKU: check_sum=0x00000004
[   25.153285] SKU: customization=0x0000001e
[   25.153286] SKU: external_amp=0x0
[   25.153287] SKU: platform_type=0x0
[   25.153289] SKU: swap=0x0
[   25.153290] SKU: override=0x1
[   25.153296] hda-intel 0000:80:01.0: spurious response 0x101:0x0, last cmd=0x20c0000
[   25.153420] autoconfig: line_outs=2 (0x16/0x15/0x0/0x0/0x0) type:line
[   25.153422]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   25.153423]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   25.153425]    mono: mono_out=0x0
[   25.153426]    dig-out=0x1e/0x0
[   25.153427]    inputs:
[   25.153429] realtek: No valid SSID, checking pincfg 0x40041e01 for NID 0x1d
[   25.153430] realtek: Enabling init ASM_ID=0x1e01 CODEC_ID=10ec0662
[   25.171742] hda_codec: formats == 0 (nid=0x9, val=0x10ec0662, ovrd=1, streams=0x10ec0662)
[   25.171749] hda_codec: cannot attach PCM stream 2 for codec #0
[   25.171787] hda-codec: out of range cmd 0:20:400:100101
[   25.177774] input: HDA VIA VT82xx Line Out Surround as /devices/pci0000:80/0000:80:01.0/sound/card0/input6
[   25.177879] input: HDA VIA VT82xx Line Out Front as /devices/pci0000:80/0000:80:01.0/sound/card0/input5
[   25.581059] init: failsafe main process (667) killed by TERM signal
[   26.955732] init: samba-ad-dc main process (861) terminated with status 1
[   27.650385] init: alsa-restore main process (1099) terminated with status 99

```


in kernel.log the only suspicious line is this one which apparently can mean motherboard is failing:
```
Aug 23 19:44:07 tatie-desktop kernel: [  441.652193] perf samples too long (2508 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

last systemlog entries before the crash again with the "perf samples too long message" (bold):
```
Aug 23 19:39:01 tatie-desktop CRON[2697]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug 23 19:41:58 tatie-desktop pulseaudio[2424]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 23 19:41:58 tatie-desktop pulseaudio[2424]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_80_01.0" card_name="alsa_card.pci-0000_80_01.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 23 19:41:58 tatie-desktop pulseaudio[2424]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 23 19:41:58 tatie-desktop pulseaudio[2424]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 23 19:42:46 tatie-desktop kernel: [  360.049123] mpu401 00:06: disabled
Aug 23 19:42:46 tatie-desktop kernel: [  360.211591] mpu401 00:06: activated
Aug 23 19:42:46 tatie-desktop kernel: [  360.246761] hda-intel 0000:80:01.0: Using VIACOMBO position fix
Aug 23 19:42:46 tatie-desktop kernel: [  360.246820] snd_hda_intel 0000:80:01.0: irq 65 for MSI/MSI-X
Aug 23 19:42:46 tatie-desktop kernel: [  360.246861] snd_hda_intel 0000:80:01.0: PCI: Disallowing DAC for device
Aug 23 19:42:46 tatie-desktop kernel: [  360.259096] SKU: Nid=0x1d sku_cfg=0x40041e01
Aug 23 19:42:46 tatie-desktop kernel: [  360.259100] SKU: port_connectivity=0x1
Aug 23 19:42:46 tatie-desktop kernel: [  360.259102] SKU: enable_pcbeep=0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259103] SKU: check_sum=0x00000004
Aug 23 19:42:46 tatie-desktop kernel: [  360.259104] SKU: customization=0x0000001e
Aug 23 19:42:46 tatie-desktop kernel: [  360.259106] SKU: external_amp=0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259109] SKU: platform_type=0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259110] SKU: swap=0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259111] SKU: override=0x1
Aug 23 19:42:46 tatie-desktop kernel: [  360.259367] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
Aug 23 19:42:46 tatie-desktop kernel: [  360.259370]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Aug 23 19:42:46 tatie-desktop kernel: [  360.259371]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
Aug 23 19:42:46 tatie-desktop kernel: [  360.259372]    mono: mono_out=0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259374]    dig-out=0x1e/0x0
Aug 23 19:42:46 tatie-desktop kernel: [  360.259375]    inputs:
Aug 23 19:42:46 tatie-desktop kernel: [  360.259377]      Mic=0x18
Aug 23 19:42:46 tatie-desktop kernel: [  360.259380]      Line=0x1a
Aug 23 19:42:46 tatie-desktop kernel: [  360.259382] realtek: No valid SSID, checking pincfg 0x40041e01 for NID 0x1d
Aug 23 19:42:46 tatie-desktop kernel: [  360.259383] realtek: Enabling init ASM_ID=0x1e01 CODEC_ID=10ec0662
Aug 23 19:42:46 tatie-desktop kernel: [  360.271034] input: HDA VIA VT82xx Line Out CLFE as /devices/pci0000:80/0000:80:01.0/sound/card0/input9
Aug 23 19:42:46 tatie-desktop kernel: [  360.272382] input: HDA VIA VT82xx Line Out Surround as /devices/pci0000:80/0000:80:01.0/sound/card0/input8
Aug 23 19:42:46 tatie-desktop kernel: [  360.272982] input: HDA VIA VT82xx Line Out Front as /devices/pci0000:80/0000:80:01.0/sound/card0/input7
Aug 23 19:42:46 tatie-desktop kernel: [  360.273230] input: HDA VIA VT82xx Line as /devices/pci0000:80/0000:80:01.0/sound/card0/input6
Aug 23 19:42:46 tatie-desktop kernel: [  360.273818] input: HDA VIA VT82xx Mic as /devices/pci0000:80/0000:80:01.0/sound/card0/input5
Aug 23 19:42:46 tatie-desktop kernel: [  360.349513] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349527] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349548] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349569] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349590] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349611] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349632] hda-intel 0000:80:01.0: spurious response 0x80000000:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349653] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349673] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop kernel: [  360.349694] hda-intel 0000:80:01.0: spurious response 0x0:0x0, last cmd=0x1639000
Aug 23 19:42:46 tatie-desktop pulseaudio[2424]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 23 19:42:46 tatie-desktop pulseaudio[2424]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 23 19:42:46 tatie-desktop rtkit-daemon[2426]: Successfully made thread 4356 of process 2424 (n/a) owned by '1000' RT at priority 5.
Aug 23 19:42:46 tatie-desktop rtkit-daemon[2426]: Supervising 2 threads of 1 processes of 1 users.
**Aug 23 19:44:07 tatie-desktop kernel: [  441.652193] perf samples too long (2508 > 2500), lowering kernel.perf_event_max_sample_rate to 50000**
Aug 23 19:47:04 tatie-desktop rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="513" x-info="http://www.rsyslog.com"] start
Aug 23 19:47:04 tatie-desktop rsyslogd: rsyslogd's groupid changed to 103
Aug 23 19:47:04 tatie-desktop rsyslogd: rsyslogd's userid changed to 101
Aug 23 19:47:04 tatie-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 23 19:47:04 tatie-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
```

---

### Post by Willyweasel on 2016-08-24
I would check the motherboard for leaking or bulging capacitors first since it's an older motherboard with electrolytic caps. If a visual inspection of the motherboard doesn't turn up anything then I would swap the power supply with a known working unit if you have one laying around that is. Then run MemTest86 for a few hours on each stick of ram individually to rule out the ram. Also try taking out the ram and gpu then use some compressed air to blow out the agp and ram slots.

---

