---
title: "Is my HDD failing?"
date: 2013-12-29
forum: Hardware
---

### Post by Manuj19 on 2013-12-29
This problem starts when centos crashed without any reason and when i tried to restart there was some error...
So i wiped the HDD assuming it as a kernel bug and install xubuntu 12.04.3 LTS. Install work fine but after one day system crash again
and when i reboot i got a message like

> 
Hd0 removed from stack
grub rescue >

So i again start with live cd and it takes around 5 minutes to boot with the following error in backend
```

 ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 3592.964750] ata1.00: irq_stat 0x40000008
[ 3592.964760] ata1.00: failed command: READ FPDMA QUEUED
[ 3592.964779] ata1.00: cmd 60/08:00:08:b5:1e/00:00:00:00:00/40 tag 0 ncq 4096 in
[ 3592.964783]          res 41/40:00:0e:b5:1e/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[ 3592.964793] ata1.00: status: { DRDY ERR }
[ 3592.964800] ata1.00: error: { UNC }
[ 3592.979867] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 3592.980916] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 3592.980928] ata1.00: configured for UDMA/133
[ 3592.980960] ata1: EH complete
[ 3595.941793] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 3595.941801] ata1.00: irq_stat 0x40000008
[ 3595.941808] ata1.00: failed command: READ FPDMA QUEUED
[ 3595.941816] ata1.00: cmd 60/08:00:08:b5:1e/00:00:00:00:00/40 tag 0 ncq 4096 in
[ 3595.941818]          res 41/40:00:0e:b5:1e/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[ 3595.941822] ata1.00: status: { DRDY ERR }
[ 3595.941826] ata1.00: error: { UNC }
[ 3595.956954] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd


```
and the error keeps on repeating

The output of **Smart Test** is as follows
```

smartctl -l selftest /dev/sda 
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-52-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      9400         2010321
# 2  Extended offline    Completed: read failure       90%      9400         2010321
# 3  Short offline       Completed: read failure       90%      9398         2010321
# 4  Extended offline    Completed: read failure       90%      9398         2010321
# 5  Extended offline    Completed: read failure       90%      9398         2010321
# 6  Extended offline    Completed without error       00%      8109         -
# 7  Extended offline    Completed without error       00%      5174         -
# 8  Extended offline    Interrupted (host reset)      80%      4404         -
# 9  Extended offline    Completed without error       00%       163         -
#10  Extended offline    Aborted by host               80%       162         -
#11  Extended offline    Aborted by host               90%       162         -
#12  Extended offline    Aborted by host               90%       162         -
#13  Extended offline    Aborted by host               90%       162         -
#14  Short offline       Completed without error       00%       157         -
#15  Short offline       Completed without error       00%        89         -

```

Output of **fdisk -lu /dev/sda**
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc236

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046     2000895      999425    5  Extended
/dev/sda2   *     2000896    41945087    19972096   83  Linux
/dev/sda3        41945088    73402367    15728640    7  HPFS/NTFS/exFAT
/dev/sda4        73402368   234436607    80517120    7  HPFS/NTFS/exFAT
/dev/sda5            2048     2000895      999424   82  Linux swap / Solaris

Output of **badblocks /dev/sda**
```

1005132
1005133
1005134
1005135
1005140
1005141
1005142
1005143
1005160
1005161
1005162
1005163
1005660
1005661
1005662
1005663
1005788
1005789
1005790
1005791
1005884
1005885
1005896
1005897
1005898
1005899
1005976
1005977
1005978
1005979
1006044
1006045
1006046
1006047
1006056
1006057
1006058
1006059
1006212
1006213
1006214
1006215
1006216
1006217
1006218
1006219
1006360
1006361
1006362
1006363
1006392
1006393
1006394
1006395
1006480
1006481
1006482
1006483
1006528
1006529
1006530
1006531
1007252
1007253
1007254
1007255
1007464
1007465
1007466
1007467
1007724
1007725
1007726
1007727
1007736
1007737
1007738
1007739
1007740
1007741
1007742
1007743
This is still running

```

---

### Post by sudodus on 2013-12-29
You seem to have many bad blocks, and not only in one group next to each other :-(

Since this happened the day after installation, there is not much personal data to be saved. Have all of most of the bad blocks turned bad recently? In that case I think the drive is failing rapidly. Otherwise a drive can live with bad blocks, that are marked to avoid using them. See

```
man e2fsck
```

```
       -c     This  option  causes  e2fsck  to  use badblocks(8) program to do a read-only scan of the
              device in order to find any bad blocks.  If any bad blocks are found, they are added  to
              the  bad  block  inode  to prevent them from being allocated to a file or directory.  If
              this option is specified twice, then the bad block  scan  will  be  done  using  a  non-
              destructive read-write test.

```

So it might help to run

```
sudo e2fsck -cf /dev/sda
```

if the number of bad blocks is stable.

---

