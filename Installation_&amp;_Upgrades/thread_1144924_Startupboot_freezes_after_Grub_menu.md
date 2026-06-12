---
title: "Startup/boot freezes after Grub menu"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by brunolabs on 2009-04-29
Hi!

I have got this problem after a fresh install of Jaunty:

After the Grub menu selection I get a terminal screen with the following information:

```
Boot from (hd0, 4) ext4 18ebd363-befe-43fb-... (this strange code/serial goes on)
Starting up...
```

And this freezes booting for about 1-2 minutes! After that time the Ubuntu loading screen appears and startup proceeds normally.

Can anyone help me with this? What causes this problem? How can I solve it?

This never happened in previous Ubuntu versions.

I tried both ext3 and ext4 filesystems and the problem remains.

---

### Post by brunolabs on 2009-05-01
desperate bump

---

### Post by brunolabs on 2009-05-01
Hi!

I have got this problem after a fresh install of Jaunty:

After the Grub menu selection I get a terminal screen with the following information:

```
Boot from (hd0, 4) ext4 18ebd363-befe-43fb-... (this strange code/serial goes on)
Starting up...
```

And this freezes booting for about 1-2 minutes! After that time the Ubuntu loading screen appears and startup proceeds normally.

Can anyone help me with this? What causes this problem? How can I solve it?

This never happened in previous Ubuntu versions.

I tried both ext3 and ext4 filesystems and the problem remains.



PS- I double posted this thread on another subtopic. Now I realized this one may be more suited for this problem.

---

### Post by brunolabs on 2009-05-01
bump

---

### Post by brunolabs on 2009-05-02
Can anyone help me on this one?
Please.

---

### Post by brunolabs on 2009-05-02
Can anyone help?

---

### Post by caljohnsmith on 2009-05-02
Brunolabs, please do not start duplicate threads of the same subject/problem, because otherwise it can lead to others duplicating each others' efforts when trying to help you. :)

About your problem, how about trying this: on start up when you get the Grub menu, select the Ubuntu entry you intend to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, then remove the "quiet" at the end of the kernel line:
```
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=80a49462-c6f8-45dd-ba1a-9f63d0ee6885 ro [COLOR="Red"]quiet[/COLOR] splash 
```
Press enter to save the change, and finally press "b" to boot. Then watch the messages carefully as Ubuntu tries to boot, and please let me know exactly what happens--where Ubuntu gets hung up. Hopefully that will give us a better clue what is causing Ubuntu to falter on start up. 

John

---

### Post by brunolabs on 2009-05-02
First of all, thanks for the help :) and sorry for the double posting :(.

Well, after doing what you suggested I found out where the startup froze:

```
ata1: SATA link up 1,5 Gbps
ata1: link online but drive misclassified, retrying
ata1: reset failed (errno=-11), retrying in 35 secs
```

It freezes for awile (those 35s), then repeats this code block a few more times (and more waiting).
At some point a lot of text appears on screen but too fast to read and then Ubuntu starts normally with the orange bar.

Any ideas how to solve this?


Thanks again! ;)

---

### Post by caljohnsmith on 2009-05-02
Great, at least we have more of a clue at what point Ubuntu is faltering, but I'm confused by the error you got--I don't know what Ubuntu is referring to when it says "ata1: SATA link up 1,5 Gbps". Do you have an idea what that refers to? If not, it might help to post your computer's hardware specifications:
```
sudo lshw
```

John

---

### Post by brunolabs on 2009-05-03
I have no idea what may be causing this so here's the "lshw" output:

```
description: Desktop Computer
    product: P5SD1-FM2
    vendor: FUJITSU SIEMENS
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=48BB45CA-84FE-D511-A529-CC744D1709F8
  *-core
       description: Motherboard
       product: P5SD1-FM2
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: Rev 1.xx
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0304 (01/03/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          slot: LGA 775
          size: 2800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
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
          physical id: 2b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: SiS649 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV410 [Radeon X700]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS965 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 48
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
           *-cdrom:0
                description: DVD reader
                product: DROM6216
                vendor: PHILIPS
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DD08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD_RW ND-4551A
                vendor: _NEC
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1-84
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 00
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
        *-ide:1
             description: IDE interface
             product: 182 SATA/RAID Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=64
           *-disk
                description: ATA Disk
                product: WDC WD2500JS-55N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cfcb27b7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /windows
                   version: 3.1
                   size: 115GiB
                   capacity: 115GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-05-01 15:51:55 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   size: 114GiB
                   capacity: 117GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2008-04-28 23:29:21 filesystem=ext3 modified=2008-05-01 13:09:29 mounted=2008-05-01 13:08:56 state=clean
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 114GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2957MiB
                      capabilities: nofs
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm bus_master cap_list
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


Here's also "sudo lshw | grep SATA":

```
 product: 182 SATA/RAID Controller
```


With this same hardware I haven't had this kind of problems with the other Ubuntu versions.

---

### Post by Elfy on 2009-05-03
Hi - it seems you're not alone - [http://tinyurl.com/cax2s3](http://tinyurl.com/cax2s3)

Can you look in your log files - System Admin - Log File Viewer - have a look at messages/syslog around the time that the boot stops - look what is there and see if there is any more information that can help.

---

### Post by brunolabs on 2009-05-03
Looks like a Fujitsu-Siemens PC's problem...

---

### Post by TomB19 on 2009-05-03
If it were me, I would look for a BIOS upgrade.

---

### Post by brunolabs on 2009-05-16
Has anyone found a way to solve this problem?

---

### Post by Kenrro on 2009-05-26
I have the Same problem here:

Using Jaunty 9.04
Kernel Linux 2.6.28-12-generic

dmesg:
```

[    2.592144] Driver 'sd' needs updating - please use bus_type methods
[    2.592205] Driver 'sr' needs updating - please use bus_type methods
[    2.592505] sata_sis 0000:00:05.0: version 1.0
[    2.592574] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.592628] sata_sis 0000:00:05.0: Detected **SiS 182/965 chipset**
[    2.592843] scsi0 : sata_sis
[    2.593025] scsi1 : sata_sis
[    2.593134] ata1: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xf900 irq 17
[    2.593187] ata2: SATA max UDMA/133 cmd 0xfb00 ctl 0xfa00 bmdma 0xf908 irq 17
[    2.912065] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.912122] ata1: link online but device misclassified, retrying
[    2.912172] ata1: reset failed (errno=-11), retrying in 10 secs
[   12.912061] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.912117] ata1: link online but device misclassified, retrying
[   12.912167] ata1: reset failed (errno=-11), retrying in 10 secs
[   22.912060] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.912117] ata1: link online but device misclassified, retrying
[   22.912166] ata1: reset failed (errno=-11), retrying in 35 secs
[   57.592016] ata1: limiting SATA link speed to 1.5 Gbps
[   57.912060] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   57.912117] ata1: link online but device misclassified, device detection might fail
[   57.920661] ata1.00: ATA-8:** ST31000340AS**, SD15, max UDMA/133
[   57.920711] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   57.936661] ata1.00: configured for UDMA/133
[   58.256060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   58.256116] ata2: link online but device misclassified, retrying
[   58.256166] ata2: reset failed (errno=-11), retrying in 10 secs
[   68.256060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   68.256116] ata2: link online but device misclassified, retrying
[   68.256166] ata2: reset failed (errno=-11), retrying in 10 secs
[   78.256060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   78.256116] ata2: link online but device misclassified, retrying
[   78.256166] ata2: reset failed (errno=-11), retrying in 35 secs
[  112.936016] ata2: limiting SATA link speed to 1.5 Gbps
[  113.256060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  113.256116] ata2: link online but device misclassified, device detection might fail
[  113.264228] ata2.00: ATAPI: **HL-DT-STDVD-RAM GH22LS30**, 1.01, max UDMA/100
[  113.280266] ata2.00: configured for UDMA/100
[  113.280756] scsi 0:0:0:0: Direct-Access     ATA      ST31000340AS     SD15 PQ: 0 ANSI: 5
[  113.280961] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[  113.281044] sd 0:0:0:0: [sda] Write Protect is off
[  113.281093] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  113.281135] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  113.281289] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[  113.281367] sd 0:0:0:0: [sda] Write Protect is off
[  113.281416] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  113.281456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  113.281518]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[  113.392618] sd 0:0:0:0: [sda] Attached SCSI disk
[  113.392741] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  113.394748] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LS30 1.01 PQ: 0 ANSI: 5
[  113.398417] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[  113.398478] Uniform CD-ROM driver Revision: 3.20
[  113.398664] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  113.398723] sr 1:0:0:0: Attached scsi generic sg1 type 5
```

on SATA1: Barracuda 7200.11 SATA 3Gb/s 1-TB Hard Drive
on SATA2: LG DVD Writer, [B]HL-DT-STDVD-RAM GH22LS30

[/B]Couldthis be a problem with the chipset? It works fine in 8.10

Kenrro.

---

### Post by maranda on 2009-05-29
I've the same problem, my chipset is SiS 182/965.
Worked perfectly with 8.10.

---

### Post by brunolabs on 2009-05-29
How can we submit a bug/problem report for this?

---

### Post by Elfy on 2009-05-29
> **brunolabs said:**
> How can we submit a bug/problem report for this?
This should help you do that - 
[http://ubuntuforums.org/showpost.php?p=6367705&postcount=1](http://ubuntuforums.org/showpost.php?p=6367705&postcount=1)

---

### Post by brunolabs on 2009-05-29
I have reported the bug at Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/381777]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/381777")

For everyone with this problem, go to the link and subscribe.

---

### Post by brunolabs on 2009-06-06
Anyone knows how much time does it take for a bug request like this one (above) to get processed?

---

### Post by Elfy on 2009-06-07
No idea - but it might be worth getting the other user here with the same problem to confirm the bug.

---

### Post by dirtygreek on 2009-06-07
I have the same problem.

---

### Post by brunolabs on 2009-06-07
> **forestpixie said:**
> No idea - but it might be worth getting the other user here with the same problem to confirm the bug.

At least three more users have this problem:

-maranda
-Kenrro
-dkulchenko


I wonder if they will check on this thread again...

(I PM'd them)

---

### Post by Kenrro on 2009-06-08
> **brunolabs said:**
> I have reported the bug at Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/381777](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/381777)

For everyone with this problem, go to the link and subscribe.

Done, thanks.

Kenrro.

---

### Post by dkulchenko on 2009-07-28
> **brunolabs said:**
> At least three more users have this problem:

-maranda
-Kenrro
-dkulchenko


I wonder if they will check on this thread again...


I have just now. :D I'd been putting up with it for a good month, and decided that enough is enough. There are tons of bug reports being filed, dozens of forum posts all over the internet on this issue, yet it seems that nothing is being done. No one has yet submitted a solution/workaround.

I'll try installing a daily build of 9.10 today, to see if the problem persists with 2.6.30. Has anyone done this already?

---

### Post by brunolabs on 2009-07-30
> **dkulchenko said:**
> I have just now. :D I'd been putting up with it for a good month, and decided that enough is enough. There are tons of bug reports being filed, dozens of forum posts all over the internet on this issue, yet it seems that nothing is being done. No one has yet submitted a solution/workaround.

I'll try installing a daily build of 9.10 today, to see if the problem persists with 2.6.30. Has anyone done this already?


Not yet. Have you tried 9.10? Does it solve the problem?

Thanks.


PS: btw, the bug report at launchpad has been confirmed.

---

### Post by Miguel on 2009-08-18
Hi guys,

I don't know whether this is related or not but I've just installed Kubuntu 9.10 into a spare partition I had on my laptop. Because I do use this laptop (Ubuntu 9.04 and Windows 7 installed aside), I didn't want to mess much with grub, and thus I didn't install the new grub.

The thing is, even though Ubuntu 9.04 (even with the xorg-edgers kernel) and windows7 boot OK, everytime I try to boot kubuntu I get only the following:
```

Boot from (hd0,6) ext4 2bbd02db-7cda-4038-8a5a-0179307ff2c5

```
I don't even get the "Starting up" line. I must admit, however, I haven't waited for more than 5 minutes. My current relevant entry in grub's menu is:
```

title		Kubuntu 9.10
uuid		2bbd02db-7cda-4038-8a5a-0179307ff2c5
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=2bbd02db-7cda-4038-8a5a-0179307ff2c5 ro splash usbcore.autosuspend=1 rootfstype=ext4
initrd		/boot/initrd.img-2.6.31-5-generic

```

I got the UUID of the relevant partition with vol_id, and I've checked it works in Ubuntu by substituting /dev/sda7 with UUID=***** in /etc/fstab and remounting the partition, so that isn't wrong. Also, should the kernel image not be found, I'd get an error, which I don't.

Does anybody have a clue? In case it matters, this PC is a Lenovo T400 with the latest BIOS and hybrid graphics disabled on it.

---

### Post by brunolabs on 2009-08-18
Try the suggestions made in the first page of this thread. The one that removes the quiet boot and allows you to see where the boot hangs. If you get the same output as I/we did, looks like it is the same problem.

If you do, please check the bug report at Launchpad (link above) and subscribe it, so we can get this annoying bug fixed.

---

### Post by Miguel on 2009-08-19
> **brunolabs said:**
> Try the suggestions made in the first page of this thread. The one that removes the quiet boot and allows you to see where the boot hangs. If you get the same output as I/we did, looks like it is the same problem.

If you do, please check the bug report at Launchpad (link above) and subscribe it, so we can get this annoying bug fixed.

I already tried that. Actually, one of the first things I do in my personal ubuntu installs is removing the quiet option from grub. In any case, I didn't even get to see "Starting up..." line. However, I think I just solved it. For some weird reason, reinstalling grub from Ubuntu fixed it. I used the following command (dangerous!!!!!):
```

sudo grub-install /dev/sda --no-floppy --recheck

```

---

### Post by brunolabs on 2009-08-22
> **Miguel said:**
> In any case, I didn't even get to see "Starting up..." line.

Seems like a different issue then.
Thanks for the help anyway.

---

### Post by Punk_Nadel on 2009-08-27
I've opened a kernel bug for this:
[http://bugzilla.kernel.org/show_bug.cgi?id=14075](http://bugzilla.kernel.org/show_bug.cgi?id=14075)

P.S. I don't use ubuntu ;)

---

### Post by brunolabs on 2009-08-28
> **Punk_Nadel said:**
> I've opened a kernel bug for this:
[http://bugzilla.kernel.org/show_bug.cgi?id=14075](http://bugzilla.kernel.org/show_bug.cgi?id=14075)

P.S. I don't use ubuntu ;)

Nice work! ;)

What distro do you use then? Do you have this problem with another OS?

---

### Post by Punk_Nadel on 2009-08-30
> **brunolabs said:**
> ...What distro do you use then?...
Gentoo ;)

//EDIT: to everybody who knows how to use a kernel patch, here it is: [http://bugzilla.kernel.org/attachment.cgi?id=22953](http://bugzilla.kernel.org/attachment.cgi?id=22953)

have fun! :)

---

### Post by brunolabs on 2009-09-10
Hi all!

Has anyone here tried Karmic Koala? Does it have the problem solved?


Cheers.

---

### Post by freaz on 2009-10-29
I tried, and still not working :(

---

### Post by brunolabs on 2009-11-01
> **freaz said:**
> I tried, and still not working :(

:(

I wonder if this will ever be solved...

---

### Post by brunolabs on 2009-12-01
> **Punk_Nadel said:**
> 
//EDIT: to everybody who knows how to use a kernel patch, here it is: [http://bugzilla.kernel.org/attachment.cgi?id=22953](http://bugzilla.kernel.org/attachment.cgi?id=22953)

have fun! :)


Found how to apply the patch: [http://www.linuxheadquarters.com/howto/tuning/kernelpatch.shtml]("http://www.linuxheadquarters.com/howto/tuning/kernelpatch.shtml")

But will it work? It will probably mess up with the Ubuntu updates... or worse. :(
At the moment I can't manage to have a kernel panic error or something like that and reinstall the OS. Have a lot of important stuff on the pc.

Anyone tried it?


Thanks for the help! ;)

---

### Post by brunolabs on 2009-12-05
This thread may become more effective on the "Hardware & Laptops" or "General Help" categories.

Is it possible for a forum admin to move it please?

Thanks.

---

### Post by brunolabs on 2010-01-09
hmmm bump

---

### Post by brunolabs on 2010-05-03
> **brunolabs said:**
> Hi all!

Has anyone here tried Karmic Koala? Does it have the problem solved?


Cheers.


Same question for 10.04...

:(

---

### Post by brunolabs on 2010-05-07
Last Bump

---

