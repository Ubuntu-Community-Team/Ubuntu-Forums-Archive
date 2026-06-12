---
title: "Tape Drive Problems with Version 7.04"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by ronWI on 2007-09-10
I am looking at upgrading my system which uses an STT20000A drive attached to a primary ide for backup. The drive works fine with Version 6.10 where it shows up as /dev/ht0, but not with 7.04 where it is showing up as st0.  Any ideas?

Here's some 7.04 data:
----------------------------------------------------------------------------
uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

Here's the drive setup info from dmesg:
[   76.005252] scsi 2:0:1:0: Sequential-Access Seagate  STT20000A        8A51 PQ: 0 ANSI: 2
[   76.014120] st: Version 20061107, fixed bufsize 32768, s/g segs 256
[   76.015469] st 2:0:1:0: Attached scsi tape st0
[   76.015473] st 2:0:1:0: st0: try direct i/o: yes (alignment 512 B)
[   76.021518] scsi 0:1:0:0: Attached scsi generic sg0 type 0
[   76.021644] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   76.021767] st 2:0:1:0: Attached scsi generic sg2 type 1

And if I try mt:

mt -f /dev/st0 status
mt: /dev/st0: Input/output error

And here's the error from dmesg:
[  981.013047] st0: Error 40000 (sugg. bt 0x0, driver bt 0x0, host bt 0x4).

Here's the same data from 6.10:
----------------------------------------------------------------------------
 uname -a
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Here's the drive setup info from dmesg:
[17179575.748000] Probing IDE interface ide0...
[17179576.420000] hdb: Seagate STT20000A, ATAPI TAPE drive
[17179576.476000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
...
[17179618.192000] ide-tape: hdb <-> ht0: Seagate STT20000A rev 8A51
[17179618.204000] ide-tape: hdb <-> ht0: 1000KBps, 6*54kB buffer, 9720kB pipeline, 108ms tDSC

Here's successful mt command:
 mt -f /dev/ht0 status
drive type = Generic SCSI-2 tape
drive status = 512
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 512 bytes. Density code 0x0 (default).
Soft error count since last status=0
General status bits on (0):

---

