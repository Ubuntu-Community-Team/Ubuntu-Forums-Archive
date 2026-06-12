---
title: "ATA issues SuperMicro ubuntu 20.04"
date: 2022-11-28
forum: Hardware
---

### Post by driesmelkebeke on 2022-11-28
Hi

Since a couple weeks we've been having issues with a couple servers running Ubuntu 20.04. Our systems have 2 SATA ssd's running in software RAID1 (MDADM) and 2 NVME disks running databases.
We've had 2 identical incidents on 2 identical servers where the system went into read-only mode. The latest system logs show the following:

First we get a ATA2 exception
```

[TABLE]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744322] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744394] ata2.00: failed command: WRITE DMA EXT[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744434] ata2.00: cmd 35/00:c8:60:61:68/00:01:1c:00:00/e0 tag 18 dma 233472 out[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744434]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744549] ata2.00: status: { DRDY }[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744582] ata2: hard resetting link[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[/TABLE]

```
After this the other disk seems to also write the same error to the other disk
```

[TABLE]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744598] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744670] ata1.00: failed command: WRITE DMA EXT[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744709] ata1.00: cmd 35/00:c0:a0:5b:68/00:05:1c:00:00/e0 tag 14 dma 753664 out[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744709]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744821] ata1.00: status: { DRDY }[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047348.744864] ata1: hard resetting link[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[/TABLE]

```
Then the system tries to recover itself but fails
```

[TABLE]
[TR]
[TD][TABLE]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745297] ata2: reset failed, giving up[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745332] ata2.00: disabled[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745358] ata2: EH complete[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745415] sd 1:0:0:0: [sdb] tag#5 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745429] sd 1:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 1c 68 63 28 00 00 18 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745434] blk_update_request: I/O error, dev sdb, sector 476603176 op 0x1:(WRITE) flags 0x0 phys_seg 3 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745975] sd 1:0:0:0: [sdb] tag#6 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=90s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745988] sd 1:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 1c 68 61 60 00 01 c8 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.745992] blk_update_request: I/O error, dev sdb, sector 476602720 op 0x1:(WRITE) flags 0x0 phys_seg 57 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746025] ata1: softreset failed (1st FIS failed)[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746439] ata1: reset failed, giving up[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746474] ata1.00: disabled[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746585] sd 1:0:0:0: [sdb] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746639] sd 1:0:0:0: [sdb] tag#15 CDB: Write(10) 2a 00 0b 10 7d a8 00 00 30 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746649] blk_update_request: I/O error, dev sdb, sector 185630120 op 0x1:(WRITE) flags 0x0 phys_seg 5 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746732] ata1: EH complete[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746794] sd 1:0:0:0: [sdb] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746799] sd 1:0:0:0: [sdb] tag#19 CDB: Write(10) 2a 00 1b d0 90 10 00 00 08 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746801] blk_update_request: I/O error, dev sdb, sector 466653200 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746806] sd 0:0:0:0: [sda] tag#4 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746884] sd 0:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 1c 68 61 60 00 01 e0 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746888] blk_update_request: I/O error, dev sda, sector 476602720 op 0x1:(WRITE) flags 0x0 phys_seg 60 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.746962] sd 1:0:0:0: [sdb] tag#20 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747189] sd 1:0:0:0: [sdb] tag#20 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747194] blk_update_request: I/O error, dev sdb, sector 4112 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747282] md: super_written gets error=-5[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747318] md/raid1:md0: Disk failure on sdb2, disabling device.[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747318] md/raid1:md0: Operation continuing on 1 devices.[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747426] sd 0:0:0:0: [sda] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=90s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747473] sd 0:0:0:0: [sda] tag#15 CDB: Write(10) 2a 00 1c 68 5b a0 00 05 c0 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.747476] blk_update_request: I/O error, dev sda, sector 476601248 op 0x1:(WRITE) flags 0x0 phys_seg 168 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748144] sd 0:0:0:0: [sda] tag#14 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748181] sd 0:0:0:0: [sda] tag#14 CDB: Write(10) 2a 00 0b 10 7d a8 00 00 30 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748186] blk_update_request: I/O error, dev sda, sector 185630120 op 0x1:(WRITE) flags 0x0 phys_seg 5 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748443] sd 0:0:0:0: [sda] tag#21 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748484] sd 0:0:0:0: [sda] tag#21 CDB: Write(10) 2a 00 1b d0 90 10 00 00 c0 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748490] blk_update_request: I/O error, dev sda, sector 466653200 op 0x1:(WRITE) flags 0x800 phys_seg 24 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748901] sd 0:0:0:0: [sda] tag#22 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK cmd_age=0s[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748906] sd 0:0:0:0: [sda] tag#22 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748911] blk_update_request: I/O error, dev sda, sector 4112 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.748991] md: super_written gets error=-5[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica Neue][COLOR=#000000][COLOR=#000000][FONT=&amp][3047408.749099] md: super_written gets error=-5[/FONT][/COLOR][/COLOR][/FONT][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```
Our ubuntu systems are running on SuperMicro servers running Ubuntu 20.04.
More info about the system:

CPU: AMD EPYC 7542 32-Core Processor
DISKS and layout:
```
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTsda           8:0    0 447.1G  0 disk
&#9500;&#9472;sda1        8:1    0   1.1G  0 part  /boot/efi
&#9492;&#9472;sda2        8:2    0   440G  0 part
  &#9492;&#9472;md0       9:0    0 439.9G  0 raid1
    &#9492;&#9472;md0p1 259:8    0 439.9G  0 part  /
sdb           8:16   0 447.1G  0 disk
&#9500;&#9472;sdb1        8:17   0   1.1G  0 part
&#9492;&#9472;sdb2        8:18   0   440G  0 part
  &#9492;&#9472;md0       9:0    0 439.9G  0 raid1
    &#9492;&#9472;md0p1 259:8    0 439.9G  0 part  /
nvme0n1     259:0    0   7.3T  0 disk
&#9492;&#9472;nvme0n1p1 259:1    0   7.3T  0 part
  &#9492;&#9472;md127     9:127  0   7.3T  0 raid1 /mnt/storage1
nvme1n1     259:2    0   7.3T  0 disk
&#9492;&#9472;nvme1n1p1 259:3    0   7.3T  0 part
  &#9492;&#9472;md127     9:127  0   7.3T  0 raid1 /mnt/storage1
nvme3n1     259:4    0   7.3T  0 disk
&#9492;&#9472;nvme3n1p1 259:7    0   7.3T  0 part
  &#9492;&#9472;md126     9:126  0   7.3T  0 raid1 /mnt/storage2
nvme2n1     259:5    0   7.3T  0 disk
&#9492;&#9472;nvme2n1p1 259:6    0   7.3T  0 part
  &#9492;&#9472;md126     9:126  0   7.3T  0 raid1 /mnt/storage
```

BIOS version 2.0
Kernel version: 5.15.0-53-generic

Any help is appreciated

---

### Post by ActionParsnip on 2022-11-28
Make sure you have the latest BIOS. This may help.

---

### Post by driesmelkebeke on 2022-11-28
The same issue happens on BIOS versions 2.0, 2.2, 2.3 and 2.4 (latest).

---

### Post by slickymaster on 2022-11-28
*Thread moved to **Hardware**.*

---

