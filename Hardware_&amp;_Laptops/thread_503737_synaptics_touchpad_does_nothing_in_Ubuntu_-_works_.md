---
title: "synaptics touchpad does nothing in Ubuntu - works in PCLinuxOS"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2007-07-18
I recently bought a laptop, and immediately put several Linux distro's on it. Here's the thing: the touchpad doesn't come alive in any Ubuntu I try (UbuntuStudio, Kubuntu, Gutsy), but in PCLinuxOS it works out of the box. 

I tried all the help I could find in the forums, like:
Option  "CorePointer" or Option "AlwaysCore"
Option  "SHMConfig" "true" or "on"
Load  "synaptics" in the load modules-section

I even peaked at the PCLOS xorg.conf to see if they do something funky, but they have even less lines than Ubuntu:
```

          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SHMConfig"               "True"

```

I looked through /var/log/Xorg.0.log to see if anything weird was going on, but I only see "loading synaptics", "reloading synaptics" and somewhere down the bottom: "unloading module synaptics: couldn't find the hardware (looked in 17 places) (my wording, I'm on a different PC at the moment).

What can possibly be so difficult about getting a touchpad to work? And why can't any version of Ubuntu I tried get it up, whilst it's possible with as little as three lines in another distro?

---

### Post by kerry_s on 2007-07-18
try this
[http://ubuntuforums.org/showthread.php?t=502147](http://ubuntuforums.org/showthread.php?t=502147)

---

### Post by DFreeze on 2007-07-20
Yup, tried it literally just now, but nothing...

---

### Post by DFreeze on 2007-07-22
Anyone else have a clue?

---

### Post by tcoffeep on 2007-07-22
Try this for your touchpad :

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection
```

Tell me if that works. It works for me (and trust me, 'cos I don't own a  mouse :)

---

### Post by DFreeze on 2007-07-30
Sorry for the long delay, tcoffeep, but I've had a short holiday-break. I've tried your fix, copy pasted it literally into my xorg.conf, but nothing happens... Do you have any idea where the problem might be? Or anyone else for that matter...

---

### Post by tcoffeep on 2007-08-01
I'm going to assume you have a laptop, What model is it?

---

### Post by kerry_s on 2007-08-01
are you restarting X, when ever you make a change in xorg.conf, you need to restart x for it to take effect. logout and press ctrl+alt+backspace

---

### Post by DFreeze on 2007-08-01
tcoffeep, I have a CyberMaxx MAM 2070 (Medion MD 95448 ) 17" laptop, AMD Mobile Athlon 3200+ (2000 MHz). Bought it cheap, but the lack of PnP in some areas makes me want to have spent some more dough, sometimes ;)

I tried to find the make and model in my hardware listing, but couldn't find it. I've put the complete output of "sudo lshw" at the bottom, maybe one of you can find it... If Ubuntu can't see the synaptic touchpad, no wonder it can't be enabled. Still it's peculiar that PCLinuxOS does find and enable it. So it must be possible.

kerry_s, yes I do the CTRL-ALT-BACKSPACE routine after every change.

output of "sudo lshw":

```
c-maxx
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 383MB
     *-cpu
          product: Mobile AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.10
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up ts fid vid ttp cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-pcmcia
             description: CardBus bridge
             product: PCIxx21/x515 Cardbus Controller
             vendor: Texas Instruments
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: OHCI Compliant IEEE 1394 Host Controller
             vendor: Texas Instruments
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=3 module=ohci1394
        *-storage
             description: Mass storage controller
             product: PCIxx21 Integrated FlashMedia Controller
             vendor: Texas Instruments
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-system
             description: Generic system peripheral
             product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
             vendor: Texas Instruments
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7 module=sdhci
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: W89C33D 802.11 a/b/g BB/MAC
             vendor: Winbond Electronics Corp
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0 maxlatency=32 mingnt=64
        *-network:1
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 10
             serial: 00:40:d0:76:47:1f
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.7 latency=128 maxlatency=64 mingnt=32 module=r8169 multicast=yes
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=128 maxlatency=32 mingnt=16 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: High Definition Audio/AC'97 Host Controller
             vendor: ALi Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=128 maxlatency=80 mingnt=16 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: PCI to LPC Controller
             vendor: ALi Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=64 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=192 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: ST9100823A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 93GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: MATSHITADVD-RAM UJ-840S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
c-maxx
    description: Portable Computer
    product: MAM 2070
    vendor: Notebook
    version: 5a
    serial: 12345678
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=portable power-on_password=disabled uuid=00000000-0000-0000-0000-0040D076471F
  *-core
       description: Motherboard
       product: MAM 2070
       vendor: Notebook
       physical id: 0
       version: 5a
       serial: 12345678
     *-firmware
          description: BIOS
          vendor: Insyde Software Corporation
          physical id: 0
          version: M1.04 (07/15/2005)
          size: 84KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot socketedrom edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot smartbattery netboot
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.10
          serial: Processor Serial Number
          slot: mPGA478
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up ts fid vid ttp cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst pipeline-burst external write-back
     *-memory:0
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          capacity: 256MB
        *-bank:0
             description: DIMM DDR EDO 166 MHz (6.0 ns)
             physical id: 0
             slot: DRAM Slot 0
             size: 256MB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:1
             description: DIMM DDR EDO 166 MHz (6.0 ns)
             physical id: 1
             slot: DRAM Slot 1
             size: 256MB
             width: 64 bits
             clock: 166MHz (6.0ns)
     *-memory:1 UNCLAIMED
          description: Video Memory
          physical id: 18
          slot: System board or motherboard
          capacity: 2MB
     *-memory:2 UNCLAIMED
          description: Flash Memory
          physical id: 19
          slot: System board or motherboard
          capacity: 2MB
     *-memory:3 UNCLAIMED
          description: Cache Memory
          physical id: 1a
          slot: System board or motherboard
          capacity: 256KB
     *-memory:4 UNCLAIMED
          physical id: 1
     *-memory:5 UNCLAIMED
          physical id: 2
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-pcmcia
             description: CardBus bridge
             product: PCIxx21/x515 Cardbus Controller
             vendor: Texas Instruments
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-firewire
             description: FireWire (IEEE 1394)
             product: OHCI Compliant IEEE 1394 Host Controller
             vendor: Texas Instruments
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=3 module=ohci1394
        *-storage
             description: Mass storage controller
             product: PCIxx21 Integrated FlashMedia Controller
             vendor: Texas Instruments
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-system
             description: Generic system peripheral
             product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
             vendor: Texas Instruments
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7 module=sdhci
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: W89C33D 802.11 a/b/g BB/MAC
             vendor: Winbond Electronics Corp
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=32 mingnt=64
        *-network:1
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 10
             serial: 00:40:d0:76:47:1f
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.7 latency=128 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=128 maxlatency=32 mingnt=16 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: High Definition Audio/AC'97 Host Controller
             vendor: ALi Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=128 maxlatency=80 mingnt=16 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: PCI to LPC Controller
             vendor: ALi Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=64 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=192 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: ST9100823A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.02
                   serial: 3LG0RGSB
                   size: 93GB
                   capacity: 93GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10000MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 83GB
                      capacity: 83GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux filesystem partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 9993MB
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 1427MB
                         capabilities: nofs
                    *-logicalvolume:2
                         description: W95 FAT32 partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 37GB
                    *-logicalvolume:3
                         description: Linux filesystem partition
                         physical id: 8
                         logical name: /dev/hda8
                         capacity: 9538MB
                    *-logicalvolume:4
                         description: Linux filesystem partition
                         physical id: 9
                         logical name: /dev/hda9
                         capacity: 9538MB
                    *-logicalvolume:5
                         description: Linux filesystem partition
                         physical id: a
                         logical name: /dev/hda10
                         capacity: 9538MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: MATSHITADVD-RAM UJ-840S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.50
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-battery
       product: DR36
       vendor: Duracell
       physical id: 1
       version: 01/06/97
       serial: 0042
       slot: Smart Battery Conn J37
       configuration: voltage=0.0V
```

::EDIT::

I just booted into PCLinuxOS to see how they find and describe the touchpad, and this is what I see in HardDrake:
```

Connection
Bus: &#8206;isa
Manufacturer-ID: &#8206;0x0002
Device-ID: &#8206;0x0007
Sub-manufacturer-ID: &#8206;0x0000
Sub-device-ID: &#8206;0x0000

Options
emulated wheel: &#8206;No

Div.
Manufacturer: &#8206;
Description: &#8206;SynPS/2 Synaptics TouchPad
Module: &#8206;mouse0

```

I've translated the wordings from Dutch to English, so some terminology might be off.

---

### Post by tcoffeep on 2007-08-02
I'm stumped. I tried looking at the LaptopTestingTeam listings : [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

But unfortunately, it seems your model has never been tested. My most sincere apologies that I have not helped you much.

---

### Post by kerry_s on 2007-08-02
my guess is it's ubuntu's kernel, i had alot of mice stop working with recent kernels.
what kernel is pclinuxos using? i'm thinking 2.6.18, thats what i'm using in debian & everything just works.

---

### Post by ugm6hr on 2007-08-02
Some commands that might offer you hope:
```
cat /proc/bus/input/devices
dmesg | grep Synaptics
```

Maybe post the ouput of these commands, and also the whole of your xorg.conf to see if there is anything that stares us in the face.  Sometimes a fresh set of eyes is all that is required.

---

### Post by DFreeze on 2007-08-03
ugm6hr, thanks for giving me some more ways to troubleshoot. I've executed the commands you suggested. Here's the outcome:

```

goswin@c-maxx:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=event5 
B: EV=21
B: SW=1

I: Bus=0003 Vendor=1241 Product=1177 Version=0110
N: Name="HID 1241:1177"
P: Phys=usb-0000:00:1c.1-3/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

The dmesg didn't contain anything with "Synaptics" or "synaptics" in it, so I'll post the whole of dmesg here:

```
[    0.000000] Linux version 2.6.22-9-generic (buildd@rothera) (gcc version 4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Wed Aug 1 17:31:10 GMT 2007 (Ubuntu 2.6.22-9.21-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017fef000 (usable)
[    0.000000]  BIOS-e820: 0000000017ff0000 - 0000000017ffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017ffffc0 - 0000000018000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98287) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98287
[    0.000000]   HighMem     98287 ->    98287
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98287
[    0.000000] On node 0 totalpages: 98287
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 735 pages used for memmap
[    0.000000]   Normal zone: 93456 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 17FFC340, 0030 (r1 INSYDE FACP_000      100 0000    10200)
[    0.000000] ACPI: FACP 17FFFAC0, 0074 (r1 INSYDE FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 17FFC380, 3736 (r1 INSYDE ATIRS480     1000 INTL 20040116)
[    0.000000] ACPI: FACS 17FFFFC0, 0040
[    0.000000] ACPI: APIC 17FFFB50, 0068 (r1 INSYDE APIC_000 30303030 0000    10200)
[    0.000000] ACPI: HPET 17FFFBC0, 0038 (r1 INSYDE HPET_000 30303030 0000 30303030)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7f80000)
[    0.000000] Built 1 zonelists.  Total pages: 97520
[    0.000000] Kernel command line: root=UUID=536e9360-11f9-4f38-9289-90cfc74887e5 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2000.164 MHz processor.
[   15.339650] Console: colour VGA+ 80x25
[   15.340021] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.340304] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.348549] Memory: 378516k/393148k available (2010k kernel code, 14100k reserved, 917k data, 364k init, 0k highmem)
[   15.348559] virtual kernel memory layout:
[   15.348560]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.348562]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.348563]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   15.348564]     lowmem  : 0xc0000000 - 0xd7fef000   ( 383 MB)
[   15.348565]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[   15.348566]       .data : 0xc02f6806 - 0xc03dbe64   ( 917 kB)
[   15.348568]       .text : 0xc0100000 - 0xc02f6806   (2010 kB)
[   15.348571] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.348606] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.428482] Calibrating delay using timer specific routine.. 4004.14 BogoMIPS (lpj=8008298)
[   15.428506] Security Framework v1.0.0 initialized
[   15.428513] SELinux:  Disabled at boot.
[   15.428525] Mount-cache hash table entries: 512
[   15.428643] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   15.428651] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.428653] CPU: L2 Cache: 1024K (64 bytes/line)
[   15.428656] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   15.428665] Compat vDSO mapped to ffffe000.
[   15.428676] Checking 'hlt' instruction... OK.
[   15.444574] SMP alternatives: switching to UP code
[   15.444719] Freeing SMP alternatives: 11k freed
[   15.444975] Early unpacking initramfs... done
[   15.724126] ACPI: Core revision 20070126
[   15.724185] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.729282] CPU0: AMD Mobile AMD Athlon(tm) 64 Processor 3200+ stepping 0a
[   15.729300] Total of 1 processors activated (4004.14 BogoMIPS).
[   15.729867] ENABLING IO-APIC IRQs
[   15.730122] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.875698] Brought up 1 CPUs
[   15.875788] Booting paravirtualized kernel on bare hardware
[   15.875859] Time: 22:26:43  Date: 07/03/107
[   15.875878] NET: Registered protocol family 16
[   15.875951] EISA bus registered
[   15.875964] ACPI: bus type pci registered
[   15.876308] PCI: PCI BIOS revision 2.10 entry at 0xea064, last bus=2
[   15.876310] PCI: Using configuration type 1
[   15.876313] Setting up standard PCI resources
[   15.891034] ACPI: EC: Look up EC in DSDT
[   15.891558] ACPI: EC: GPE=0x03, ports=0x66, 0x62
[   15.895983] ACPI: Interpreter enabled
[   15.895986] ACPI: (supports S0 S3 S4 S5)
[   15.895999] ACPI: Using IOAPIC for interrupt routing
[   15.899762] ACPI: EC: GPE=0x03, ports=0x66, 0x62
[   15.899799] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.899806] PCI: Probing PCI hardware (bus 00)
[   15.900675] PCI quirk: region 1000-103f claimed by ali7101 ACPI
[   15.900940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.901021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GFX_._PRT]
[   15.901103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[   15.910503] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   15.910598] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[   15.910690] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   15.910780] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[   15.910871] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 14 15)
[   15.910960] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   15.911052] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 14 15)
[   15.911142] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   15.911235] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 *11 14 15)
[   15.911314] ACPI: Power Resource [PUT2] (on)
[   15.911320] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.911327] pnp: PnP ACPI init
[   15.911333] ACPI: bus type pnp registered
[   15.912949] pnp: PnP ACPI: found 10 devices
[   15.912951] ACPI: ACPI bus type pnp unregistered
[   15.912955] PnPBIOS: Disabled by ACPI PNP
[   15.912993] PCI: Using ACPI for IRQ routing
[   15.912996] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.913038] PCI: Cannot allocate resource region 0 of device 0000:00:11.0
[   15.913074] PCI: Cannot allocate resource region 1 of device 0000:00:11.0
[   15.913107] PCI: Cannot allocate resource region 2 of device 0000:00:11.0
[   15.919049] NET: Registered protocol family 8
[   15.919051] NET: Registered protocol family 20
[   15.919098] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[   15.919101] pnp: 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[   15.919104] pnp: 00:05: iomem range 0xd0000-0xdefff has been reserved
[   15.919107] pnp: 00:05: iomem range 0xe0000000-0xe0ffffff has been reserved
[   15.919111] pnp: 00:07: ioport range 0x480-0x48f has been reserved
[   15.919114] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[   15.919116] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   15.919119] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[   15.919122] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[   15.919586] Time: tsc clocksource has been installed.
[   15.949317] PCI: Bridge: 0000:00:01.0
[   15.949320]   IO window: c000-dfff
[   15.949323]   MEM window: c0000000-cfffffff
[   15.949325]   PREFETCH window: 90000000-9fffffff
[   15.949328] PCI: Bus 3, cardbus bridge: 0000:00:10.0
[   15.949330]   IO window: 00001800-000018ff
[   15.949335]   IO window: 00001c00-00001cff
[   15.949340]   PREFETCH window: 20000000-23ffffff
[   15.949345]   MEM window: 24000000-27ffffff
[   15.949350] PCI: Bridge: 0000:00:19.0
[   15.949353]   IO window: a000-bfff
[   15.949358]   MEM window: b8000000-bfffffff
[   15.949362]   PREFETCH window: 88000000-8fffffff
[   15.949385] PCI: Enabling device 0000:00:10.0 (0000 -> 0003)
[   15.949392] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.949410] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   15.949422] NET: Registered protocol family 2
[   15.987502] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.987549] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   15.987787] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   15.987951] TCP: Hash tables configured (established 16384 bind 16384)
[   15.987954] TCP reno registered
[   15.999549] checking if image is initramfs... it is
[   16.450611] Switched to high resolution mode on CPU 0
[   16.548295] Freeing initrd memory: 6757k freed
[   16.548686] audit: initializing netlink socket (disabled)
[   16.548700] audit(1186180002.968:1): initialized
[   16.550132] VFS: Disk quotas dquot_6.5.1
[   16.550169] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.550246] io scheduler noop registered
[   16.550248] io scheduler anticipatory registered
[   16.550250] io scheduler deadline registered
[   16.550261] io scheduler cfq registered (default)
[   16.550268] PCI: MSI quirk detected. MSI deactivated.
[   16.618265] Boot video device is 0000:01:05.0
[   16.618422] isapnp: Scanning for PnP cards...
[   16.972557] isapnp: No Plug & Play device found
[   16.990719] Real Time Clock Driver v1.12ac
[   16.990802] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.991610] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.991808] input: Macintosh mouse button emulation as /class/input/input0
[   16.991869] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.756390] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.756489] mice: PS/2 mouse device common for all mice
[   17.756580] EISA: Probing bus 0 at eisa.0
[   17.756590] Cannot allocate resource for EISA slot 1
[   17.756593] Cannot allocate resource for EISA slot 2
[   17.756624] EISA: Detected 0 cards.
[   17.756720] TCP cubic registered
[   17.756734] NET: Registered protocol family 1
[   17.756755] Using IPI No-Shortcut mode
[   17.756935]   Magic number: 3:944:450
[   17.757567] Freeing unused kernel memory: 364k freed
[   17.827992] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.913838] Capability LSM initialized
[   18.919474] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.919479] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.278242] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 19 (level, low) -> IRQ 17
[   19.328004] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.374249] r8169 Gigabit Ethernet driver 2.2LK loaded
[   19.374284] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 18
[   19.374476] eth0: RTL8169sb/8110sb at 0xd8826300, 00:40:d0:76:47:1f, IRQ 18
[   19.435147] usbcore: registered new interface driver usbfs
[   19.435169] usbcore: registered new interface driver hub
[   19.435188] usbcore: registered new device driver usb
[   19.435697] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.435732] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 19
[   19.435747] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[   19.435911] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 1
[   19.435932] ohci_hcd 0000:00:1c.0: irq 19, io mem 0xf8002000
[   19.510727] usb usb1: configuration #1 chosen from 1 choice
[   19.510753] hub 1-0:1.0: USB hub found
[   19.510765] hub 1-0:1.0: 3 ports detected
[   19.567361] SCSI subsystem initialized
[   19.571289] libata version 2.21 loaded.
[   19.612764] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 18 (level, low) -> IRQ 20
[   19.612782] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[   19.612885] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 2
[   19.612906] ohci_hcd 0000:00:1c.1: irq 20, io mem 0xf8003000
[   19.670405] usb usb2: configuration #1 chosen from 1 choice
[   19.670425] hub 2-0:1.0: USB hub found
[   19.670433] hub 2-0:1.0: 3 ports detected
[    4.228000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.232000] Time: acpi_pm clocksource has been installed.
[    4.328000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 20 (level, low) -> IRQ 19
[    4.328000] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[    4.328000] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 3
[    4.328000] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xf8004000
[    4.384000] usb usb3: configuration #1 chosen from 1 choice
[    4.384000] hub 3-0:1.0: USB hub found
[    4.384000] hub 3-0:1.0: 3 ports detected
[    4.488000] PCI: Enabling device 0000:00:1c.3 (0000 -> 0002)
[    4.488000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 21
[    4.488000] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[    4.488000] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 4
[    4.488000] ehci_hcd 0000:00:1c.3: debug port 1
[    4.512000] ehci_hcd 0000:00:1c.3: irq 21, io mem 0x28021200
[    4.512000] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.512000] usb usb4: configuration #1 chosen from 1 choice
[    4.512000] hub 4-0:1.0: USB hub found
[    4.512000] hub 4-0:1.0: 8 ports detected
[    4.620000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.620000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.620000] ALI15X3: IDE controller at PCI slot 0000:00:1f.0
[    4.620000] ACPI: PCI Interrupt 0000:00:1f.0[A] -> GSI 21 (level, low) -> IRQ 22
[    4.620000] ALI15X3: chipset revision 199
[    4.620000] ALI15X3: not 100% native mode: will probe irqs later
[    4.620000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[    4.620000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[    4.620000] Probing IDE interface ide0...
[    4.908000] hda: ST9100823A, ATA DISK drive
[    5.152000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d001002d964f]
[    5.192000] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    5.448000] usb 3-1: configuration #1 chosen from 1 choice
[    5.580000] hda: selected mode 0x45
[    5.580000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.580000] Probing IDE interface ide1...
[    6.320000] hdc: MATSHITADVD-RAM UJ-840S, ATAPI CD/DVD-ROM drive
[    6.656000] hdc: selected mode 0x42
[    6.656000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.660000] hda: max request size: 512KiB
[    6.668000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.668000] hda: cache flushes supported
[    6.668000]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 hda10 >
[    6.784000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.784000] Uniform CD-ROM driver Revision: 3.20
[    7.244000] Attempting manual resume
[    7.244000] swsusp: Resume From Partition 3:6
[    7.244000] PM: Checking swsusp image.
[    7.244000] PM: Resume from disk failed.
[    7.280000] kjournald starting.  Commit interval 5 seconds
[    7.280000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.236000] r8169: eth0: link up
[   19.488000] NET: Registered protocol family 10
[   19.488000] lo: Disabled Privacy Extensions
[   19.624000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.652000] ACPI: PCI Interrupt 0000:00:10.3[A] -> GSI 17 (level, low) -> IRQ 16
[   19.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.720000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.764000] sdhci: Secure Digital Host Controller Interface driver
[   19.764000] sdhci: Copyright(c) Pierre Ossman
[   19.764000] sdhci: SDHCI controller found at 0000:00:10.4 [104c:8034] (rev 0)
[   19.764000] ACPI: PCI Interrupt 0000:00:10.4[A] -> GSI 17 (level, low) -> IRQ 16
[   19.764000] mmc0: SDHCI at 0xd000a000 irq 16 DMA
[   19.768000] mmc1: SDHCI at 0xd000a100 irq 16 DMA
[   19.768000] mmc2: SDHCI at 0xd000a200 irq 16 DMA
[   19.864000] Yenta: CardBus bridge found at 0000:00:10.0 [1071:8317]
[   19.864000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.864000] Yenta: Routing CardBus interrupts to PCI
[   19.864000] Yenta TI: socket 0000:00:10.0, mfunc 0x01ac1b22, devctl 0x66
[   20.096000] Yenta: ISA IRQ mask 0x0cf0, PCI irq 16
[   20.096000] Socket status: 30000006
[   20.508000] input: PC Speaker as /class/input/input2
[   20.560000] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   20.560000] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[   20.564000] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   20.564000] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[   20.648000] Bluetooth: Core ver 2.11
[   20.648000] NET: Registered protocol family 31
[   20.648000] Bluetooth: HCI device and connection manager initialized
[   20.648000] Bluetooth: HCI socket layer initialized
[   20.700000] Bluetooth: HCI USB driver ver 2.9
[   20.844000] usbcore: registered new interface driver hci_usb
[   21.000000] cs: IO port probe 0x100-0x3af: excluding 0x2f8-0x2ff
[   21.000000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.004000] cs: IO port probe 0x820-0x8ff: clean.
[   21.004000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.008000] cs: IO port probe 0xa00-0xaff: clean.
[   21.096000] ACPI: PCI Interrupt 0000:00:1d.0[C] -> GSI 22 (level, low) -> IRQ 23
[   21.284000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   22.232000] lp: driver loaded but no devices found
[   22.308000] Adding 1461872k swap on /dev/disk/by-uuid/8908c3f9-4308-4f65-b314-a885de913bc9.  Priority:-1 extents:1 across:1461872k
[   24.988000] EXT3 FS on hda10, internal journal
[   29.376000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   29.448000] NTFS volume version 3.1.
[   29.472000] kjournald starting.  Commit interval 5 seconds
[   29.472000] EXT3 FS on hda5, internal journal
[   29.472000] EXT3-fs: mounted filesystem with ordered data mode.
[   29.560000] eth0: no IPv6 routers present
[   29.608000] kjournald starting.  Commit interval 5 seconds
[   29.608000] EXT3 FS on hda8, internal journal
[   29.608000] EXT3-fs: mounted filesystem with ordered data mode.
[   29.624000] kjournald starting.  Commit interval 5 seconds
[   29.624000] EXT3 FS on hda9, internal journal
[   29.624000] EXT3-fs: mounted filesystem with ordered data mode.
[   31.772000] input: Power Button (FF) as /class/input/input3
[   31.776000] ACPI: Power Button (FF) [PWRF]
[   31.804000] input: Sleep Button (CM) as /class/input/input4
[   31.808000] ACPI: Sleep Button (CM) [SBTN]
[   31.836000] input: Lid Switch as /class/input/input5
[   31.840000] ACPI: Lid Switch [LID]
[   31.876000] No dock devices found.
[   31.896000] ACPI: Battery Slot [BAT0] (battery present)
[   32.076000] ACPI: AC Adapter [AC] (off-line)
[   32.364000] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   32.364000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   32.364000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   32.364000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0xe
[   32.364000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   38.288000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   38.292000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[   38.292000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   38.320000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   41.148000] [fglrx] total      GART = 130023424
[   41.148000] [fglrx] free       GART = 114032640
[   41.148000] [fglrx] max single GART = 114032640
[   41.148000] [fglrx] total      LFB  = 134217728
[   41.148000] [fglrx] free       LFB  = 116002816
[   41.148000] [fglrx] max single LFB  = 116002816
[   41.148000] [fglrx] total      Inv  = 0
[   41.148000] [fglrx] free       Inv  = 0
[   41.148000] [fglrx] max single Inv  = 0
[   41.148000] [fglrx] total      TIM  = 0
[   43.112000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.112000] apm: overridden by ACPI.
[   43.320000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   43.432000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   43.432000] NFSD: starting 90-second grace period
[   44.496000] Clocksource tsc unstable (delta = -300019510 ns)
[   46.120000] Bluetooth: L2CAP ver 2.8
[   46.120000] Bluetooth: L2CAP socket layer initialized
[   46.280000] Bluetooth: RFCOMM socket layer initialized
[   46.280000] Bluetooth: RFCOMM TTY layer initialized
[   46.280000] Bluetooth: RFCOMM ver 1.8
[  139.040000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[  139.308000] usb 2-3: configuration #1 chosen from 1 choice
[  139.504000] usbcore: registered new interface driver hiddev
[  139.548000] input: HID 1241:1177 as /class/input/input6
[  139.548000] input: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1c.1-3
[  139.548000] usbcore: registered new interface driver usbhid
[  139.548000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

```

And finally the xorg.conf listing you requested:

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

# Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"CorePointer"  
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"RTCornerButton"	"0"
#	Option		"RBCornerButton"	"2"
#	Option		"LTCornerButton"	"0"
#	Option		"LBCornerButton"	"0"
#	Option		"AccelFactor"	        "0.05"
#	Option		"LockedDrags"	        "true"	       
#	Option		"HorizScrollDelta"	"0"
#       Option 		"SHMConfig"             "on"
# EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"	
#        Option          "AccelMethod" "XAA"
#        Option          "AccelDFS"    "1"
#        Option          "GARTSize" "64"
#        Option          "EnablePageFlip" "1"
#        Option          "ColorTiling" "1"
#        Option          "AGPMode" "4"
#        Option          "AGPFastWrite" "1"
EndSection

Section "Monitor"
	Identifier	"Generieke beeldscherm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generieke beeldscherm"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen	 	"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
#	Load		"synaptics"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

As you can see, I've tried several options in my xorg.conf already (previous attempts commented out), but none were successful so far. I hope you or anyone can find a lead as to where to look for the fix... In any case: thanks for trying!

---

### Post by ugm6hr on 2007-08-03
Hmm... the absence of any mention of the Touchpad in *cat /proc/bus/input/devices* is a bit worrying - it should include an entry like this:
> I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003


It suggests that the computer is not even registering the presence of the touchpad.

And I can't see any major flaws with the various attempts at xorg edits (except that I think you can only have 1 "CorePointer" - so if the Touchpad is CorePointer, the Mouse can't be - although that doesn't really explain it).

In case you've not tried these:
Boot with no mouse plugged in;
Boot from LiveCD with / without mouse plugged in.

Hopefully someone else will have an answer for you.

---

### Post by DFreeze on 2007-08-07
Could it be that both mice (the synaptics touchpad and the USB mouse I'm using at the moment) are detected as 'mouse'? I see two 'mouse' instances in /proc/bus/input/devices: 

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```


```

I: Bus=0003 Vendor=1241 Product=1177 Version=0110
N: Name="HID 1241:1177"
P: Phys=usb-0000:00:1c.1-3/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

---

