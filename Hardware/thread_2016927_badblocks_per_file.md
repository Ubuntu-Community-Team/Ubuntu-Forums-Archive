---
title: "badblocks per file ?"
date: 2012-07-04
forum: Hardware
---

### Post by juju43 on 2012-07-04
Hello,

from time to time, I have some I/O problems (mostly rsync io timeout) with an USB external disk.
It's not possible to use smartmon on it and fsck is normal (even if forced).
I tried badblocks tool but, as it is a 1TB disk, it takes ages ... would probably need 3 or 4 days to finish (i'm on a netbook ...)

as I have a list of file possibly bad (rsync failing with them, not if exclude), I'm looking to first check those file. I've looked at the following links:

[http://serverfault.com/questions/29886/how-do-i-list-a-files-data-blocks-on-linux](http://serverfault.com/questions/29886/how-do-i-list-a-files-data-blocks-on-linux)
[http://computer-forensics.sans.org/blog/2010/12/20/digital-forensics-understanding-ext4-part-1-extents](http://computer-forensics.sans.org/blog/2010/12/20/digital-forensics-understanding-ext4-part-1-extents)

[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html) 
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

```

$ sudo debugfs -R "stat /etc/passwd" /dev/sda6
[sudo] password for julien: 
debugfs 1.41.14 (22-Dec-2010)
Inode: 3673222   Type: regular    Mode:  0644   Flags: 0x80000
Generation: 3568479395    Version: 0x00000000:00000001
User:     0   Group:     0   Size: 1715
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 8
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x4fc021f1:3c73a448 -- Fri May 25 20:21:05 2012
 atime: 0x4ff3bd69:1b8ea810 -- Tue Jul  3 23:50:01 2012
 mtime: 0x4fc021f1:34d286b0 -- Fri May 25 20:21:05 2012
crtime: 0x4fc021f1:34d286b0 -- Fri May 25 20:21:05 2012
Size of extra inode fields: 28
EXTENTS:
(0):14714406

```Problem, it's ext4 with extents and not blocks so can't use for "badblocks <device> <last_block> <start_block>"

also on the real problematic files, I get
```

$ sudo debugfs -R "stat /home/user/Images/20120603/20120603_084829--DSC_0662.JPG.bad" /dev/sdc1
debugfs 1.41.14 (22-Dec-2010)
/home/user/Images/20120603/20120603_084829--DSC_0662.JPG.bad: File not found by ext2_lookup

```so is there a way to check badblocks on one file ? else what could cause a io timeout for rsync ? (rest of Internet connexion http/ssh working normally)

Thanks a lot.

---

### Post by ahallubuntu on 2012-07-04
Run smartctl (part of smartmontools) on it to check the S.M.A.R.T. status.

smartmontools does have trouble automatically recognizing the chipset of some external USB drives, but if you can figure out (or just guess) the chipset, you can perhaps coax it to report Attributes:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

For example, instead of typing

sudo smartctl -a /dev/sda

try

sudo smartctl -a -d sat /dev/sda

(or something else instead of "-d sat" - depending on the chipset).

Sometimes adding "-T permissive" also helps it read S.M.A.R.T.

---

### Post by juju43 on 2012-07-05
Thanks. That's it for smartctl. doesn't look good ...

```

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-21-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10TMVW-11ZSMS1
Serial Number:    WD-WXK1A11P5834
LU WWN Device Id: 5 0014ee 103f0086d
Firmware Version: 01.01A01
User Capacity:    1 000 204 886 016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Jul  5 08:15:30 2012 CLT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (25080) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 244) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   169   169   051    Pre-fail  Always       -       13493
  3 Spin_Up_Time            0x0027   174   163   021    Pre-fail  Always       -       4291
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1427
  5 Reallocated_Sector_Ct   0x0033   195   195   140    Pre-fail  Always       -       42
  7 Seek_Error_Rate         0x002e   200   196   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4561
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       623
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       120
193 Load_Cycle_Count        0x0032   176   176   000    Old_age   Always       -       72693
194 Temperature_Celsius     0x0022   127   097   000    Old_age   Always       -       23
196 Reallocated_Event_Count 0x0032   197   197   000    Old_age   Always       -       3
197 Current_Pending_Sector  0x0032   200   001   000    Old_age   Always       -       129
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      4553         11737672
# 2  Short offline       Completed: read failure       90%      4553         11737672

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```Those page gave indications to reallocate but not sure if it applies well to ext4 and if it's not better buying a new disk.
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
[http://nwsmith.blogspot.com/2007/08/smartmontools-and-fixing-unreadable.html](http://nwsmith.blogspot.com/2007/08/smartmontools-and-fixing-unreadable.html)

I did the beginning of the process but not sure of result
```

$ sudo fdisk -lu /dev/sdc

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 têtes, 63 secteurs/piste, 121597 cylindres, total 1953458176 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00042ada

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdc1            2048  1748658175   874328064   83  Linux
/dev/sdc2      1748658176  1851058175    51200000    7  HPFS/NTFS/exFAT
/dev/sdc3      1851058176  1953458175    51200000   83  Linux
$ sudo tune2fs -l /dev/sdc1 | grep Block
Block count:              218582016
Block size:               4096
Blocks per group:         32768
=>
math: lba_first_error - partition_start_block * units size/block size
    11737672-2048 * 512/4096 = 1466953
$ sudo debugfs /dev/sdc1
debugfs 1.41.14 (22-Dec-2010)
debugfs:  icheck 1466953
Block   Inode number
1466953 264815
debugfs:  ncheck 264815
Inode   Pathname
264815  /Images/20111230/20111230_105148--DSC_0271.NEF
debugfs:  icheck 264815
Block   Inode number
264815  263596
debugfs:  quit
$ md5sum ~/Images/20111230/20111230_105148--DSC_0271.NEF
md5sum: /home/julien/Images/20111230/20111230_105148--DSC_0271.NEF: Erreur d'entrée/sortie
$ sudo debugfs /dev/sdc1
debugfs 1.41.14 (22-Dec-2010)
debugfs:  imap /home/julien/Images/20120521/20120521_165457--DSC_0531.JPG.bad
/home/julien/Images/20120521/20120521_165457--DSC_0531.JPG.bad: File not found by ext2_lookup
debugfs:  ncheck 477904
Inode   Pathname
477904  /Images/20120521/20120521_165457--DSC_0531.JPG.bad
debugfs:  icheck 477904
Block   Inode number
477904  263836
debugfs:  quit
$ md5sum /home/julien/Images/20120521/20120521_165457--DSC_0531.JPG.bad
ac48502ad1c79a0eeeef8aee66678b8a  /home/julien/Images/20120521/20120521_165457--DSC_0531.JPG.bad

```

no error there and there would be only one block to check ? or need to repeat 42 times ?

---

