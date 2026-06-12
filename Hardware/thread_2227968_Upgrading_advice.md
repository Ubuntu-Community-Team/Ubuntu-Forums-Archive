---
title: "Upgrading advice"
date: 2014-06-05
forum: Hardware
---

### Post by LastDino on 2014-06-05
My current config:

Mobo
```
MSI+G41M-P26+(MS-7592)
Chipset:Intel G41Socket:LGA 775Form Factor:Micro ATXIntegrated Graphics:Intel GMA X4500

```

CPU:
Intel P43.0Ghz

RAM: 4GIG DDR3 ( I've one slot free)

Output of sudo lshw for people with interest.
```

 description: Desktop Computer
    product: MS-7592 (To Be Filled By O.E.M.)
    vendor: MSI
    version: 5.0
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
     configuration: boot=normal chassis=desktop family=To Be Filled By  O.E.M. sku=To Be Filled By O.E.M.  uuid=00000000-0000-0000-0000-8C89A5624227
  *-core
       description: Motherboard
       product: G41M-P26 (MS-7592)
       vendor: MSI
       physical id: 0
       version: 5.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V26.11
          date: 12/10/2012
          size: 64KiB
          capacity: 960KiB
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880  int5printscreen int9keyboard int14serial int17printer int10video acpi  usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 CPU 3.00GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 3003MHz
          capacity: 3003MHz
          width: 64 bits
          clock: 200MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe syscall nx constant_tsc pebs bts nopl pni dtes64  monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: cores=1 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:feaf8000-feafbfff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:f0000000-f01fffff ioport:f0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:feb00000-febfffff ioport:f0400000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 8c:89:a5:62:42:27
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.100 latency=0  link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:45 memory:febc0000-febfffff ioport:ec00(size=128)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:f0600000-f07fffff ioport:f0800000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:feaf7c00-feaf7fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
              resources: irq:19 ioport:d080(size=8) ioport:d000(size=4)  ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72101
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: GKAO
             serial: GTE002PAKVKV3E
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0003ad90
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 59bc15ce-9ec0-4760-9ebf-9752388e8837
                size: 285MiB
                capacity: 285MiB
                capabilities: primary journaled extended_attributes huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2014-05-13 21:43:37 filesystem=ext4  lastmountpoint=/boot modified=2014-06-02 14:12:39 mounted=2014-06-02  14:12:39 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 717GiB
                capacity: 717GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 277GiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /media/glen/Storage
                   capacity: 356GiB
                   configuration: mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 3904MiB
                   capabilities: nofs
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 19GiB
                   capabilities: bootable
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 19GiB
              *-logicalvolume:5
                   description: Linux filesystem partition
                   physical id: a
                   logical name: /dev/sda10
                   logical name: /
                   capacity: 39GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: f53e9947-65fa-47e3-a805-42ac1c92f191
                size: 22GiB
                capacity: 22GiB
                 capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2014-05-13 21:43:30 filesystem=ext4  lastmountpoint=/ modified=2014-06-02 14:12:33 mounted=2014-06-02  14:12:33 state=clean
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                version: 1.0
                serial: 079cccfe-58c1-4a11-9f2d-f68add0ba943
                size: 191GiB
                capacity: 191GiB
                 capabilities: primary journaled extended_attributes large_files  huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2014-05-13 21:43:33 filesystem=ext4  lastmountpoint=/home modified=2014-06-02 14:12:38 mounted=2014-06-02  14:12:38 state=clean
  *-battery
       description: Nickel Cadmium Battery
       product: Nikon Ultra Plus
       vendor: Nikon Battery
       physical id: 1
       version: 08/11/97
       serial: NI00123
       slot: Left side of System
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh


```
I  don't have any dedicated GPU, but that has hardly mattered to me as the  last worth mentioning game I played was FIFA2007 and NFS Most-wanted.  Though, I'm not knowledgeable in this particular area and I intend to run  my PC for VM's and as media box, if and when I do upgrade.

I was thinking along the lines of simply updating my processor as Mobo supports it according to this site.
[http://www.cpu-upgrade.com/mb-MSI/G41M-P26.html](http://www.cpu-upgrade.com/mb-MSI/G41M-P26.html)

If its just CPU, which should I pick? Do I need to put in GPU card too? If yes, which is suitable? 



Is   doing just that would be right thing to do or should I go for  fully-fledged Mobo+CPU+GPU upgrade? If it's the latter, pleas suggest  the  possible combo's which would have zero problems with Linux. I'm not made  for windows or Mac and I believe it to be true other way around as  well.

I  would also like to know about suitable PSU unit, this part is often  unintentionally neglected by me, but I would like to make a long term  good investment here. 

I wont comment on budget as it isn't decided yet, so I'm open for suggestions from low to mid level. 

Extra info: If it helps, my mobo has already done 2 back and forths to service center. It hasn't caused any issues in last 8-9 months though.
I plan to to add RAM later as I find 4Gigs to be fairly suffecient, unless I actually do start to run VMs.

Any ideas?

---

### Post by TheFu on 2014-06-05
Don't waste time with any CPU-only update for that old MB. Not worth your time.
Definitely do a "fully-fledged Mobo+CPU+GPU upgrade" - you'll be amazed at the performance boost that $350 will get you.

Pick the CPU (I like $199 Intels) as the base, then pick the MB - that will lead to RAM, and add-on cards based on the bus in the system.  PCIe or PCIx ... if you pick the right MB, then addon network cards aren't needed. With VMs, having 2-3 ethernet ports is good.  Be certain they are all GigE - not 10/100 ports.  This makes upgrading your home network from 100base-t to 1000base-t just a $15 switch, don't even need to touch the router.

I'm not in the market for any equipment today, so I can't recommend anything. Using a good [VMware HCL whitebook list]("http://www.vm-help.com/esx40i/esx40_whitebox_HCL.php#MB") is your best bet. If ESXi will run on on the MB, then you should be find with Ubuntu.  I am NOT suggesting that you install VMware anything - use KVM - but if you get hardware compatible with ESXi, the support for most Linuxen is good.

I don't game either.  Any $50 (or less) current-Gen GPU should be fine ... from Intel, AMD, or nVidia.  Avoid the older crap that is still being pushed - saw a GS-8400 at Microcenter ... the drivers available for that old card are ... old.

PSU ... if it ain't broke, I wouldn't bother.  OTOH, I like quieter PSUs and sometimes Seasonic comes on sale for $60 or less. Wouldn't buy anything over 500W - for a non-gamer, it just isn't needed.  Corsair has a good rep too for PSU. 80% efficient means less heat, which means less noise. Any higher efficiency seems like overkill to me.

If you are doing VMs, 8G min - RAM is relatively cheap.  Be certain whatever system you buy supports 16-32G of RAM.  I feel stuck on my 8G limited systems.

---

### Post by monkeybrain20122 on 2014-06-05
> 

If you are doing VMs, 8G min - RAM is relatively cheap.  Be certain whatever system you buy supports 16-32G of RAM.  I feel stuck on my 8G limited systems.

Only 4 G's here, it is quite fast (Win 7, CentOS 6.5 and OpenSuse on vbox)

---

### Post by LastDino on 2014-06-05
> **TheFu said:**
> Don't waste time with any CPU-only update for that old MB. Not worth your time.
Definitely do a "fully-fledged Mobo+CPU+GPU upgrade" - you'll be amazed at the performance boost that $350 will get you.

Pick the CPU (I like $199 Intels) as the base, then pick the MB - that will lead to RAM, and add-on cards based on the bus in the system.  PCIe or PCIx ... if you pick the right MB, then addon network cards aren't needed. With VMs, having 2-3 ethernet ports is good.  Be certain they are all GigE - not 10/100 ports.  This makes upgrading your home network from 100base-t to 1000base-t just a $15 switch, don't even need to touch the router.

I'm not in the market for any equipment today, so I can't recommend anything. Using a good [VMware HCL whitebook list]("http://www.vm-help.com/esx40i/esx40_whitebox_HCL.php#MB") is your best bet. If ESXi will run on on the MB, then you should be find with Ubuntu.  I am NOT suggesting that you install VMware anything - use KVM - but if you get hardware compatible with ESXi, the support for most Linuxen is good.

I don't game either.  Any $50 (or less) current-Gen GPU should be fine ... from Intel, AMD, or nVidia.  Avoid the older crap that is still being pushed - saw a GS-8400 at Microcenter ... the drivers available for that old card are ... old.

PSU ... if it ain't broke, I wouldn't bother.  OTOH, I like quieter PSUs and sometimes Seasonic comes on sale for $60 or less. Wouldn't buy anything over 500W - for a non-gamer, it just isn't needed.  Corsair has a good rep too for PSU. 80% efficient means less heat, which means less noise. Any higher efficiency seems like overkill to me.

If you are doing VMs, 8G min - RAM is relatively cheap.  Be certain whatever system you buy supports 16-32G of RAM.  I feel stuck on my 8G limited systems.

Thank you for being this detailed. Its good to have someone to slap you when you're tempted to make a mistake which might be regretful. 

I'll go for full upgrade, I hope you'll write back when you next time go to market :KS

---

### Post by TheFu on 2014-06-05
My systems are generally NOT desktops and do not have GPUs, monitors, keyboards, mice connected. I haven't considered audio important in years.  Why share all this .... because it sets the expectation that average users won't be interested in any system build that I do.  The last system build I did was for a dedicated XBMC box - converted to a low-power Plex server. It is old enough that the CPU/MB cannot be purchased ANYWHERE today. I've looked.

The last time I researched a new system build was a few months ago - it was for a ZFS server running BSD, not Linux. Again, it wouldn't get anything more than "power and ping" connectivity - not really useful for average users.

While it is possible to run a few VMs in 4G, RAM is so cheap that you've be wasting money on a 4G new-machine build.  RAM chips that small will not be reused when it is time to get more.  This is opinion - everyone has one.  I know that of my 5 systems here, most are limited and do not support more than 8G of RAM. It is frustrating.  Two of them have 6G and strange RAM upgrade limits - 1 is a laptop the other (inherited) is a shuttle mini-desktop.  Normal cases are nice for future upgrades.

---

### Post by oldfred on 2014-06-06
I am planning an upgrade soon. And my plan is very similar to TheFu's suggestions.
Except I used to always buy whatever video card was about $100. I am not a gamer, but wanted good video.
But from what I now read the internal video on the Intel chips (and AMD) is as good as many low end video cards. So a slightly better Intel chip may have newer internals and save the cost of a video card if not gaming.
I do tend to prefer Intel & nVidia, but usually that costs a bit more.

This only shows the Intel 4000 in the comparison. But review is mostly for gaming high end cards.
[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107-7.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107-7.html)

Review with open source video drivers. But to see real increase with video card, you have to look at nVidia or AMD with proprietary drivers and compare that to the Intel.
[http://www.phoronix.com/scan.php?page=article&item=massive_linux_gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=massive_linux_gpus&num=1)

Also I was going to update my system a couple of years ago, but bought an SSD for my current system which is very similar CoreDuo with 4GB of RAM. With SSD, I boot and load larger apps very quickly and ended up putting off new build. And system still preforms well, so it is not an absolute requirement for me to upgrade.

---

### Post by TheFu on 2014-06-06
Just looked through a Microcenter ad here - the Core i5 4670K is 4th-gen, 84W and $190!  THAT is the CPU I'd get for a general purpose, VM, desktop, box.  Microcenter is known for loss-leader CPUs hoping to get extra business in MBs and extra stuff.  Amazon and NewEg are $235, so the microcenter discount is significant.
Some [CPU comparisons.]("http://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i5-4670K+%40+3.40GHz")

The slightly faster AMD FX-8350 is 125W - a significant power/heat difference to me - and $170.  Might be good for others.

---

### Post by oldfred on 2014-06-06
Microcenter is also showing the new Devils Canyon model i5 for the same $199 price. It seems to be just a faster chip. Not sure if in inventory yet or not.
[h=1][SIZE=1][FONT=arial]Core i5-4690K 3.5GHz LGA 1150 Boxed Processor -  PREORDER
[/FONT][/SIZE][/h][SIZE=1][FONT=arial][/FONT][/SIZE]And the new Z97 motherboards are moderately priced. Not sure what brand I might select. phoronix is using a Gigabyte where before he used to have issues with them.

[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

---

### Post by Yellow Pasque on 2014-06-06
If I was buying a new CPU for a system like that, I'd go with one of the "Haswell refresh" Core i5's (the ones with L2 cache, like the 4590 or 4690).

Intel usually takes features (like Vt-d and TSX) out of K-series CPU's, so if OP is more interested in VM's and media than OC'ing for max FPS in gamez, I'd generally avoid the K-series. The "Devil's Canyon" chip that oldfred points out is a bit of an exception, as it doesn't have features cut out like other K-series.

> **TheFu said:**
> Don't waste time with any CPU-only update for that old MB. Not worth your time.

I disagree. If OP can get hands on a cheap Yorkdale chip (like Q9400 or Q500), that's a huge upgrade. Throw in another 4GB stick of RAM, and you would have a very nice rig.

---

### Post by LastDino on 2014-06-06
Those i5 CPU's do look nice enough.

Well, as far as GPU's are concerned I was looking at these two, as they are bloody cheap and probably should suffice my needs.

[http://www.flipkart.com/asus-amd-ati-radeon-hd-5450-1-gb-ddr3-graphics-card/p/itmd2ryns3pqdhjz?pid=GRCD2RYNS3PQDHJZ&icmpid=reco_bp_personalhistoryFooter_graphics_card_5](http://www.flipkart.com/asus-amd-ati-radeon-hd-5450-1-gb-ddr3-graphics-card/p/itmd2ryns3pqdhjz?pid=GRCD2RYNS3PQDHJZ&icmpid=reco_bp_personalhistoryFooter_graphics_card_5)

[http://www.flipkart.com/forsa-nvidia-gt610-2-gb-ddr3-graphics-card/p/itmdb7pm9t8jqzwy?pid=GRCDB7PM9T8JQZWY&otracker=from-search&srno=t_16&query=graphic+cards&ref=7a22e1a1-ad08-4e06-8bb8-56dd5ff718ae](http://www.flipkart.com/forsa-nvidia-gt610-2-gb-ddr3-graphics-card/p/itmdb7pm9t8jqzwy?pid=GRCDB7PM9T8JQZWY&otracker=from-search&srno=t_16&query=graphic+cards&ref=7a22e1a1-ad08-4e06-8bb8-56dd5ff718ae)

Is there anything I'm overlooking?


I tried to search online sites here for Q9400 or Q500, but I had no luck. Forget about that, I had no luck locating anything that could work on LGA775 socket. And if by chance, I had luck in locating any shop in market which still had it, I doubt it is going to come cheap as often old discontinued parts here cost more than new one (>.>). So, I understand why TheFu would suggest it would be kind of waste. 

I do intend to check on them in market though, so I would let you know if I find anything useful.

---

### Post by oldfred on 2014-06-07
I think the performance rating on both of those cards is about the same as the Intel 4600 that you get if you get the newest i5 series chip. Even with the proprietary drivers for each of them which are better than the open source drivers.

---

### Post by Yellow Pasque on 2014-06-07
^Yeah, I wouldn't purchase either of those cards without first trying the integrated graphics, as they'll probably serve you just fine.

---

### Post by LastDino on 2014-06-07
Thanks, now I know where should be my range if I do intend to add GPU. And if new i5 chip can suffice my needs, I probably wont need it.

I'll mark this as solved. To everyone who took time to contribute, thanks again ^^

---

### Post by LastDino on 2014-06-11
Update: I've managed to locate someone who is selling his old C2D E8400+default heat sink with 2 pins broken and fan for about $30. This is not a final upgrade which I intend to do when I've enough budget, but something I want to power up my current system enough for it to horse along for year or so. P4 3.0Ghz just isn't cutting anymore and I don't have enough money atm to go main-stream.

So, what I wanted to know is; if this was ok move? I've talked with person on phone, he wants to sell this to upgrade since his mobo has gone bad (some capacitor apparently)
If yes, what to check before buying? Money exchange will happen after I'm satisfied.

Are there any quick tips about things to look out for while buying? Is there any way for me to tell if the CPU has been overclocked by its owner?

---

### Post by TheFu on 2014-06-11
Found a new E8400 for $22 from Starmicro, $25 elsewhere thru [http://www.pricewatch.com](http://www.pricewatch.com) .  Broken anything - I'd walk away.
C2D CPUs have good thermal protections, so I wouldn't worry about any OC activities.

BTW, I have an E8400 running 5 VMs right now. It has been going for about 6 yrs 24/7/365.

---

### Post by LastDino on 2014-06-11
With shipping and taxes it comes at around same with difference of dollar or two. And here you need to make a Demand draft to pay off that, while product itself is good at that price, I'm afraid its for lucky Americans :/

And I sort of like to have someone physically present to scream at when things go wrong :p

---

### Post by Yellow Pasque on 2014-06-11
I assume you're referring to broken pins on the heatsink (since the CPU doesn't have pins)? That is cause for concern, but if the two good ones are opposite each other, it should be able to apply enough pressure to maintain good contact.

There's no sure way of knowing if it was OC'd, but you can test the cpu with two instances of cpuburn (just be sure to monitor temps).

---

### Post by LastDino on 2014-06-11
I've spare heat sink pins as long as it is only that plastic looking part that is broken. I have only seen the CPU pics as heat-sink and fan are coming as extra. I also suspect that he burned his mobo capacitor due to badly mounting heat-sink on CPU. I do intend to personally visit his house and check the whole thing over weekends as seller is in my town.

Thanks! Just the thing I was looking for, is there any safe line for those temps? I've only been using P4 which runs at about 47 C max in summers here, so having baseline to compare would be nice :3

Is it possible to use my old P4 heat-sink? It doesn't have copper-base though. If it is too broken, I would consider buying new one, don't think it will be more than $ 5 here.

---

### Post by Yellow Pasque on 2014-06-11
For temps, you don't want to see over 60C under extended load.

> I also suspect that he burned his mobo capacitor due to badly mounting heat-sink on CPU.
That doesn't make sense to me. A poorly mounted heat sink would result in a warm CPU.

> Is it possible to use my old P4 heat-sink?
Probably. Even the most efficient P4's (Cedar Mill cores) were rated at the 65W TDP that the E8400 is rated for, so it's not like the cooler will be insufficent.

---

### Post by LastDino on 2014-06-11
Yeah, CPU gets warm and generally capacitor row next to it has something to say about it, more than CPU itself. G41 and sort series of Mobo's were built as economy hardware and there is not enough clearance between CPU and capacitor row,  Capacitors have electrolyte inside and if received too much heat in already ambient atmosphere like where I live, they can occasionally give out.

Alright! I'll see if its just that plastic part and replace it, if its more than that then I'll probably use my old heat-sink or buy a new unit.

---

### Post by LastDino on 2014-06-15
Update: Got my hands on that processor, I ran two instances of cpuburn and it seemed to handle itself (not that I saw any out put in numbers about its performance but still, my PC did not crash).

Is there any other software/method to check on detailed capacity of the processors? Like which core is used when, cache used and frequency utilized?

---

