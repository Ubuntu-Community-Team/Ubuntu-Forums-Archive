---
title: "Slow Boot due to Via RAID Card PATA Timeouts?"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by mevans336 on 2008-03-16
Hello all,

I've got 7.10 configured with Virtualbox seamless and I'm extremely happy with my installation, however, I've got one nagging problem I'm hoping someone here can help me with.

When I boot (this is any distro btw, not just Ubuntu), the kernel throws the following errors:```

Mar 13 10:39:43 Axon kernel: [   44.628000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Mar 13 10:39:43 Axon kernel: [   49.668000] ata7: port is slow to respond, please be patient (Status 0xd0)
Mar 13 10:39:43 Axon kernel: [   54.652000] ata7: device not ready (errno=-16), forcing hardreset
Mar 13 10:39:43 Axon kernel: [   54.652000] ata7: soft resetting port
Mar 13 10:39:43 Axon kernel: [   55.144000] ata7.00: configured for UDMA/33
Mar 13 10:39:43 Axon kernel: [   55.144000] ata7: EH complete
Mar 13 10:39:43 Axon kernel: [   85.144000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Mar 13 10:39:43 Axon kernel: [   90.184000] ata7: port is slow to respond, please be patient (Status 0xd0)
Mar 13 10:39:43 Axon kernel: [   95.168000] ata7: device not ready (errno=-16), forcing hardreset
Mar 13 10:39:43 Axon kernel: [   95.168000] ata7: soft resetting port
Mar 13 10:39:43 Axon kernel: [   95.660000] ata7.00: configured for UDMA/33
Mar 13 10:39:43 Axon kernel: [   95.660000] ata7: EH complete
Mar 13 10:39:43 Axon kernel: [  125.660000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Mar 13 10:39:43 Axon kernel: [  130.700000] ata7: port is slow to respond, please be patient (Status 0xd0)
Mar 13 10:39:43 Axon kernel: [  135.684000] ata7: device not ready (errno=-16), forcing hardreset
Mar 13 10:39:43 Axon kernel: [  135.684000] ata7: soft resetting port
Mar 13 10:39:43 Axon kernel: [  136.176000] ata7.00: configured for UDMA/33
Mar 13 10:39:43 Axon kernel: [  136.176000] ata7: EH complete
Mar 13 10:39:43 Axon kernel: [  165.896000] usb 2-3: USB disconnect, address 2
Mar 13 10:39:43 Axon kernel: [  165.896000] eth1: unregister 'rndis_host' usb-0000:00:02.0-3, RNDIS device
Mar 13 10:39:43 Axon kernel: [  166.176000] ata7.00: limiting speed to UDMA/25:PIO4
Mar 13 10:39:43 Axon kernel: [  166.176000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Mar 13 10:39:43 Axon kernel: [  171.216000] ata7: port is slow to respond, please be patient (Status 0xd0)
Mar 13 10:39:43 Axon kernel: [  176.200000] ata7: device not ready (errno=-16), forcing hardreset
Mar 13 10:39:43 Axon kernel: [  176.200000] ata7: soft resetting port
Mar 13 10:39:43 Axon kernel: [  176.692000] ata7.00: configured for UDMA/25
Mar 13 10:39:43 Axon kernel: [  176.692000] ata7: EH complete

```

As you can see, it takes FOREVER to initialize this device.

ATA7 is a PATA CDRW attached to a PCI Via PATA/SATA RAID card.

```

Mar 13 10:39:43 Axon kernel: [    7.160000] sata_via 0000:01:06.0: routed to hard irq line 5
Mar 13 10:39:43 Axon kernel: [    7.160000] scsi5 : sata_via
Mar 13 10:39:43 Axon kernel: [    7.160000] scsi6 : sata_via
Mar 13 10:39:43 Axon kernel: [    7.160000] scsi7 : sata_via
Mar 13 10:39:43 Axon kernel: [    8.636000] ata7.00: ATAPI: HL-DT-ST GCE-8481B, C102, max UDMA/33
Mar 13 10:39:43 Axon kernel: [    8.808000] ata7.00: configured for UDMA/33[

```

Any ideas how I can resolve this? I have the PATA CDRW and a SATA DVD-R attached to the PCI card, nothing else. Could it be because it's using the sata_via module for a PATA CDRW?

Here's what lspci shows for the Via controller:

```

01:06.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

```

Thanks!

---

### Post by RaZoR1394 on 2008-04-08
I have a very similar problem (if not the same) with the a card of the same model (VIA VT6421) and revision (50). In my case I'm only using the eSATA port in the back and an SATA-eSATA bridge connected to the only internal SATA port.

> 
[ 159.515749] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 159.515797] ata7.00: BMDMA stat 0x4
[ 159.515841] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 159.515889] ata7.00: cmd c8/00:20:47:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 159.515891] res 51/84:00:66:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 159.515945] ata7.00: status: { DRDY ERR }
[ 159.515988] ata7.00: error: { ICRC ABRT }
[ 159.824404] ata7: soft resetting link
[ 159.980397] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 160.004738] ata7.00: configured for UDMA/33
[ 160.004742] ata7: EH complete
[ 160.513735] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 160.513783] ata7.00: BMDMA stat 0x4
[ 160.513827] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 160.513875] ata7.00: cmd c8/00:20:47:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 160.513877] res 51/84:00:66:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 160.513931] ata7.00: status: { DRDY ERR }
[ 160.513974] ata7.00: error: { ICRC ABRT }
[ 160.824268] ata7: soft resetting link
[ 160.980261] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 161.038113] ata7.00: configured for UDMA/33
[ 161.038117] ata7: EH complete
[ 161.545057] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 161.545105] ata7.00: BMDMA stat 0x4
[ 161.545149] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 161.545205] ata7.00: cmd c8/00:20:47:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 161.545206] res 51/84:00:66:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 161.545260] ata7.00: status: { DRDY ERR }
[ 161.545304] ata7.00: error: { ICRC ABRT }
[ 161.856127] ata7: soft resetting link
[ 162.012119] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 162.053986] ata7.00: configured for UDMA/33
[ 162.053990] ata7: EH complete
[ 162.565224] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 162.565273] ata7.00: BMDMA stat 0x5
[ 162.565318] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 162.565367] ata7.00: cmd c8/00:20:47:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 162.565368] res 51/84:20:47:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 162.565422] ata7.00: status: { DRDY ERR }
[ 162.565465] ata7.00: error: { ICRC ABRT }
[ 162.875987] ata7: soft resetting link
[ 163.031979] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 163.072283] ata7.00: configured for UDMA/33
[ 163.072288] ata7: EH complete
[ 163.086069] sd 6:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[ 163.086079] sd 6:0:0:0: [sdc] Write Protect is off
[ 163.086081] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 163.086093] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 163.086106] sd 6:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[ 163.086114] sd 6:0:0:0: [sdc] Write Protect is off
[ 163.086116] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 163.086128] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 163.629737] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 163.629785] ata7.00: BMDMA stat 0x4
[ 163.629831] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 163.629880] ata7.00: cmd c8/00:07:80:7b:fc/00:00:00:00:00/e6 tag 0 dma 3584 in
[ 163.629881] res 51/84:00:86:7b:fc/00:00:00:00:00/e6 Emask 0x12 (ATA bus error)
[ 163.629936] ata7.00: status: { DRDY ERR }
[ 163.629979] ata7.00: error: { ICRC ABRT }
[ 163.939841] ata7: soft resetting link
[ 164.095833] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 164.120170] ata7.00: configured for UDMA/33
[ 164.120175] ata7: EH complete
[ 164.660987] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 164.661035] ata7.00: BMDMA stat 0x4
[ 164.661081] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 164.661130] ata7.00: cmd c8/00:07:80:7b:fc/00:00:00:00:00/e6 tag 0 dma 3584 in
[ 164.661131] res 51/84:00:86:7b:fc/00:00:00:00:00/e6 Emask 0x12 (ATA bus error)
[ 164.661184] ata7.00: status: { DRDY ERR }
[ 164.661228] ata7.00: error: { ICRC ABRT }
[ 164.971700] ata7: soft resetting link
[ 165.127691] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 165.152018] ata7.00: configured for UDMA/33
[ 165.152023] ata7: EH complete
[ 165.176286] sd 6:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[ 165.176295] sd 6:0:0:0: [sdc] Write Protect is off
[ 165.176297] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 165.176310] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 165.176322] sd 6:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[ 165.176330] sd 6:0:0:0: [sdc] Write Protect is off
[ 165.176332] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 165.176344] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 165.714424] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 165.714473] ata7.00: BMDMA stat 0x4
[ 165.714518] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 165.714567] ata7.00: cmd c8/00:27:d0:df:00/00:00:00:00:00/e0 tag 0 dma 19968 in
[ 165.714569] res 51/84:00:f6:df:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 165.714623] ata7.00: status: { DRDY ERR }
[ 165.714667] ata7.00: error: { ICRC ABRT }
[ 166.023556] ata7: soft resetting link
[ 166.179547] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 166.203884] ata7.00: configured for UDMA/33
[ 166.203889] ata7: EH complete
[ 166.211563] sd 6:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[ 166.211573] sd 6:0:0:0: [sdc] Write Protect is off
[ 166.211575] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 166.211588] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 166.723501] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 166.723550] ata7.00: BMDMA stat 0x5
[ 166.723596] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 166.723645] ata7.00: cmd c8/00:80:67:00:00/00:00:00:00:00/e0 tag 0 dma 65536 in
[ 166.723647] res 51/84:80:67:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 166.723701] ata7.00: status: { DRDY ERR }
[ 166.723745] ata7.00: error: { ICRC ABRT }
[ 167.035427] ata7: soft resetting link
[ 167.191408] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 167.215720] ata7.00: configured for UDMA/33
[ 167.215724] ata7: EH complete
[ 167.721487] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 167.721535] ata7.00: BMDMA stat 0x5
[ 167.721582] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 167.721630] ata7.00: cmd c8/00:80:67:00:00/00:00:00:00:00/e0 tag 0 dma 65536 in
[ 167.721631] res 51/84:80:67:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 167.721685] ata7.00: status: { DRDY ERR }
[ 167.721729] ata7.00: error: { ICRC ABRT }
[ 168.032288] ata7: soft resetting link
[ 168.187277] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 168.211590] ata7.00: configured for UDMA/33
[ 168.211599] ata7: EH complete
[ 168.357841] skge eth1: enabling interface
[ 168.362485] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 168.578336] ppdev: user-space parallel port driver
[ 168.719489] ata7.00: exception Emask 0x12 SAct 0x0 SErr 0x1380500 action 0x2
[ 168.719550] ata7.00: BMDMA stat 0x5
[ 168.719597] ata7: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
[ 168.719646] ata7.00: cmd c8/00:80:67:00:00/00:00:00:00:00/e0 tag 0 dma 65536 in
[ 168.719647] res 51/84:80:67:00:00/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
[ 168.719702] ata7.00: status: { DRDY ERR }
[ 168.719746] ata7.00: error: { ICRC ABRT }
[ 168.790565] audit(1207680967.457:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=7005 profile="/usr/sbin/cupsd" namespace="default"
[ 169.032152] ata7: soft resetting link
[ 169.188138] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 169.212495] ata7.00: configured for UDMA/33
[ 169.212507] ata7: EH complete 


That was taken from dmesg once I managed to boot up with an eSATA HDD connected to the VIA card. Most times it takes very long to boot but sometimes it also locks up or reboots all by itself. With no eSATA drives connected to the card the computer always boots normally. Windows is having similar problems on this machine. May I add that I have tried 3 different eSATA harddrives?

I have the same model on another computer and 2 of them. The old one was working great until I inserted the new one. Now none of the eSATA ports of the two VIA cards seem to work and I'm missing one internal hard drive in dmesg, probably the one connected to the VIA card.

On the first computer I have checked with Windows if there are any IRQ problems with the VIA card but there are none. I have also tried these switches under Ubuntu to try to get around the problem:

> 
pci=routeirq, irqpoll, pci=noacpi


edit:

What motherboard do you have may I ask? I have a DFI NF4 Ultra-D in each of my machines with what I guess is the latest unofficial bios. I'm wondering if the bios on the VIA card is giving problems and if It's possible to update it.

---

### Post by kiev on 2008-05-23
This is kernel bug - anyone any idea
and not first year!!!
I think the unique decision - to use old IDE hard drive

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

---

