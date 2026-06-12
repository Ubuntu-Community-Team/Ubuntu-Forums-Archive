---
title: "Freeze with PATA hard disk"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by KnuX on 2007-04-13
Hi all ;)

Sometimes (too often for me), my HP 510 notebook hangs while I use it.

I'm using the latest linux-generic from Ubuntu Feisty 7.04. I tried the 2.6.21-rc6 and -mm with no success.

My dmesg is :
> [ 1481.467000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1481.467000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 1481.467000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1488.508000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1511.509000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 1511.509000] ata1: soft resetting port
[ 1511.855000] ata1.00: configured for UDMA/100
[ 1512.045000] ata1.01: configured for MWDMA2
[ 1512.045000] ata1: EH complete
[ 1512.051000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 1512.052000] sda: Write Protect is off
[ 1512.052000] sda: Mode Sense: 00 3a 00 00
[ 1512.052000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1512.053000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 1512.053000] sda: Write Protect is off
[ 1512.053000] sda: Mode Sense: 00 3a 00 00
[ 1512.054000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8675.785000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 8675.785000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 8675.785000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 8682.795000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 8705.835000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 8705.835000] ata1: soft resetting port
[ 8706.255000] ata1.00: configured for UDMA/100
[ 8706.446000] ata1.01: configured for MWDMA2
[ 8706.446000] ata1: EH complete
[ 8706.453000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 8706.456000] sda: Write Protect is off
[ 8706.456000] sda: Mode Sense: 00 3a 00 00
[ 8706.464000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8706.472000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 8706.473000] sda: Write Protect is off
[ 8706.473000] sda: Mode Sense: 00 3a 00 00
[ 8706.474000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8881.025000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 8881.025000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 8881.025000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 8888.066000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 8911.067000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 8911.067000] ata1: soft resetting port
[ 8911.413000] ata1.00: configured for UDMA/100
[ 8911.603000] ata1.01: configured for MWDMA2
[ 8911.603000] ata1: EH complete
[ 8911.609000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 8911.612000] sda: Write Protect is off
[ 8911.612000] sda: Mode Sense: 00 3a 00 00
[ 8911.612000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8911.613000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 8911.613000] sda: Write Protect is off
[ 8911.613000] sda: Mode Sense: 00 3a 00 00
[ 8911.614000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9678.324000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 9678.324000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 9678.324000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 9685.328000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 9708.352000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 9708.352000] ata1: soft resetting port
[ 9708.684000] ata1.00: configured for UDMA/100
[ 9708.874000] ata1.01: configured for MWDMA2
[ 9708.874000] ata1: EH complete
[ 9708.881000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 9708.885000] sda: Write Protect is off
[ 9708.885000] sda: Mode Sense: 00 3a 00 00
[ 9708.893000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9708.901000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 9708.902000] sda: Write Protect is off
[ 9708.902000] sda: Mode Sense: 00 3a 00 00
[ 9708.903000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10079.441000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[10079.441000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[10079.441000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[10086.447000] ata1: port is slow to respond, please be patient (Status 0xd0)
[10109.451000] ata1: port failed to respond (30 secs, Status 0xd0)
[10109.451000] ata1: soft resetting port
[10109.797000] ata1.00: configured for UDMA/100
[10109.974000] ata1.01: configured for MWDMA2
[10109.974000] ata1: EH complete
[10109.980000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[10109.986000] sda: Write Protect is off
[10109.986000] sda: Mode Sense: 00 3a 00 00
[10109.994000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10110.006000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[10110.006000] sda: Write Protect is off
[10110.006000] sda: Mode Sense: 00 3a 00 00
[10110.007000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10695.206000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[10695.206000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[10695.206000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[10702.247000] ata1: port is slow to respond, please be patient (Status 0xd0)
[10725.248000] ata1: port failed to respond (30 secs, Status 0xd0)
[10725.248000] ata1: soft resetting port
[10725.594000] ata1.00: configured for UDMA/100
[10725.784000] ata1.01: configured for MWDMA2
[10725.784000] ata1: EH complete
[10725.790000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[10725.794000] sda: Write Protect is off
[10725.794000] sda: Mode Sense: 00 3a 00 00
[10725.799000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10725.799000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[10725.800000] sda: Write Protect is off
[10725.800000] sda: Mode Sense: 00 3a 00 00
[10725.800000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[11459.198000] usb 1-1: USB disconnect, address 2
[11469.560000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[11469.560000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[11469.560000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[11476.601000] ata1: port is slow to respond, please be patient (Status 0xd0)
[11499.602000] ata1: port failed to respond (30 secs, Status 0xd0)
[11499.602000] ata1: soft resetting port
[11499.948000] ata1.00: configured for UDMA/100
[11500.138000] ata1.01: configured for MWDMA2
[11500.138000] ata1: EH complete
[11500.144000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[11500.148000] sda: Write Protect is off
[11500.148000] sda: Mode Sense: 00 3a 00 00
[11500.156000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[11500.161000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[11500.161000] sda: Write Protect is off
[11500.161000] sda: Mode Sense: 00 3a 00 00
[11500.162000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Can you give me some ideas ? :$

Thanks,
Maxime.

---

### Post by -X- on 2007-04-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Join the club, dude! I'm having the same freezing issues on my  Acer TravelMate 2480 laptop. There seems to be a launchpad about this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)

> Apr 14 15:13:48 richard-laptop kernel: [ 9282.980000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr 14 15:13:48 richard-laptop kernel: [ 9289.980000] ata1: port is slow to respond, please be patient (Status 0xd0)
Apr 14 15:13:48 richard-laptop kernel: [ 9312.996000] ata1: soft resetting port
Apr 14 15:13:48 richard-laptop kernel: [ 9313.340000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
Apr 14 15:13:48 richard-laptop kernel: [ 9313.348000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
Apr 14 15:13:48 richard-laptop kernel: [ 9313.348000] ata1.00: configured for UDMA/100
Apr 14 15:13:48 richard-laptop kernel: [ 9313.528000] ata1.01: configured for UDMA/33
Apr 14 15:13:48 richard-laptop kernel: [ 9313.528000] ata1: EH complete
Apr 14 15:13:48 richard-laptop kernel: [ 9313.536000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
Apr 14 15:13:48 richard-laptop kernel: [ 9313.536000] sda: Write Protect is off
Apr 14 15:13:48 richard-laptop kernel: [ 9313.536000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by blacksadness on 2007-04-21
hey,
it seems like i'm "almost" facing the same problems you have except that from your posts it seems your systems are already booting, in here the system just freeze, and gives these errors, i couldn't copy over the errors but i wrote down a notable line:

ata1.00: exception Emask 0x0 SAct 0x3 Serr 0x0 action 0x2 frozen


my harddrive is a 200MB samsung SATA

---

### Post by stiffme on 2007-04-21
I have the same problem, using Asus A8JM with PATA hdd.
This problem still remains with unpatched kernel from kernel.org using SATA driver

---

### Post by morphious on 2007-04-22
Same problem on ASUS A6Jc notebook @ Feisty Fawn (7.04) with 2.6.20-15-generic SMP kernel.

Some kind of solution is on the launchpad: insert disc in your CD/DVD drive. :)
Maybe after this freezes won't appear. I've just read this, so I cannot tell you, if this really works.

If anybody knows better solution to this problem, please post it here.

Greetz.

---

### Post by bartaz on 2007-04-22
@morphious
Thanks for the reply on my post in other thread.
That is exactly my problem (I have the same asus as you).

I haven't any freezes since yesterday...
Hmm.. I have a CD in drive... Lol :) So this workaround really works.

---

### Post by jafa on 2007-04-24
My machine (AMD5200+ with nVidia motherboard) has been running Edgy perfectly for months.

Feisty is giving me hard drive freeze problems (sata) - same as the OP reported.

For most people the problem will fix itself as the kernel will sot-reset the port.

For a RAID array this problem is very bad - the RAID array will detect the error and disable the hard drive (degrading the array).

```
Apr 21 23:21:06 mythtv-server kernel: [40687.894190] ata1: EH in ADMA mode, notifier 0x1 notifier_error 0x0 gen_ctl 0x1501000 status
 0x1540 next cpb count 0x0 next cpb idx 0x0
Apr 21 23:21:06 mythtv-server kernel: [40687.894195] ata1: CPB 0: ctl_flags 0xd, resp_flags 0x1
Apr 21 23:21:06 mythtv-server kernel: [40687.894228] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 21 23:21:06 mythtv-server kernel: [40687.894234] ata1.00: cmd ca/00:70:bf:50:af/00:00:00:00:00/e6 tag 0 cdb 0x0 data 57344 out
Apr 21 23:21:06 mythtv-server kernel: [40687.894235]          res 40/00:00:00:50:28/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 21 23:21:06 mythtv-server kernel: [40687.894255] sd 1:0:0:0: SCSI error: return code = 0x06000000
Apr 21 23:21:06 mythtv-server kernel: [40687.894257] end_request: I/O error, dev sdb, sector 112152879
Apr 21 23:21:06 mythtv-server kernel: [40687.894261] raid5: Disk failure on sdb1, disabling device. Operation continuing on 3 device
s
Apr 21 23:21:06 mythtv-server kernel: [40687.894272] sd 1:0:0:0: SCSI error: return code = 0x06000000
Apr 21 23:21:06 mythtv-server kernel: [40687.894274] end_request: I/O error, dev sdb, sector 112153151
Apr 21 23:21:06 mythtv-server kernel: [40688.016595] ata1: soft resetting port
Apr 21 23:21:07 mythtv-server kernel: [40688.076470] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 21 23:21:07 mythtv-server kernel: [40688.079610] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Apr 21 23:21:07 mythtv-server kernel: [40688.082673] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Apr 21 23:21:07 mythtv-server kernel: [40688.082676] ata1.00: configured for UDMA/133
Apr 21 23:21:07 mythtv-server kernel: [40688.082685] ata1: EH complete
Apr 21 23:21:07 mythtv-server kernel: [40688.083430] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Apr 21 23:21:07 mythtv-server kernel: [40688.083692] sda: Write Protect is off
Apr 21 23:21:07 mythtv-server kernel: [40688.083694] sda: Mode Sense: 00 3a 00 00
Apr 21 23:21:07 mythtv-server kernel: [40688.090087] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO
 or FUA
Apr 21 23:21:07 mythtv-server kernel: [40688.098056] RAID5 conf printout:
Apr 21 23:21:07 mythtv-server kernel: [40688.098059]  --- rd:4 wd:3
Apr 21 23:21:07 mythtv-server kernel: [40688.098062]  disk 0, o:0, dev:sdb1
Apr 21 23:21:07 mythtv-server kernel: [40688.098063]  disk 1, o:1, dev:sdc1
Apr 21 23:21:07 mythtv-server kernel: [40688.098065]  disk 2, o:1, dev:sdd1
Apr 21 23:21:07 mythtv-server kernel: [40688.098066]  disk 3, o:1, dev:sda1
Apr 21 23:21:07 mythtv-server kernel: [40688.102562] RAID5 conf printout:
Apr 21 23:21:07 mythtv-server kernel: [40688.102564]  --- rd:4 wd:3
Apr 21 23:21:07 mythtv-server kernel: [40688.102565]  disk 1, o:1, dev:sdc1
Apr 21 23:21:07 mythtv-server kernel: [40688.102567]  disk 2, o:1, dev:sdd1
Apr 21 23:21:07 mythtv-server kernel: [40688.102568]  disk 3, o:1, dev:sda1
Apr 21 23:21:07 mythtv-server mdadm: Fail event detected on md device /dev/md0, component device /dev/sdb1
```

The hard drive passed all tests but I replaced the hard drive just to be sure.

Within a few hours I had two more of errors:

```
[13366.577329] ata3: EH in ADMA mode, notifier 0x1 notifier_error 0x0 gen_ctl 0x1501000 status 0x1540 next cpb count 0x0 next cpb id
x 0x0
[13366.577335] ata3: CPB 0: ctl_flags 0xd, resp_flags 0x1
[13366.577393] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[13366.577398] ata3.00: cmd ca/00:18:3f:0b:fa/00:00:00:00:00/e6 tag 0 cdb 0x0 data 12288 out
[13366.577400]          res 40/00:00:06:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[13366.697074] ata3: soft resetting port
[13366.756948] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[13366.760088] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[13366.763147] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[13366.763150] ata3.00: configured for UDMA/133
[13366.763158] ata3: EH complete
[13366.763298] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[13366.763350] sdc: Write Protect is off
[13366.763352] sdc: Mode Sense: 00 3a 00 00
[13366.766816] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Nick

---

### Post by jafa on 2007-04-24
Found the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

Nick

---

### Post by kiev on 2008-05-24
This kernel bug
 this problem already whole year

for me she showed up one time in the floor of hour, however as a result of this problem I lost a mysql database - mysql innodb not start - "Accertion error" - did not help even "innodb_force_recovery = 4", backup was an a week remoteness - the works of whole department lost data for a few days, the management simply in shock - I going to discharge from job (((

this problem already whole year:
-----------
I'm stumped trying to track down the below intermittent problem.....
I've confirmed this problem on 2.6.19, 2.6.20 and 2.6.21.
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765)
[http://kerneltrap.org/node/16175](http://kerneltrap.org/node/16175)
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

SUSE:

ata errors, system freeze
[https://bugzilla.novell.com/show_bug.cgi?id=393675](https://bugzilla.novell.com/show_bug.cgi?id=393675)

System lockup with concurrent acces to SATA disks on Promise PDC20378
[http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html](http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html)

Kernel panic / system hang / sata_promise
[https://bugzilla.novell.com/show_bug.cgi?id=350907](https://bugzilla.novell.com/show_bug.cgi?id=350907)

DELL Poweredge 2970 hangs sometimes (ata1)
[https://bugzilla.novell.com/show_bug.cgi?id=359333](https://bugzilla.novell.com/show_bug.cgi?id=359333)

Fedora:
ata device crashing system in Fedora 8
[http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html](http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html)

problème de mise à jour
[http://forums.fedora-fr.org/viewtopic.php?pid=253930](http://forums.fedora-fr.org/viewtopic.php?pid=253930)

Kernel 2.6.24.x boot problem - Anyone , Any idea
[http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10](http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10)

Thought though with the newest hard drive with support of NCQ such is not present, ... also same:

"With this kernel I’m getting frequent temporary freezes (system comes back responsive after a minute or so…)."
[http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296](http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296)

---

### Post by blacknymph on 2008-06-02
Ubuntu 8.04 Hardy Heron
Lenovo 3000 N200 laptop

```
ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
ata1.00: tag 0 cmd 0x60 Emask 0x4 stat 0x40 err 0x0 (timeout)
ata1: hard resetting port
ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
ata2.00: tag 0 cmd 0x60 Emask 0x4 stat 0x40 err 0x0 (timeout)
ata2: hard resetting port
ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
ata4.00: tag 0 cmd 0x60 Emask 0x4 stat 0x40 err 0x0 (timeout)
ata4.00: tag 1 cmd 0x60 Emask 0x4 stat 0x40 err 0x0 (timeout)
```

how fix?

---

