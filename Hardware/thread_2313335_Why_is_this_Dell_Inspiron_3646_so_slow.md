---
title: "Why is this Dell Inspiron 3646 so slow?"
date: 2016-02-11
forum: Hardware
---

### Post by tahitiwibble on 2016-02-11
Hello to all,

Hope everything's well.

I've been trying to live with this Dell Inspiron 3646 for a year now and it just gets more annoying as time goes by. It's the slowest pile of junk I ever had. When I bought the thing it had W8 pre-installed (since been updated to W10) and I immediately set up dual boot with our much loved 14.04 LTS. I was thinking that the computer would be at least as good as my trusty 7 year old Asus laptop ......... WRONG! Sooooooooooooooo friggin slow it's painful, sometimes minutes goes by while waiting for windows to open, programs to start etc etc. It's buggy as hell and most of the time I have to boot in Ubuntu recovery mode to bypass the normal sequence.

Is this normal? Is there anything I could try to improve things?

I am very grateful for any help you guys may afford me.

Thanks and all the best,

Martin

The specs;

```
dad@dad-Inspiron-3646:~$ sudo lshw
[sudo] password for dad: 
dad-inspiron-3646         
    description: Desktop Computer
    product: Inspiron 3646 (xxx123x#ABA)
    vendor: Dell Inc.
    version: A04
    serial: C5NB822
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=103C_5335KV sku=xxx123x#ABA uuid=44454C4C-3500-104E-8042-C3C04F383232
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A04
          date: 08/20/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-board UNCLAIMED
          description: Motherboard
          product: 0V6D8J
          vendor: Dell Inc.
          physical id: 2
          version: A00
          serial: .C5NB822.CN701634AG00UW.
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU  J2900  @ 2.41GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU  J2900  @ 2.41GHz
          slot: CPU 1
          size: 1577MHz
          capacity: 2656MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1 Cache
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M471B5173DB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 17E50CBB
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: ValleyView SSA-CUnit
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: ValleyView Gen7
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:106 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
        *-storage
             description: SATA controller
             product: ValleyView 6-Port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:104 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:90914000-909147ff
        *-usb
             description: USB controller
             product: ValleyView USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:103 memory:90900000-9090ffff
        *-generic UNCLAIMED
             description: Encryption controller
             product: ValleyView SEC
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:90800000-908fffff memory:90700000-907fffff
        *-multimedia
             description: Audio device
             product: ValleyView High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:107 memory:90910000-90913fff
        *-pci:0
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:90600000-906fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 4c:bb:58:14:fe:a8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-77-generic firmware=N/A ip=192.168.1.43 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:90600000-9067ffff memory:90680000-9068ffff
        *-pci:2
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:90500000-905fffff ioport:90400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: b0:83:fe:72:3e:e0
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:105 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff
        *-isa
             description: ISA bridge
             product: ValleyView Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: ValleyView SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:90915000-9091501f ioport:2000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKX-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 20.0
             serial: WD-WCC2EHAT3N4X
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c6cd5a82-5640-4875-9a16-6dbc6ce5b05d sectorsize=512
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: 562c-863d
                size: 495MiB
                capacity: 499MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: 2c87-e300
                size: 15MiB
                capacity: 39MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat name=Basic data partition
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: cb3c18dc-7080-47ff-8a39-0c1b3ee69865
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 1c89-840e
                size: 720MiB
                capacity: 749MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 10:10:20 filesystem=ntfs label=WINRETOOLS modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 48e2e9d1-54bc-674b-980d-2b21f2742f00
                size: 123GiB
                capacity: 123GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 10:10:27 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: 127e-72f9
                size: 424MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-11-13 06:15:20 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: b7ad76d4-bb58-482d-9930-2ce1a0914ba3
                size: 18GiB
                capacity: 18GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-02-16 20:12:27 filesystem=ext4 lastmountpoint=/ modified=2016-02-11 09:11:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-02-11 09:11:26 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: 38bb7c1a-acdb-4967-b666-187b7664adcb
                size: 7627MiB
                capacity: 7628MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:8
                description: EXT4 volume
                vendor: Linux
                physical id: 9
                bus info: scsi@0:0.0.0,9
                logical name: /dev/sda9
                logical name: /home
                version: 1.0
                serial: 1a65b39e-19b6-49d3-8657-6037ea2ef906
                size: 306GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-02-16 20:12:29 filesystem=ext4 lastmountpoint=/home modified=2016-02-11 09:11:27 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-02-11 09:11:27 state=mounted
           *-volume:9
                description: Windows NTFS volume
                vendor: Windows
                physical id: a
                bus info: scsi@0:0.0.0,10
                logical name: /dev/sda10
                version: 3.1
                serial: 925c-f23c
                size: 8165MiB
                capacity: 8184MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 12:03:37 filesystem=ntfs label=PBR Image modified_by_chkdsk=true mounted_on_nt4=true name=Microsoft recovery partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GHB0N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: A1B0
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 5
          bus info: usb@1:4.1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Multi-Card
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 2012062914345300
             capabilities: removable
             configuration: ansiversion=4 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
dad@dad-Inspiron-3646:~$ 

```

---

### Post by oldfred on 2016-02-11
I have the Dell 3647 which I got about a year ago, but it has i3 chip. 
I shrink Windows 8 to 40GB, but updates filled it. I had not planned on using Windows, but to watch TV via Comcast only Windows works. But then to update to Windows 10, I expanded back to 100GB.

I had 15.04, and just replaced it with 16.04 and have 15.10 which I have not booted recently in another / (root) partition. 
It boots almost as quick as my main Desktop and the only issue I have has been since updating to Windows 10 and watching a TV show for half an hour it will give memory low error. I did go back and install in Windows some Dell drivers.

In Ubuntu it has run extremely well, but have not used it a lot. It is dedicated to watching TV.

---

### Post by weatherman2 on 2016-02-11
That shouldn't be too slow, but I wouldn't expect it to be fast, either.  Your CPU is certainly not very fast - but it is quad core.  The J2900 you have is a quad core "Atom" basically - power-efficient netbook CPU:

[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+J2900+%40+2.41GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+J2900+%40+2.41GHz)

Multiple cores are of greater benefit in Windows because you have to run an anti-virus program in the background.  For simple user computers, doing one task at a time, a quad core CPU may not give you a big performance boost.  So, you are mostly using a single (slow) core on the CPU.

I use a netbook daily with Ubuntu on it.  It has a CPU that has about the same single-core performance as yours but not quad core.  Yours should be a little faster.  I find my netbook is a tad slow, but I'm used to it.  On the other hand, I upgraded the RAM to 16GB, which mostly means I can have more windows open at one time without slowing down.  I use another laptop with only 4GB of RAM and that one runs Ubuntu just fine, but if I open a dozen browser windows at one time it starts to swap out and really slow down til I reboot.

I also upgraded my hard drive to an SSD.  That would give you your biggest performance boost, by far.  It would allow windows to open much more quickly.  Consider it.  SSD prices have really been plunging.  You can get a 500GB SSD to replace your 500GB HDD for about $150 or so on sale, and the price will just keep dropping over time.  If you buy a new computer next year, you can use your SSD in it (Ubuntu should work automatically but of course Windows probably won't if you move.)

---

### Post by weatherman2 on 2016-02-11
But if you are needing to boot into recovery mode occasionally - I don't think I've EVER had to do that in 2+ years using Ubuntu on my netbook - then I suspect something else might be wrong.  Hard drive is a good place to start.  Try installing GSmartControl in Ubuntu and checking the current S.M.A.R.T. Attributes.  Look for a number of bad sectors more than 0 (RAW value).  If you have any, your drive could be failing.  Even one pending sector (a sector in a file that cannot be read) can cause awful problems and slowness if the sector is in the wrong place on your disk!

---

### Post by tahitiwibble on 2016-02-11
Thank you both for chipping in. What surprises me so much is the difference between my old Asus and this relatively new machine. 

**Oldfred**, it sounds like my 3646 should be doing a little better. 

**Weatherman**, thanks for your explanations, I'm downloading GSmartControl and will see what goes on. It's actually about 70-80 of the time I have to go through 'recovery'. In 10+ years of Ubuntu I never had to use recovery ever.

---

### Post by gordintoronto on 2016-02-12
You're running an old version of Ubuntu on a new computer, and that often leads to problems. With such a slow CPU, I would install Xubuntu 15.10.

But also +1 to checking the hard drive status.

---

### Post by MartyBuntu on 2016-02-12
It's a low powered "budget" machine.

It is what it is.

---

### Post by tahitiwibble on 2016-02-13
**gordintoronto**, I'll consider that although I usually just go from one LTS version to the next. I don't think I ever found an easy way to do it, so as seldom as possible is the order of the day. HDD was in perfect condition according to GSmartControl.

**MartyBuntu**, Yes, I knew that when I bought it, but I never thought though that it wouldn't stand up against my ancient Asus laptop. I wonder if more memory would help?

Thanks to you both.

---

### Post by mörgæs on 2016-02-13
4 GB of memory is more than enough. 
As mentioned above, give it the latest of software. 'Budget' or not has no significance.

---

### Post by weatherman2 on 2016-02-13
> **tahitiwibble said:**
> **gordintoronto**, I'll consider that although I usually just go from one LTS version to the next. I don't think I ever found an easy way to do it, so as seldom as possible is the order of the day. HDD was in perfect condition according to GSmartControl.

You mean, no Attributes were showing highlighted in pink on the Attributes tab?

It passed tests?  Try running the extended S.M.A.R.T. test if you haven't (may take a few hours).

---

### Post by tahitiwibble on 2016-02-13
> **weatherman2 said:**
> You mean, no Attributes were showing highlighted in pink on the Attributes tab?

It passed tests?  Try running the extended S.M.A.R.T. test if you haven't (may take a few hours).

I'll run it tonight and see.

---

### Post by tahitiwibble on 2016-02-13
> **mörgæs said:**
> 4 GB of memory is more than enough. 
As mentioned above, give it the latest of software. 'Budget' or not has no significance.

That was always the beauty of Ubuntu (Linux) wasn't it, that you never needed power-house computers to make the OS shine. You wouldn't believe some of the junk that I've installed (L)Ubuntu on. When is that next LTS version supposed to come out? :p

---

### Post by weatherman2 on 2016-02-13
I've got Ubuntu (not even Lubuntu) running well on some ten year old Dell laptops that can do only 2GB of RAM but do have dual core CPUs.  I use Ubuntu Flashback to get the old "Gnome" look - with Metacity the graphic performance is very adequate.  My local thrift store regularly gets Dell Inspiron E1505 (aka 6400) 15" laptops and sells them without hard drives for $10 to $20.  They are as fast as some of the newer budget laptops that have those Atom-derivative CPUs in them.  But I wouldn't dream of running Windows on them!

---

### Post by kansasnoob on 2016-02-13
> **weatherman2 said:**
> I've got Ubuntu (not even Lubuntu) running well on some ten year old Dell laptops that can do only 2GB of RAM but do have dual core CPUs.  I use Ubuntu Flashback to get the old "Gnome" look - with Metacity the graphic performance is very adequate.  My local thrift store regularly gets Dell Inspiron E1505 (aka 6400) 15" laptops and sells them without hard drives for $10 to $20.  They are as fast as some of the newer budget laptops that have those Atom-derivative CPUs in them.  But I wouldn't dream of running Windows on them!

+1! I prefer GNOME Shell somewhat, but basically anything with much under a 3 GHz CPU and 4 GB of RAM gets [flashback w/metacity]("http://ubuntuforums.org/showthread.php?t=2220264").

---

### Post by weatherman2 on 2016-02-13
Yeah, I love Lubuntu for what it is, but I hate the look and feel, and I find Gnome Flashback works just as well and fast enough.

---

### Post by oldfred on 2016-02-13
I also use flashback/fallback/gnome-panel. Both because laptop only has 1.5GB and I still prefer menus.

They have improved Unity so it almost is functional for me. But my last issue is that they do not assume you open two of anything full screen. With fallback, I can see several open windows in bottom panel and directly click on the one I want. With Unity I have to click on icon, and choose which one I want. Just not as convenient for the way I work.

---

### Post by mörgæs on 2016-02-14
> **tahitiwibble said:**
> That was always the beauty of Ubuntu (Linux) wasn't it, that you never needed power-house computers to make the OS shine. You wouldn't believe some of the junk that I've installed (L)Ubuntu on. When is that next LTS version supposed to come out? :p

The desire to run LTS only is a problem, not a solution. In many threads I have solved problems by dragging people's attention from LTS's to the short term versions, in this case 15.10. Yes, it takes a little more time to reinstall twice a year but it gives a lot of advantages, especially for new hardware. It's a shame that many people deem short term Buntus unsuitable without even testing. 

Anyway, you could also install 16.04 (development version) as of today and help testing and reporting bugs. It's the best way to ensure that it works well on your hardware.

---

### Post by Neptune_Computer_S on 2016-02-14
Dear Sir,
Neptune Computer Systems, has tested the above mentioned Dell Inspiron 3646 with an Intel Pentium J2900 clocked at 1.8 GHz using Ubuntu 14.04.3 LTS 64 Bit alongside Windows 10 Pro, 64 Bit and found that the problem that you mentioned above (slow system) is a common problem for this computer, due to lack of CPU drivers.

Yours Sincerely
<snipped company name>

---

### Post by tahitiwibble on 2016-02-14
> **mörgæs said:**
> The desire to run LTS only is a problem, not a solution. In many threads I have solved problems by dragging people's attention from LTS's to the short term versions, in this case 15.10. Yes, it takes a little more time to reinstall twice a year but it gives a lot of advantages, especially for new hardware. It's a shame that many people deem short term Buntus unsuitable without even testing. 

Anyway, you could also install 16.04 (development version) as of today and help testing and reporting bugs. It's the best way to ensure that it works well on your hardware.

OK, you've got me! :lolflag: After considering that particular food for thought I will be upgrading more regularly than before. And I had never even entertained the idea of a development version, but I do love, and owe a lot to Ubuntu, so I guess I could try to help out even if it will be in a very small way.

---

### Post by tahitiwibble on 2016-02-14
> **Neptune_Computer_S said:**
> Dear Sir,
Neptune Computer Systems, has tested the above mentioned Dell Inspiron 3646 with an Intel Pentium J2900 clocked at 1.8 GHz using Ubuntu 14.04.3 LTS 64 Bit alongside Windows 10 Pro, 64 Bit and found that the problem that you mentioned above (slow system) is a common problem for this computer, due to lack of CPU drivers.

Yours Sincerely
<snipped company name>

Game, set and maaat  :-({|=  , heck no! am not giving up that easily :p

---

### Post by oldfred on 2016-02-14
Dell is one of the better companies.
With 12.04 they released Sputnik which was a set of drivers for its hardware to work with 12.04. And all those changes ended up in 14.04.

But that is often why with newer hardware to use the newest Ubuntu release as it takes time for drivers & other support software to catch up with kernel release, support software release & then have those releases included in a distribution like Ubuntu.

Intel has also been updating video drivers and other support software. While a lot is for newer chips, some not even released yet, some of those changes help older versions.

---

### Post by tahitiwibble on 2016-02-14
So Gentlemen, this has been a most interesting conversation. Thanks many times for your participation! 

I have always been able to fix and build my own and some other peoples computers but am really not a hardware guy (could never have afforded to become one basically) and would be very grateful if you would be kind enough to explain to me in a nutshell, why this first machine running W10 (the **only** reason I keep it is for my RC flight simulator) and 14.04 on dual boot ........ why is this machine lagging so miserably far behind my old laptop, running dual boot W7 and 14.04. And what would you try if it was yours, **apart** from OS upgrade ;)

Old Asus;

```
dad@dad-laptop:~$ sudo lshw
[sudo] password for dad: 
dad-laptop                
    description: Notebook
    product: K50IJ ()
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: A2N0AS223331079
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: chassis=notebook cpus=2 uuid=963681DF-1591-CE4D-0700-E0CB4EB1CD9A
  *-core
       description: Motherboard
       product: K50IJ
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 217
          date: 12/04/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 478
          size: 2101MHz
          capacity: 2101MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
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
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1-Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 6GiB
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
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:ec00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe900000-fe9fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e880(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e800(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e480(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:feafbc00-feafbfff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:feaf4000-feaf7fff
        *-pci:0
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
             resources: irq:40
        *-pci:1
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
             resources: irq:41 memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 1c:4b:d6:79:51:eb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-98-generic-pae firmware=N/A ip=192.168.1.61 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:febf0000-febfffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:bde00000-bdffffff ioport:be000000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e400(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e080(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e000(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:feafb800-feafbbff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
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
             resources: irq:43 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=32) memory:feafb000-feafb7ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54503
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB3O
                serial: 100123PB4C001YGZMJPB
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=76692ca8
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 3c98-ac5d
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary hidden fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/OS
                   version: 3.1
                   serial: be49e10c-82ac-3842-b2f5-9c958441a9d4
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-08 18:46:21 filesystem=ntfs label=OS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 9e3bae1a-a7f0-469d-bd44-1d4ea22bb9cf
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-12 06:45:22 filesystem=ext4 lastmountpoint=/ modified=2016-01-19 15:48:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2016-02-14 05:44:05 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 222GiB
                   capacity: 222GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/DATA
                      capacity: 222GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A4S
                vendor: Slimtype
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: JA22
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium-Ion Battery
       product: F82-22
       vendor: AS044Ih43E
       physical id: 1
       version: 05/04/14
       serial: <600
       slot: In the back
       capacity: 4200mWh
       configuration: voltage=10.8V
dad@dad-laptop:~$
```


New Dell;

```
dad@dad-Inspiron-3646:~$ sudo lshw
[sudo] password for dad: 
dad-inspiron-3646         
    description: Desktop Computer
    product: Inspiron 3646 (xxx123x#ABA)
    vendor: Dell Inc.
    version: A04
    serial: C5NB822
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=103C_5335KV sku=xxx123x#ABA uuid=44454C4C-3500-104E-8042-C3C04F383232
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A04
          date: 08/20/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-board UNCLAIMED
          description: Motherboard
          product: 0V6D8J
          vendor: Dell Inc.
          physical id: 2
          version: A00
          serial: .C5NB822.CN701634AG00UW.
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU  J2900  @ 2.41GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU  J2900  @ 2.41GHz
          slot: CPU 1
          size: 1577MHz
          capacity: 2656MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1 Cache
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M471B5173DB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 17E50CBB
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: ValleyView SSA-CUnit
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: ValleyView Gen7
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:106 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
        *-storage
             description: SATA controller
             product: ValleyView 6-Port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:104 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:90914000-909147ff
        *-usb
             description: USB controller
             product: ValleyView USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:103 memory:90900000-9090ffff
        *-generic UNCLAIMED
             description: Encryption controller
             product: ValleyView SEC
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:90800000-908fffff memory:90700000-907fffff
        *-multimedia
             description: Audio device
             product: ValleyView High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:107 memory:90910000-90913fff
        *-pci:0
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:90600000-906fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 4c:bb:58:14:fe:a8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-77-generic firmware=N/A ip=192.168.1.43 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:90600000-9067ffff memory:90680000-9068ffff
        *-pci:2
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:90500000-905fffff ioport:90400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: b0:83:fe:72:3e:e0
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:105 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff
        *-isa
             description: ISA bridge
             product: ValleyView Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: ValleyView SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:90915000-9091501f ioport:2000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKX-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 20.0
             serial: WD-WCC2EHAT3N4X
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c6cd5a82-5640-4875-9a16-6dbc6ce5b05d sectorsize=512
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: 562c-863d
                size: 495MiB
                capacity: 499MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: 2c87-e300
                size: 15MiB
                capacity: 39MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat name=Basic data partition
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: cb3c18dc-7080-47ff-8a39-0c1b3ee69865
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 1c89-840e
                size: 720MiB
                capacity: 749MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 10:10:20 filesystem=ntfs label=WINRETOOLS modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 48e2e9d1-54bc-674b-980d-2b21f2742f00
                size: 123GiB
                capacity: 123GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 10:10:27 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: 127e-72f9
                size: 424MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-11-13 06:15:20 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: b7ad76d4-bb58-482d-9930-2ce1a0914ba3
                size: 18GiB
                capacity: 18GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-02-16 20:12:27 filesystem=ext4 lastmountpoint=/ modified=2016-02-11 09:11:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-02-11 09:11:26 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: 38bb7c1a-acdb-4967-b666-187b7664adcb
                size: 7627MiB
                capacity: 7628MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:8
                description: EXT4 volume
                vendor: Linux
                physical id: 9
                bus info: scsi@0:0.0.0,9
                logical name: /dev/sda9
                logical name: /home
                version: 1.0
                serial: 1a65b39e-19b6-49d3-8657-6037ea2ef906
                size: 306GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-02-16 20:12:29 filesystem=ext4 lastmountpoint=/home modified=2016-02-11 09:11:27 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-02-11 09:11:27 state=mounted
           *-volume:9
                description: Windows NTFS volume
                vendor: Windows
                physical id: a
                bus info: scsi@0:0.0.0,10
                logical name: /dev/sda10
                version: 3.1
                serial: 925c-f23c
                size: 8165MiB
                capacity: 8184MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-10-24 12:03:37 filesystem=ntfs label=PBR Image modified_by_chkdsk=true mounted_on_nt4=true name=Microsoft recovery partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GHB0N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: A1B0
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 5
          bus info: usb@1:4.1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Multi-Card
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 2012062914345300
             capabilities: removable
             configuration: ansiversion=4 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
dad@dad-Inspiron-3646:~$
```

---

### Post by kurt18947 on 2016-02-14
No expert here but I wonder if this has something to do with your problem:

```
*-board **UNCLAIMED**
          description: Motherboard
          product: 0V6D8J
          vendor: Dell Inc.
          physical id: 2
          version: A00
          serial: .C5NB822.CN701634AG00UW.

```

As I understand it, Ubuntu/Open Source developers don't get the pre-release specifications and samples of hardware that Microsoft gets for example. So it takes time after
hardware is released to develop drivers for the new hardware. I've used a few different 'flavors' of 16.04 and they've been pretty stable. They use Linux image 4.0.x. vs. 14.04s image
3.13.xx version. Unlike Windows many hardware drivers are 'baked into' the kernel so using a more recent kernel should also provide better new hardware support. You could create one or more live USBs of 16.04 and see if they perform any better. Live sessions running off DVD can be pretty laggy, live sessions running of liveUSB are pretty fast in my experience.

---

### Post by oldfred on 2016-02-14
I might suspect video drivers. Intel is updating those.

Since my 3647 runs so well with 15.10 and 16.04, I might even suggest another 25GB / (root) partition with 16.04 on hard drive, just to see if it works better.

---

### Post by tahitiwibble on 2016-02-14
> **kurt18947 said:**
> As I understand it, Ubuntu/Open Source developers don't get the pre-release specifications and samples of hardware that Microsoft gets for example. So it takes time after
hardware is released to develop drivers for the new hardware. I've used a few different 'flavors' of 16.04 and they've been pretty stable. They use Linux image 4.0.x. vs. 14.04s image
3.13.xx version. Unlike Windows many hardware drivers are 'baked into' the kernel so using a more recent kernel should also provide better new hardware support. You could create one or more live USBs of 16.04 and see if they perform any better. Live sessions running off DVD can be pretty laggy, live sessions running of liveUSB are pretty fast in my experience.

Hm, sounds very logical ...... I wonder if that's it? 16.04 here we come.

---

### Post by tahitiwibble on 2016-02-14
> **oldfred said:**
> I might suspect video drivers. Intel is updating those.

Since my 3647 runs so well with 15.10 and 16.04, I might even suggest another 25GB / (root) partition with 16.04 on hard drive, just to see if it works better.

As in 'triple boot'?

---

### Post by oldfred on 2016-02-14
I have two Ubuntu installs on sda, and several more on sdb on my main desktop.

My Dell is also triple boot as it has a 1TB drive. After I shank Windows to 40GB I had so much space I did know what to do with all of it. But then expanded Windows back to 100GB. I normally install Ubuntu into a 25GB / partition but have all my data folder like Docuements, Music, Videos, etc in separate /mnt/data partition that I then mount in every install.

---

### Post by tahitiwibble on 2016-02-14
> **oldfred said:**
> I normally install Ubuntu into a 25GB / partition but have all my data folder like Docuements, Music, Videos, etc in separate /mnt/data partition that I then mount in every install.

**Oldfred** please bear with me for just a little while longer. Sooo  ........ I'm going to shrink a partition or two to make space for 16.04 and then install as usual with my existing home data being accessed as it is by the W10 and 14.04 partitions. I go into cold sweats every time I update from one LTS to another, given that I am having so much trouble with this machine and have to go into Ubuntu 'recovery' so often just to boot successfully ........ am I going to have a heart attack? :roll: I have not yet figured out how to re-install an identical OS set-up to the preceding LTS with all the same programs etc.

---

### Post by oldfred on 2016-02-14
This is my  backup procedure. See dpkg list for application list backup/reinstall.
I liked having old install, so I could go back and find some setting I forgot about. So once I changed to new install to new partition, I could still boot into old install if needed. Or mount some configuration file to find settings. 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

I typically do not restore /home (but mine is not a separate partition), but do reinstall list of installed apps. I found I was running the same commands with each install. So I listed history and converted to bash drive. Then 75% of a new install is automated. And I keep trying to find command line ways to do more, so I can include in my scripts. Script auto edits fstab, to mount /mnt/data partition and link folders into /home.

---

### Post by weatherman2 on 2016-02-14
It's handy to have a little portable USB hard drive around for projects like this.  You can install various OSes on it and just move it to different machines that can boot off of USB.  Ubuntu seems to tolerate being moved to very different hardware in most cases without issue.  You can do the same thing with a USB flash drive, as large drives are getting cheap, but some of the cheaper ones can be frustrating slow (poor write performance).

There's nothing wrong with multiple boot OSes on a single drive.  Windows I think might prefer being in a primary partition, but Linux doesn't care - you can make as many logical partitions on an old MSDOS-style partitioning scheme as you like inside an Extended Partition - or if you use a GPT partitioned disk it's even easier.  You can even make a single swap partition and share it among the various Linux distros you install.

---

### Post by weatherman2 on 2016-02-14
I like the old-style "dump" command to make reliable backups of OS partitions.  You do have to install dump and find the command line opts you want, but it saves the dump of the OS in a single file that you can then zip up.  You can use rsync too but use the -x switch to skip syncing anything out side the partition.  And you'll want to do this from a live boot and not while the OS is booted, unless you used an LVM and know how to make a snapshot etc.

---

### Post by tahitiwibble on 2016-02-14
Well to all you guys another huge and heartfelt **thank you**. Your company has been a pleasure and your suggestions/remarks/ideas and knowledge have been priceless. I have to analyse and digest everything and then will make the impending improvements.

If you ever need information about either main or even the more obscure islands in French Polynesia .... hit me up.

My very best wishes,

Martin

---

### Post by mörgæs on 2016-02-15
Good luck.
Could you please change the thread title to *Dell Inspiron 3646* or similar? It will help people searching for information for this particular Dell.

---

