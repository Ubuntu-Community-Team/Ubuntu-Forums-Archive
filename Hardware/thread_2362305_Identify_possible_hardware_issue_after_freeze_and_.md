---
title: "Identify possible hardware issue after freeze and restart"
date: 2017-05-26
forum: Hardware
---

### Post by iqdesigner on 2017-05-26
Hi,
 
 I am running 16.04 Ubuntu on my laptop. At random times (it might happen several times in a week or once a month) my computer freezes (I cannot do anything, keyboard/mouse are not responding, screen is frozen). So I shutdown using the power button.
 
 How can I see any informative logs after I restart my laptop in order to identify why I get the freeze?  eg at this time this hardware device was accessed and as it was the last one, this device was the problem
 Is something like that available in Ubuntu? How can I debug hardware access via linux to get some error info?
 
Thanks

---

### Post by TheFu on 2017-05-26
Boot off a flash drive running any live-boot version of linux, mount the internal disk with /var/logs/ and look at the log files.

Do not boot from the internal disk, since that overwrites some logs, like the dmesg one.

---

### Post by iqdesigner on 2017-05-30
> **TheFu said:**
> Boot off a flash drive running any live-boot version of linux, mount the internal disk with /var/logs/ and look at the log files.

Do not boot from the internal disk, since that overwrites some logs, like the dmesg one.

Hi TheFu,

My pc crashed, and I boot from a flash drive. I mount the /var/logs but I did not found anything interesting in dmesg/log files, no errors.
Probably I need more low level information for hardware. Is something like this possible?

Thanks

---

### Post by TheFu on 2017-05-30
A locked up screen, keyboard and mouse doesn't necessarily mean the computer is locked up. It could just be the X/Server with an issue.   Can you ssh into the box from another device and do some remote troubleshooting?  That won't use X/Windows.

lshw can provide detailed info about the connected hardware.  But that just shows what it is, where it is on the bus and which driver is being used.  Enable system monitoring - push the monitoring logs to a different system live, so they aren't lost.  Cacti, munin, nagios are popular, but there are 50 others.

The issue really could be anything:
* running out of virtual memory
* bad power supply
* bad video card
* bad power connector to any device
* cracked motherboard
* failing RAM
* corrupted OS data on storage
or 50 other issues.

---

### Post by sp40140 on 2017-05-30
Random freezes can be caused by many things. Firstly, what are the hardware specs of your laptop?

---

### Post by iqdesigner on 2017-05-30
> **TheFu said:**
> A locked up screen, keyboard and mouse doesn't necessarily mean the computer is locked up. It could just be the X/Server with an issue.   Can you ssh into the box from another device and do some remote troubleshooting?  That won't use X/Windows.

lshw can provide detailed info about the connected hardware.  But that just shows what it is, where it is on the bus and which driver is being used.  Enable system monitoring - push the monitoring logs to a different system live, so they aren't lost.  Cacti, munin, nagios are popular, but there are 50 others.

The issue really could be anything:
* running out of virtual memory
* bad power supply
* bad video card
* bad power connector to any device
* cracked motherboard
* failing RAM
* corrupted OS data on storage
or 50 other issues.


   TheFu, not easy (I do not have a second laptop) but could try if I can get a connection on same hub/wifi with my mobile phone to get an ssh in case the problem is with X. From X logs I did not found something. Yes as you mentioned there might be several reasons, just trying to figure out what it is. I was expecting linux to give me some way to see details on hardware level (or it might be just ubuntu but I suspect hardware, but as it happens randomly I want to find what it is before I decide that I need a new laptop). I can install some monitoring application, but those can go such deep as I want?




> **sp40140 said:**
> Random freezes can be caused by many things. Firstly, what are the hardware specs of your laptop?

   Hi sp40140. The main question is how can I debug a crash/stall on ubuntu? (for example back when I have windows -a lot years ago- the blue screen gives a hex code and then I was able to search for it)
  For your question, a simple sudo lshw gives:

```

computer
    description: Notebook
    product: HP G62 Notebook PC (WM959EA#B1A)
    vendor: Hewlett-Packard
    version: 049D100000202710000020000
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=WM959EA#B1A uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 1426
       vendor: Hewlett-Packard
       physical id: 0
       version: 54.13
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.07
          date: 02/10/2010
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
          slot: CPU
          size: 1733MHz
          capacity: 2133MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm arat cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: 17
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
             configuration: level=3
        *-cache:1
             description: L2 cache
             physical id: 19
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
             configuration: level=2
        *-cache:2
             description: L1 cache
             physical id: 1a
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
             configuration: level=1
     *-cache
          description: L1 cache
          physical id: 18
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: AD73I1B1674EG
             vendor: A-DATA Technology
             physical id: 0
             serial: [REMOVED]
             slot: Bottom - Slot 1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: AD73I1B1674EG
             vendor: A-DATA Technology
             physical id: 1
             serial: [REMOVED]
             slot: Bottom - Slot 2
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
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
             resources: irq:24 ioport:4000(size=4096) memory:d4000000-d40fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Park [Mobility Radeon HD 5430]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:27 memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:4000(size=256) memory:d4040000-d405ffff
           *-multimedia
                description: Audio device
                product: Cedar HDMI Audio [Radeon HD 5400/6300 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:30 memory:d4020000-d4023fff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:28 memory:d4106100-d410610f
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
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d4105c00-d4105fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-78-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Mouse
                      product: USB OPTICAL MOUSE
                      vendor: Pixart Imaging, Inc.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:d4100000-d4103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:d3000000-d3ffffff ioport:d0000000(size=16777216)
           *-network DISABLED
                description: Wireless interface
                product: Centrino Wireless-N 1000 [Condor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlo1
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-78-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:31 memory:d3000000-d3001fff
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
             resources: irq:16 ioport:2000(size=4096) memory:d2000000-d2ffffff ioport:d1000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:25 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d2000000-d200ffff
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
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:d4105800-d4105bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-78-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Keyboard
                      vendor: SEM
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=98mA speed=1Mbit/s
                 *-usb:1
                      description: Video
                      product: HP Webcam-101
                      vendor: Chicony Corp.
                      physical id: 5
                      bus info: usb@2:1.5
                      version: 59.54
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=320mA speed=480Mbit/s
        *-pci:3
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
             product: HM55 Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:5048(size=8) ioport:5054(size=4) ioport:5040(size=8) ioport:5050(size=4) ioport:5020(size=32) memory:d4105000-d41057ff
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
             resources: memory:d4106000-d41060ff ioport:5000(size=32)
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
          product: 1st Generation Core i3/5/7 Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS721010A9
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A3B0
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=c4261bd3
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 927GiB
                capacity: 927GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-07-18 02:19:08 filesystem=ext4 lastmountpoint=/ modified=2017-05-31 07:23:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-05-30 22:58:37 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3957MiB
                capacity: 3957MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3957MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7701H
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 2.85
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: 13-54
       physical id: 1
       slot: Primary
       capacity: 4400mWh
       configuration: voltage=10,8V

```


Thanks

---

### Post by TheFu on 2017-05-30
If you have a core dump, you can debug it.  Skills are necessary for this. Are you a C programmer?
But if it is a PSU dying, all power is cut and **no** consumer level HW/OS will help.  It is an apples/oranges comparison.  Enterprise hardware performs self-checks constantly and would report, via the logs, the issues.  Laptops don't have this capability.

Please edit the lshw output and use 'code tags' to fix the alignment. Too hard to read as it is.

---

### Post by sp40140 on 2017-05-30
for lshw, I suggest you use it with sensitize option. 
On how to find the cause: it depends on lots of things, so you need as many details as possible. Typically you start with /var/logs and go from there. That is a very concrete step.
There are short cuts like googling the make-model of your pc and symptoms. If it's common enough, you will get hits.
Lots of these comes with experience.
For example, I see that you have HP G series laptop with first or second gen i3. As I don't like ANY consumer class laptops, my first educated guess would be that it's related to overheating. And then try to validate that assumption by checking fans / vents. When does it happen: on you lap or pillow? which limits the airflow? How does it do on flat surface with good flow.. and on and on..
Second guess would be some hardware component is going bad.
There are many things to look at, which ones to look at first... that part comes with experience and is based on symptoms.

---

### Post by TheFu on 2017-05-30
-sanitize, but it doesn't really matter much. The manpage for lshw has more info. The only things I **might** consider sensitive in there are the MAC addresses for wifi/LAN cards.  If you do anything sketchy, be certain to spoof your MAC.

All core i3 have thermal controls. It wouldn't lock up over that. It would just get slower. Intel has had thermal protection for almost 20 yrs.  I have an i3 too, BTW.  From a /proc/cpuinfo:
model name      : Intel(R) Core(TM) i3-5015U CPU @ 2.10GHz

Also, wouldn't hurt to look at the HDD SMART data.  Use **smartctl** to run some tests, then wait some time and use smartclt to look at the test results.  The most important aspects in the report is relocated sectors and pending sector relocation. I doubt this is any issue, but a disk with lots of errors __could__ be causing problems.

---

### Post by iqdesigner on 2017-05-31
Hi,

TheFu, I used to be a pretty advanced C programmer back in my days... I will check core dump info and will see. I was expecting linux to provide me all the info about hw components. If you see on my first post I just asked to see the order that devices are accessed (in any operation, io) just to see after the stall what is happening. 
sp40140, I checked var/logs nothing suspicious there. I will check the sensors again, the freeze it is happen in a common table (flat surface). I already check the temperature and everything seems normal.
Yes, I know that you go via symptoms, I remove one by one my memories, I switch them but the problem still occurs. I cannot remove anything else from my laptop (I do not think it is a hdd problem but I will check the smartctl as the TheFu suggested)
I sanitize my lshw

Thanks

---

### Post by TheFu on 2017-05-31
strace, but you have to have it enabled and running. [http://man7.org/linux/man-pages/man1/strace.1.html](http://man7.org/linux/man-pages/man1/strace.1.html)  I didn't want to suggest this to someone without the background.

[http://blog.tanelpoder.com/2013/02/21/peeking-into-linux-kernel-land-using-proc-filesystem-for-quickndirty-troubleshooting/](http://blog.tanelpoder.com/2013/02/21/peeking-into-linux-kernel-land-using-proc-filesystem-for-quickndirty-troubleshooting/)

But if all the power is gone, you won't see anything.  The fact that nothing is showing up in log files means it isn't a tiny hardware fault. Any errors are always logged;  a bad SATA cable will show up as thousands of errors in the logs - if it is possible to log.

A bad USB/SATA connection or failing controller:
```
[2677246.898501] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880424249180
[2677246.898504] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804242491c0
[2677827.016919] ata5.00: exception Emask 0x10 SAct 0x8000000 SErr 0x280100 action 0x6 frozen
[2677827.016925] ata5.00: irq_stat 0x08000000, interface fatal error
[2677827.016930] ata5: SError: { UnrecovData 10B8B BadCRC }
[2677827.016935] ata5.00: failed command: READ FPDMA QUEUED
[2677827.016943] ata5.00: cmd 60/80:d8:4b:e2:5f/00:00:a1:00:00/40 tag 27 ncq 65536 in
[2677827.016943]          res 50/00:80:4b:e2:5f/00:00:a1:00:00/40 Emask 0x10 (ATA bus error)
[2677827.016947] ata5.00: status: { DRDY }
[2677827.016952] ata5: hard resetting link

```

Try accessing a floppy drive that doesn't have a readable disc:
```
[1995245.844213] floppy0: floppy timeout called
[1995245.844219] end_request: I/O error, dev fd0, sector 0
[1995245.844223] Buffer I/O error on device fd0, logical block 0
[1995245.844225] lost page write due to I/O error on fd0
[1995261.897650] 
[1995261.897656] floppy driver state
[1995261.897659] -------------------
[1995261.897687] now=4793785464 last interrupt=4793784714 diff=750 last called h
andler=recal_interrupt [floppy]
[1995261.897690] timeout_message=floppy start
[1995261.897691] last output bytes:
[1995261.897694]  0 90 4793784713
[1995261.897697] 13 90 4793784713
[1995261.897699]  0 90 4793784713
[1995261.897701] 1a 90 4793784713
[1995261.897703]  0 90 4793784713
[1995261.897705]  3 90 4793784713

```

A CPU that is overheating ... shows up too:```

[4581869.288227] CPU1: Core temperature/speed normal
[4582021.371157] mce: [Hardware Error]: Machine check events logged
[4582169.303117] CPU1: Core temperature/speed normal
[4582169.303118] CPU5: Core temperature/speed normal
[4582171.378647] mce: [Hardware Error]: Machine check events logged
[4582469.321621] CPU5: Core temperature/speed normal
[4582469.321623] CPU1: Core temperature/speed normal
[4582621.409117] mce: [Hardware Error]: Machine check events logged
[4582767.413518] CPU0: Core temperature above threshold, cpu clock throttled (total events = 165746190)
[4582767.413520] CPU4: Core temperature above threshold, cpu clock throttled (total events = 165746747)
[4582767.414517] CPU4: Core temperature/speed normal
[4582767.414519] CPU0: Core temperature/speed normal
```  That's a 1st gen Core i7 being worked VERY hard.

Basically, the log files **have** any issues that aren't so bad as to prevent logging.  So a machine that dies won't have anything in the logs.  It isn't a peripheral. It is power or something ON the motherboard. If the kernel and non-GUI programs are still running, then it is X/Windows or GPU related.  That is common enough. Not all GUI programmers are cautious.

For example, here's a GUI program using more RAM than the system has:
```
[4544270.046731] Out of memory: Kill process 2418 (ghb) score 952 or sacrifice child

```
Rather than handling it properly, they just let the OS kill it. That's rude. It is probably an unexpected input causing this issue.  The previous version of this same program didn't have the issue and it doesn't happen all the time. Only with certain inputs and not all the time. Sometimes it will complete if the program is restarted, but usually not. The CLI version of similar tools don't crash. They complete the processing and provide the expected output.

A kernel lockup that is handled:
```
[2230455.722482] Call Trace:
[2230455.722489]  [<ffffffff81731b79>] schedule_preempt_disabled+0x29/0x70
[2230455.722491]  [<ffffffff817339b5>] __mutex_lock_slowpath+0x135/0x1b0
[2230455.722493]  [<ffffffff81733a4f>] mutex_lock+0x1f/0x2f
[2230455.722497]  [<ffffffff81200ae9>] do_blockdev_direct_IO+0x1bd9/0x28f0
[2230455.722500]  [<ffffffff810aa393>] ? find_busiest_group+0x133/0x890
[2230455.722503]  [<ffffffff81201855>] __blockdev_direct_IO+0x55/0x60
[2230455.722505]  [<ffffffff81246f70>] ? _ext4_get_block+0x190/0x190
[2230455.722507]  [<ffffffff81283b2b>] ext4_ind_direct_IO+0x16b/0x450
[2230455.722509]  [<ffffffff81246f70>] ? _ext4_get_block+0x190/0x190
[2230455.722512]  [<ffffffff81246355>] ext4_direct_IO+0x345/0x550
[2230455.722513]  [<ffffffff817311d4>] ? __schedule+0x384/0x7f0
[2230455.722516]  [<ffffffff81373f74>] ? timerqueue_del+0x24/0x70
[2230455.722519]  [<ffffffff81155e7b>] generic_file_aio_read+0x69b/0x700
[2230455.722522]  [<ffffffff81091e1a>] ? hrtimer_cancel+0x1a/0x30
[2230455.722525]  [<ffffffff810dc4c2>] ? futex_wait+0x1b2/0x290
[2230455.722528]  [<ffffffff8109b9b5>] ? check_preempt_curr+0x75/0xa0
[2230455.722531]  [<ffffffff811c1ddc>] do_sync_readv_writev+0x4c/0x80
[2230455.722533]  [<ffffffff811c32a0>] do_readv_writev+0xb0/0x220
[2230455.722535]  [<ffffffff810df08e>] ? do_futex+0xde/0x760
[2230455.722537]  [<ffffffff811c343d>] vfs_readv+0x2d/0x50
[2230455.722539]  [<ffffffff811c36e2>] SyS_preadv+0xa2/0xd0
[2230455.722541]  [<ffffffff8173dd5d>] system_call_fastpath+0x1a/0x1f
[2230455.722543] INFO: task qemu-system-x86:30181 blocked for more than 120 seco
nds.
```  So the problem is with some disk access (vfs) trying to write. It is probably related to virtualization. That machine is running 10 VMs.

If you have a core file, you can load it up and see exactly what the last place in the stack was - similar to that trace (from the dmesg logs).  More data will be available if the program crashing has debug symbols built-into it.  If it was reading or writing to a HW address, then you can find what the HW in that location is/was and swap it out. Usually there are hints, like the ext4_direct_IO() call in the trace above.

Anyway - the point that showing some of my logs is that errors are logged, if they can be logged.  Things are pretty bad if nothing is logged.

Hope this helps.

---

### Post by sp40140 on 2017-05-31
Agree with TheFu here. 
As you have two RAM chips, you can try to remove one and see how it behaves or switch places. And see if there are any changes in behavior.
I used to have HP laptop with AMD cpu, it had problems with northbridge. It would randomly shutdown and wouldn't boot. Since, it was a mobo thing, I couldn't to anything else but throw it away. Hope you are not that unlucky.
BTW, not that it justifies the issues, but you got good 7 years out of a consumer laptop. It's a good thing.

---

