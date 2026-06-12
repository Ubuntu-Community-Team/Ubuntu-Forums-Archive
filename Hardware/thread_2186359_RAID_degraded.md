---
title: "RAID degraded"
date: 2013-11-07
forum: Hardware
---

### Post by reano on 2013-11-07
Hey guys,
We're having a very weird issue at work. Our server has 6 drives, set up with RAID1 as follows:

/dev/md0, consisting of:
/dev/sda1
/dev/sdb1

/dev/md1, consisting of:
/dev/sda2
/dev/sdb2

/dev/md2, consisting of:
/dev/sda3
/dev/sdb3

/dev/md3, consisting of:
/dev/sdc1
/dev/sdd1

/dev/md4, consisting of:
/dev/sde1
/dev/sdf1

As you can see, md0, md1 and md2 all use the same 2 drives (split into 3 partitions). I also have to note that this is done via ubuntu software raid, not hardware raid.

Today, the /md0 RAID1 array shows as degraded - it is missing the /dev/sdb1 drive. But since /dev/sdb1 is only a partition (and /dev/sdb2 and /dev/sdb3 are working fine), it's obviously not the drive that's gone AWOL, it seems the partition itself is missing.

How is that even possible? And what could we do to fix it?

My output of cat /proc/mdstat:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

md1 : active raid1 sda2[0] sdb2[1]
      24006528 blocks super 1.2 [2/2] [UU]


md2 : active raid1 sda3[0] sdb3[1]
      1441268544 blocks super 1.2 [2/2] [UU]


md0 : active raid1 sda1[0]
      1464710976 blocks super 1.2 [2/1] [U_]


md3 : active raid1 sdd1[1] sdc1[0]
      2930133824 blocks super 1.2 [2/2] [UU]


md4 : active raid1 sdf2[1] sde2[0]
      2929939264 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```


Any help would be greatly appreciated!

---

### Post by reano on 2013-11-07
FYI: I tried the following:

```
mdadm /dev/md0 --add /dev/sdb1
```

But got this error:

```
mdadm: add new device failed for /dev/sdb1 as 2: Invalid argument
```

---

### Post by reano on 2013-11-07
Some more info: the output of mdadm --detail /dev/md0 is:


```
/dev/md0:
        Version : 1.2
  Creation Time : Sat Dec 29 17:09:45 2012
     Raid Level : raid1
     Array Size : 1464710976 (1396.86 GiB 1499.86 GB)
  Used Dev Size : 1464710976 (1396.86 GiB 1499.86 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


    Update Time : Thu Nov  7 15:55:07 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : lia:0  (local to host lia)
           UUID : eb302d19:ff70c7bf:401d63af:ed042d59
         Events : 26216


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed

```

---

### Post by reano on 2013-11-13
Hate to bump a thread, but I still need help with this. Any advice, anyone? :)

---

### Post by SaturnusDJ on 2013-11-13
Post the output of this:

```

mdadm --examine /dev/sda1
mdadm --examine /dev/sdb1

```

---

### Post by reano on 2013-11-13
> **SaturnusDJ said:**
> Post the output of this:

```

mdadm --examine /dev/sda1
mdadm --examine /dev/sdb1

```
Sure, here you go:

```

/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : eb302d19:ff70c7bf:401d63af:ed042d59
           Name : lia:0  (local to host lia)
  Creation Time : Sat Dec 29 17:09:45 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 2929422336 (1396.86 GiB 1499.86 GB)
     Array Size : 1464710976 (1396.86 GiB 1499.86 GB)
  Used Dev Size : 2929421952 (1396.86 GiB 1499.86 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ad54335c:00241027:a3732eae:dcb1c708


    Update Time : Wed Nov 13 14:18:35 2013
       Checksum : ffad19d5 - correct
         Events : 371283




   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)

```

Buuuut, for sdb1, I get the following:

```
mdadm: No md superblock detected on /dev/sdb1.
```

---

### Post by SaturnusDJ on 2013-11-13
That's clear.

How's the SMART status for that device?
```

smartctl -a /dev/sdb
smartctl -t short /dev/sdb
smartctl -a /dev/sdb

```

Also look in the logs for information.
Only proceed if there are no errors.

I've seen cases where superblocks where 'missing' too, but after rebooting they were back.
So you can try some reboots if S.M.A.R.T. is fine and the machine is allowed to be unavailable some time (note that sometimes upon reboot a filesystem check may happen).

---

### Post by reano on 2013-11-14
> **SaturnusDJ said:**
> That's clear.

How's the SMART status for that device?
```

smartctl -a /dev/sdb
smartctl -t short /dev/sdb
smartctl -a /dev/sdb

```

Also look in the logs for information.
Only proceed if there are no errors.

I've seen cases where superblocks where 'missing' too, but after rebooting they were back.
So you can try some reboots if S.M.A.R.T. is fine and the machine is allowed to be unavailable some time (note that sometimes upon reboot a filesystem check may happen).
I've tried reboots last week, unfortunately that didn't help. smartctl -a /dev/sdb gives me the following:

> smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-29-generic] (local build)Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     ST3000VX000-9YW166
Serial Number:    W1F0VJ95
LU WWN Device Id: 5 000c50 052d36854
Firmware Version: CV13
User Capacity:    3Â 000Â 592Â 982Â 016 bytes [3,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov 14 08:28:41 2013 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (  584) seconds.
Offline data collection
capabilities:                    (0x73) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x10b9) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       31525534
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       97
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       189250104
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       8948
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       97
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   032   032   000    Old_age   Always       -       68
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       12885098499
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       264
190 Airflow_Temperature_Cel 0x0022   064   059   045    Old_age   Always       -       36 (Min/Max 34/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       89
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1145
194 Temperature_Celsius     0x0022   036   041   000    Old_age   Always       -       36 (0 16 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       15
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       15
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
ATA Error Count: 2798 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.


Error 2798 occurred at disk power-on lifetime: 8930 hours (372 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 09 08 00 00  Error: UNC at LBA = 0x00000809 = 2057


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 08 00 e0 00   6d+05:48:06.522  READ DMA
  27 00 00 00 00 00 e0 00   6d+05:48:06.521  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   6d+05:48:06.513  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   6d+05:48:06.409  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   6d+05:48:06.401  READ NATIVE MAX ADDRESS EXT


Error 2797 occurred at disk power-on lifetime: 8930 hours (372 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 09 08 00 00  Error: UNC at LBA = 0x00000809 = 2057


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 08 00 e0 00   6d+05:48:06.126  READ DMA
  27 00 00 00 00 00 e0 00   6d+05:48:06.125  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   6d+05:48:06.117  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   6d+05:48:06.045  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   6d+05:48:06.037  READ NATIVE MAX ADDRESS EXT


Error 2795 occurred at disk power-on lifetime: 8930 hours (372 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 09 08 00 00  Error: UNC at LBA = 0x00000809 = 2057


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 08 00 e0 00   6d+05:48:06.126  READ DMA
  27 00 00 00 00 00 e0 00   6d+05:48:06.125  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   6d+05:48:06.117  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   6d+05:48:06.045  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   6d+05:48:06.037  READ NATIVE MAX ADDRESS EXT


Error 2794 occurred at disk power-on lifetime: 8930 hours (372 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 09 08 00 00  Error: UNC at LBA = 0x00000809 = 2057


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 08 00 e0 00   6d+05:48:05.769  READ DMA
  27 00 00 00 00 00 e0 00   6d+05:48:05.769  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   6d+05:48:05.761  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00   6d+05:48:05.701  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   6d+05:48:05.685  READ NATIVE MAX ADDRESS EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      8933         -


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




---

