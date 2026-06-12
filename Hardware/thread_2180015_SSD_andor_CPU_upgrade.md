---
title: "SSD and/or CPU upgrade?"
date: 2013-10-11
forum: Hardware
---

### Post by MibunoOokami on 2013-10-11
I have an HP mini netbook which has an Intel Atom CPU. I'm wondering which would be better to achieve better performance, replacing the HDD with an SSD or just upgrading the CPU. By performance I mean, this netbook can't handle videos, be it DVDs via external DVD drive, online streaming or video files. I get sound but a still image.
Changing to SSD is rather spendy and you get less storage space, but I've read it can enhance performance. I'm guessing that the video problem is likely graphics related though and an SSD may not help. I'm not sure what to replace the CPU with but it's going to have to be similar to the Atom right? As I understand it the graphics card/controller is built into the CPU. Please correct me if I'm mistaken, The price of new CPUs doesn't look too bad, so maybe upgrading that is the way to go? Or upgrade both perhaps?
To the point, if a new CPU is the way to go, can someone please recommend what to replace it with? Thanks

---

### Post by mkmanifesto on 2013-10-11
More then likely the CPU is soldered on to the motherboard. Your only option would probably be to add an SSD and in my opinion that probably wouldn't be worth it, imo.

---

### Post by MibunoOokami on 2013-10-11
> **mkmanifesto said:**
> More then likely the CPU is soldered on to the motherboard. Your only option would probably be to add an SSD and in my opinion that probably wouldn't be worth it, imo.

Oh, that's a shame. I thought the CPU clips in.

---

### Post by mörgæs on 2013-10-11
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by MibunoOokami on 2013-10-11
> **mörgæs said:**
> Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

Here it is, thanks.

```
computer
    description: Notebook
    product: HP Mini 110-4100 (A9M23PA#ABG)
    vendor: Hewlett-Packard
    version: 0797200000204600000300100
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 family=103C_5335KV G=N L=CON B=HP S=PAV X=MIN sku=A9M23PA#ABG uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 338D
       vendor: Hewlett-Packard
       physical id: 0
       version: 37.19
       serial: [REMOVED]
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.07
          date: 11/14/2012
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: DIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: HMT325S6BFR8C-H9
             vendor: Hynix
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-Slot 1(top)
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
          vendor: Intel Corp.
          physical id: f
          bus info: cpu@0
          version: 6.6.1
          serial: [REMOVED]
          slot: CPU
          size: 600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 400MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm arat dtherm cx16 cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=4
        *-cache:0
             description: L2 cache
             physical id: 10
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.6.1
          serial: [REMOVED]
          size: 1600MHz
          capacity: 1600MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
     *-pci
          description: Host bridge
          product: Atom Processor D2xxx/N2xxx DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:84000000-840fffff ioport:40d0(size=8)
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:84100000-84103fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:83000000-83ffffff ioport:80000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 05
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:3000(size=256) memory:80004000-80004fff memory:80000000-80003fff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:82000000-82ffffff ioport:81000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-54-generic-pae firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:82000000-8207ffff memory:81000000-8100ffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:40a0(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4080(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4060(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4040(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:17 memory:84105000-841053ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: NM10/ICH7 Family SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:40c8(size=8) ioport:40dc(size=4) ioport:40c0(size=8) ioport:40d8(size=4) ioport:4020(size=16) memory:84104000-841043ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54323
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ES2O
                serial: [REMOVED]
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8c890b7d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: [REMOVED]
                   size: 197MiB
                   capacity: 199MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-12-23 08:15:19 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: [REMOVED]
                   size: 49GiB
                   capacity: 50GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-23 07:51:46 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 247GiB
                   capacity: 247GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 19GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2929MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 225GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
              *-volume:3
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: FAT32
                   serial: [REMOVED]
                   size: 78MiB
                   capacity: 103MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:4000(size=32)
  *-battery
       description: Lithium Ion Battery
       product: MT06055
       vendor: 11-85
       physical id: 1
       slot: Primary
       capacity: 55080mWh
       configuration: voltage=10.8V
```

---

### Post by mörgæs on 2013-10-12
The hard disk has fairly good performance: [http://www.chip.de/preisvergleich/101013/Datenblatt-Hitachi-Travelstar-5K320-320GB-HTS543232-L9A300.html](http://www.chip.de/preisvergleich/101013/Datenblatt-Hitachi-Travelstar-5K320-320GB-HTS543232-L9A300.html) . I don't think it matters anything changing to SSD. Have you noticed any increased activity when trying to play a film?

I believe that you should focus on software solutions.

---

### Post by Tobi_Rall on 2013-10-12
I think so too. CPU will be difficult to change, and the SSd will speed up the system, but not help very much with video encoding.

I heard that the Atom Linux driver are very poor. Especially the video part. That might be where the problem is at.

---

### Post by mkmanifesto on 2013-10-12
> **Tobi_Rall said:**
> I think so too. CPU will be difficult to change, and the SSd will speed up the system, but not help very much with video encoding.

I heard that the Atom Linux driver are very poor. Especially the video part. That might be where the problem is at.

I've owned 2 HP Mini's and even running WinXP or Win7 provided the same performance when it came to video play back. In general they are decent netbooks, but they lack performance for certain tasks.

---

### Post by MibunoOokami on 2013-10-14
> **mörgæs said:**
> The hard disk has fairly good performance: [http://www.chip.de/preisvergleich/101013/Datenblatt-Hitachi-Travelstar-5K320-320GB-HTS543232-L9A300.html](http://www.chip.de/preisvergleich/101013/Datenblatt-Hitachi-Travelstar-5K320-320GB-HTS543232-L9A300.html) . I don't think it matters anything changing to SSD. Have you noticed any increased activity when trying to play a film?

I believe that you should focus on software solutions.

I can't say that I've noticed any increased activity. I just assumed this netbook is just not powerful enough and somewhere during an online search I came across some info about SSDs and the extra boost in performance that they give since they have no moving parts.

What type of software solutions should I be looking for? I did have the additional drivers installed which controlled graphics (assuming this is graphics related) but it really slowed the netbook down.

---

### Post by MibunoOokami on 2013-10-14
> **Tobi_Rall said:**
> I think so too. CPU will be difficult to change, and the SSd will speed up the system, but not help very much with video encoding.

I heard that the Atom Linux driver are very poor. Especially the video part. That might be where the problem is at.

If I understand correctly, an SSD would make the system faster but that wouldn't do anything for playing a video? There's still so much I don't know.

> **mkmanifesto said:**
> I've owned 2 HP Mini's and even running WinXP or Win7 provided the same performance when it came to video play back. In general they are decent netbooks, but they lack performance for certain tasks.

Did you have the same video problems? If so were you able to overcome them?

---

### Post by Ranko Kohime on 2013-10-14
> **MibunoOokami said:**
> If I understand correctly, an SSD would make the system faster but that wouldn't do anything for playing a video? There's still so much I don't know.
An SSD makes programs read from the disk faster, (because generally, the CPU sits around waiting on the hard drive whenever it needs something from it)

And as far as that CPU, I'm rather surprised it can't play DVD's.  There's nothing CPU-intensive about them, and I played them successfully on a 400MHz Celeron back in the day. (1/4 the CPU speed you have)

---

### Post by mörgæs on 2013-10-14
> **MibunoOokami said:**
> 
What type of software solutions should I be looking for? 

Which versions of Buntu have you tried until now?

---

### Post by mkmanifesto on 2013-10-14
> **MibunoOokami said:**
> If I understand correctly, an SSD would make the system faster but that wouldn't do anything for playing a video? There's still so much I don't know.



Did you have the same video problems? If so were you able to overcome them?

SSD will certainly help with disk performance, but it will not help with video rendering, etc. 

Overall video performance wasn't terrible for me but it didn't work that great either. I did upgrade the memory in the ones I owned.

---

### Post by MibunoOokami on 2013-10-15
> **mörgæs said:**
> Which versions of Buntu have you tried until now?

Only U.

---

### Post by mörgæs on 2013-10-15
I mean the release numbers.

---

### Post by MibunoOokami on 2013-10-15
> **mörgæs said:**
> I mean the release numbers.

Sorry, thought you meant K, X, U etc. I've only tried 12.04 LTS.

---

### Post by mörgæs on 2013-10-15
In that case I would try Lubuntu 13.10 for comparison.

---

### Post by MibunoOokami on 2013-10-16
> **mörgæs said:**
> In that case I would try Lubuntu 13.10 for comparison.

I was trying the live version but early into the session, before I could try videos it became unresponsive. After a reboot, it gives error messages about an internal error which I forgot to write down, though I vaguely recall it having the words executable and GTK. Lost access to internet as well as the wifi and battery icons, and all the options such as reboot, shut down, suspend, hibernate etc all disappeared to. I restarted a few times and nothing changed. 
I'll try making another USB startup disk and see if that helps. Hopefully it's not related to my hardware.

---

### Post by mörgæs on 2013-10-17
You could also try to install the mini.iso first and add the desktop environment later:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by MibunoOokami on 2013-10-20
> **mörgæs said:**
> You could also try to install the mini.iso first and add the desktop environment later:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

I didn't get a chance to retry the USB start up disk over the weekend and will skip it for now and just try the mini version later tonight. Will keep you posted.

---

### Post by MibunoOokami on 2013-10-22
> **MibunoOokami said:**
> I didn't get a chance to retry the USB start up disk over the weekend and will skip it for now and just try the mini version later tonight. Will keep you posted.

I wasn't confident with following the instructions to make a USB startup disk with the mini version and I don't have my external cd drive available. As it turned out though, I had accidentally downloaded and tried 13.04 instead of 13.10, so I downloaded and installed it last night and it's not too bad, had a different internal error message this time but only the once and at least the settings which disappeared last time haven't disappeared this time. Takes a bit of getting used to not having Unity anymore, this reminds me of my very first version of Ubuntu which was 7.10 IIRC.
Getting to the original point of this thread, I was able to play some videos in the default Lubuntu media player so they should work with VLC, I'm glad I didn't have to buy any new hardware. If I encounter any problems with Lubuntu, I'll burn the mini version to a CD when I get my external drive back and test that out.

Thanks everyone for your help.

---

