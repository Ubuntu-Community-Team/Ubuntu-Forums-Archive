---
title: "HDs missing"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by maraschin on 2006-03-15
hi,

I've installed ubuntu 5.1 with 14 HDs (all IDE)...
Now I'm trying to add a new set, so I plugged a new IDE card that can support up to 8 IDEs (RocketRAID 454 - I've two BTW) and connect all the HDs. The bios of the card found all 8 HDs and ubuntu started...

Well, I can see 4 new HDs to be partitioned and added to the LVM but there are 4 still missing...  IS THERE ANY LIMITATIONS on the number of discs we can insert?

Here my /proc/partitions
major minor  #blocks  name

   3     0   80418240 hda
   3     1    2931831 hda1
   3     2      96390 hda2
   3     3   77385105 hda3
   3    64  120627360 hdb
   3    65  120624021 hdb1
  33     0  195312500 hde
  33     1  195310206 hde1
  33    64  195312500 hdf
  33    65  195310206 hdf1
  34     0  195312500 hdg
  34     1  195310206 hdg1
  34    64  195312500 hdh
  34    65  195310206 hdh1
  56     0  160086528 hdi
  56     1  160079661 hdi1
  56    64  160086528 hdj
  56    65  160079661 hdj1
  57     0  195312500 hdk
  57     1  195310206 hdk1
  57    64  195312500 hdl
  57    65  195310206 hdl1
  88     0  160086528 hdm
  88     1  160079661 hdm1
  88    64  160086528 hdn
  88    65  160079661 hdn1
  89     0  244198584 hdo
  89     1  244196001 hdo1
  89    64  244198584 hdp
  89    65  244196001 hdp1
  90     0  199148544 hdq
  90    64  199148544 hdr
  91     0  199148544 hds
  91    64  199148544 hdt
 253     0 2421174272 dm-0
 253     1    2931831 dm-1
 253     2      96390 dm-2
 253     3   77385105 dm-3
 253     4  120624021 dm-4
 253     5  195310206 dm-5
 253     6  195310206 dm-6
 253     7  195310206 dm-7
 253     8  195310206 dm-8
 253     9  160079661 dm-9
 253    10  160079661 dm-10
 253    11  195310206 dm-11
 253    12  195310206 dm-12
 253    13  160079661 dm-13
 253    14  160079661 dm-14
 253    15  244196001 dm-15
 253    16  244196001 dm-16
 253    17 2421174272 dm-17

Cheers,

---

### Post by roachk71 on 2006-03-16
[LEFT]I believe the Linux kernel only allows up to 15 mounted stand-alone volumes (in partitions.) If you're using a RAID card, I think it's possible to have up to 127 drives configured as a RAID.

A note about this:

I'm not quite sure about this version of the kernel, but prior versions only supported SCSI RAID. It would be worthwhile to check this out, but I don't have the threads right off the bat; I'll come back here later on.

Keep checking...

Threads/articles found so far:

[http://www.ubuntuforums.org/showthread.php?t=137600]("http://www.ubuntuforums.org/showthread.php?t=137600")
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html")
[http://www.linuxplanet.com/linuxplanet/tutorials/4349/5/]("http://www.linuxplanet.com/linuxplanet/tutorials/4349/5/")

Unfortunately, you'll have to completely reinstall to take advantage of this option, keeping a drive in reserve to boot from, and that drive **MUST** be the primary IDE master. This unless you don't mind booting from CD or floppy every time.

There's also a caveat: the slightest error on any of the drives will probably kick that drive out of the array until the problem's fixed, making this a possibly time-consuming option.
[/LEFT]

---

### Post by maraschin on 2006-03-17
My problem seems to be the limit on the number of IDE channels.
( I've posted another one: [http://ubuntuforums.org/showthread.php?t=145118](http://ubuntuforums.org/showthread.php?t=145118) )

I found this article:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0407.0/1300.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0407.0/1300.html)
and this:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0411.1/0617.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0411.1/0617.html)

The problem is that right now there is a limit of 10!
I did not check and try to use 16, I got this "nice" problem:

Mar 17 20:25:57 localhost kernel: [4294677.997000] Probing IDE interface ide9...
Mar 17 20:25:57 localhost kernel: [4294678.261000] hds: Maxtor 6L200P0, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294678.516000] hdt: Maxtor 6L200P0, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294678.570000] ide9 at 0xc400-0xc407,0xc802 on irq 18
Mar 17 20:25:57 localhost kernel: [4294678.570000] hds: max request size: 1024KiB
Mar 17 20:25:57 localhost kernel: [4294678.591000] hds: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(100)
Mar 17 20:25:57 localhost kernel: [4294678.592000] hds: cache flushes supported
Mar 17 20:25:57 localhost kernel: [4294678.593000]  hds: unknown partition table
Mar 17 20:25:57 localhost kernel: [4294678.598000] hdt: max request size: 1024KiB
Mar 17 20:25:57 localhost kernel: [4294678.620000] hdt: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(100)
Mar 17 20:25:57 localhost kernel: [4294678.622000] hdt: cache flushes supported
Mar 17 20:25:57 localhost kernel: [4294678.622000]  hdt: unknown partition table
Mar 17 20:25:57 localhost kernel: [4294678.629000] Probing IDE interface ide:...
Mar 17 20:25:57 localhost kernel: [4294678.893000] hdu: WDC WD2000BB-00DAA3, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294679.148000] hdv: WDC WD2000BB-00DAA3, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294679.201000] ide:: failed to initialize IDE interface
Mar 17 20:25:57 localhost kernel: [4294679.201000] Probing IDE interface ide;...
Mar 17 20:25:57 localhost kernel: [4294679.465000] hdw: WDC WD2000JB-00DUA3, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294679.720000] hdx: WDC WD2000JB-00DUA3, ATA DISK drive
Mar 17 20:25:57 localhost kernel: [4294679.773000] ide;: failed to initialize IDE interface

So, after ide9 it will try to map ide: and ide; ...
and it will even find the HDs but it will fail in initialize the IDE interface...

Is there anyone working on this?
Is there a patch?

Cheers,

---

### Post by maraschin on 2006-03-18
I've posted the solution at:
[http://ubuntuforums.org/showthread.php?p=836704#post836704](http://ubuntuforums.org/showthread.php?p=836704#post836704)

Need to hack in the kernel...

---

