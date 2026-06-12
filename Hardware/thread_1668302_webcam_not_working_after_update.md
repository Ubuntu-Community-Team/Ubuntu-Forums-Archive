---
title: "webcam not working after update"
date: 2011-01-16
forum: Hardware
---

### Post by gnomepm on 2011-01-16
Hi everyone.
I've been using Ubuntu 10.10 for a while and everything was working fine.but recently i wanted to use "Cheese" application and when I run it, it tells me that it cant find my webcam!I used Cheese before and there was no problem.Also ubuntu cannot detect my fingerprint reader.I thought maybe it has something to do with the latest update(proposed).
(I thought maybe these can help)
when I run 
```
gstreamer-properties
```
and test my video it says :
```

Error running pipeline [COLOR="Red"]'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'[/COLOR]. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]

```
and when I run
```

lsmod | grep video

```
I get 
```

uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  0 
output                  1883  1 video

```
BTW I use a thinkpad sl500c.

---

### Post by gnomepm on 2011-01-16
Just found out that the "Protector Suit for Linux" (Application and dirver for UPEK finger print reader) is not working either!

---

### Post by gnomepm on 2011-01-16
still no one?
I found something else.When I run "lsusb", I get this:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
What is wrong?!!Someone please!help me!! :shock:

---

### Post by e_torano on 2011-01-16
Is it an external or internal webcam? Can you try running cheese as root: sudo cheese

---

### Post by gnomepm on 2011-01-16
It is internal.I can not run it as root.it says :
```

cheese: ../../src/xcb_io.c:385: _XAllocID: Assertion `ret != inval_id' failed.
Aborted

```
but i dont think it is related to this problem.I think ubuntu can not recognize my device as I mentioned above.

---

### Post by gnomepm on 2011-01-16
someone help me please!!
I'm new to these forums, if this is the wrong thread to ask my question please tell me.

---

### Post by gnomepm on 2011-01-16
still no one...
something is messing with my USB devices.

---

### Post by gnomepm on 2011-01-17
I searched but I didn't find the solution.
It can't detect my webcam as I run "lshw" and there is no webcam in the list:
```
    
    description: Notebook
    product: 4414W2Y
    vendor: LENOVO
    version: ThinkPad SL500
    serial: R8CBKF0
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=0061F1BE-009F-DE81-3030-002618AFB944
  *-core
       description: Motherboard
       product: 4414W2Y
       vendor: LENOVO
       physical id: 0
       version: LENOVO 6AET59WW
       serial: 11S42W8209Z1ZGM598DEVS
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 6AET59WW (08/26/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 478
          size: 2668MHz
          capacity: 2668MHz
          width: 64 bits
          clock: 267MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
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
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
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
          physical id: 19
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
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
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:6000(size=4096) memory:f9f00000-fcffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98M [GeForce G 105M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:6c00(size=128) memory:f9fe0000-f9ffffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5c00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:5880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f9effc00-f9efffff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:48 memory:f9ef8000-f9efbfff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:fd600000-fd6fffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:1e:65:aa:35:98
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=8.24.2.12 ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:47 memory:fd6fe000-fd6fffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:7000(size=28672) memory:fd700000-fddfffff ioport:f8800000(size=7340032)
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:e000(size=4096) memory:fde00000-fdefffff ioport:f8f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth0
                version: 02
                serial: 00:26:18:af:b9:44
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:45 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:fdef0000-fdefffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:5480(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5080(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f9eff800-f9effbff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fdf00000-fdffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0d:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:16 memory:fdfff800-fdffffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:0d:00.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:fdfff400-fdfff4ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:0d:00.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:fdffec00-fdffecff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:0d:00.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:17 memory:fdffe800-fdffe8ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:5000(size=8) ioport:4c00(size=4) ioport:4880(size=8) ioport:4800(size=4) ioport:4480(size=32) memory:f9eff000-f9eff7ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 14.0
                serial: WD-WXW0E69VPX07
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b7db6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2d64f226-b5a5-480d-acb7-df7ba9ebfee4
                   size: 286GiB
                   capacity: 286GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-12-11 20:03:14 filesystem=ext4 lastmountpoint=/&#65533;aj[H3&#65533;8&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;q!&#65533;8&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;H3&#65533;A&#65533;h&#65533;&#65533;&#65533;It!&#65533;&#65533;j modified=2011-01-14 15:44:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-16 22:40:30 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RE05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by gnomepm on 2011-01-17
I've tested an external webcam and it worked fine.I know something is wrong with my USB.Please help me!!

---

### Post by gnomepm on 2011-01-17
Changed the title...maybe it helps after one day....

---

### Post by gnomepm on 2011-01-17
I know bumping a thread is not a good thing to do but I need an answer!

---

### Post by gnomepm on 2011-01-17
Fingerprint reader problem solved after completely removing UPEK software and installing Fingerprint GUI and scaning for my device (with a little hand pressure on it! It wasn't detected at first.I tried pressure with the UPEK software but I didn't have any luck that time!)

---

### Post by adrien214 on 2011-01-17
>  *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:0d:00.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:fdfff400-fdfff4ff


what about trying lspci ? It seems your webcam is on pci bus ;D So it seems the system sees the webcam, but not you : Sorry I can't help you more.. have you tried [gspca]("http://mxhaard.free.fr/") ?

---

### Post by gnomepm on 2011-01-17
> **adrien214 said:**
> what about trying lspci ? It seems your webcam is on pci bus ;D So it seems the system sees the webcam, but not you : Sorry I can't help you more.. have you tried [gspca]("http://mxhaard.free.fr/") ?

Thanks for the reply!!
I tired "lspci" but the webcam is not there either.
I will try the link you gave me.

---

