---
title: "Seagate 4TB Drive Failing - Can't mount &quot;Stale file handle&quot;"
date: 2018-04-20
forum: Hardware
---

### Post by Ackis on 2018-04-20
First let me preface this with that the data on the drive isn't backed up, but it isn't important.  It's just easier if I can see what's on it still and maybe recover some metadata.

I know this drive is failing - it seems that there's 50% chance that it shows up on blkid when I've rebooted.  It doesn't even show in the bios. :)  So I'm working with a piece of crap.

What I've done is run fsck multiple times - around 10 with some of the checks taking 10 hours or more.  Again the drive is on its last legs. Press F to pay respects.

Here's some output from various commands that could be helpful.  Any tips/tricks/pointers would be helpful.

```
sudo tune2fs -l /dev/sdj
```

```
tune2fs 1.42.13 (17-May-2015)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          883d1bdf-b06d-4865-b64f-f0c44d66ab62
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244195328
Block count:              976754646
Reserved block count:     48837732
Free blocks:              961377496
Free inodes:              244195317
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Jun  4 18:16:06 2017
Last mount time:          n/a
Last write time:          Thu Apr 19 21:26:35 2018
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Jun  4 18:16:06 2017
Check interval:           0 (<none>)
Lifetime writes:          160 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      7817ff9f-54d7-4fd4-8012-c11920e8d8c7
Journal backup:           inode blocks

```

```
sudo file -s /dev/sdj
```
```
/dev/sdj: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,1), end-CHS (0x3ff,254,63), startsector 1, 4294967295 sectors, extended partition table (last)
```

```
sudo mount -o ext4 /dev/sdj /mnt/SG-4TB-3/
```
```
mount: wrong fs type, bad option, bad superblock on /dev/sdj,
       missing codepage or helper program, or other error

```

```
sudo mount /dev/sdj /mnt/SG-4TB-3
```
```
mount: mount /dev/sdj on /mnt/SG-4TB-3 failed: Stale file handle
```

```
 sudo fdisk -l /dev/sdj
```
```
The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdj: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 76CF3296-7588-4F52-86C7-8C1CB7601B77


Device     Start        End    Sectors  Size Type
/dev/sdj1   2048 7814037134 7814035087  3.7T Linux filesystem
```

```
 sudo smartctl -a /dev/sdj

``````
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-119-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Desktop HDD.15
Device Model:     ST4000DM000-1F2168
Serial Number:    S300FJS8
LU WWN Device Id: 5 000c50 06dc6bb4f
Firmware Version: CC54
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5900 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Apr 19 23:11:49 2018 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART Status not supported: Incomplete response, ATA output registers missing
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 116) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                (  107) seconds.
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
recommended polling time:        ( 523) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x1085) SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   092   092   006    Pre-fail  Always       -       70442968
  3 Spin_Up_Time            0x0003   093   091   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1764
  5 Reallocated_Sector_Ct   0x0033   078   078   010    Pre-fail  Always       -       28264
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       80051125
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       25817
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       984
183 Runtime_Bad_Block       0x0032   099   099   000    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   040   040   000    Old_age   Always       -       60
188 Command_Timeout         0x0032   099   099   000    Old_age   Always       -       3 3 3
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   051   045    Old_age   Always       -       41 (Min/Max 37/42)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       2
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       332169
194 Temperature_Celsius     0x0022   041   049   000    Old_age   Always       -       41 (0 11 0 0 0)
197 Current_Pending_Sector  0x0012   009   009   000    Old_age   Always       -       14984
198 Offline_Uncorrectable   0x0010   009   009   000    Old_age   Offline      -       14984
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       9125h+54m+38.305s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       32935486401
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       135946334945


SMART Error Log Version: 1
ATA Error Count: 60 (device log contains only the most recent five errors)
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


Error 60 occurred at disk power-on lifetime: 25692 hours (1070 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 4f 00   8d+02:07:42.639  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.105  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.068  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.051  READ DMA EXT


Error 59 occurred at disk power-on lifetime: 25692 hours (1070 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 4f 00   8d+02:07:25.105  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.068  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.051  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+02:07:25.037  READ DMA EXT


Error 58 occurred at disk power-on lifetime: 25692 hours (1070 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 4f 00   8d+01:29:57.797  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+01:29:57.790  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+01:29:57.772  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+01:29:57.756  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+01:29:57.737  READ DMA EXT


Error 57 occurred at disk power-on lifetime: 25691 hours (1070 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 4f 00   8d+00:34:17.350  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:34:17.331  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:34:17.318  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:34:17.302  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:34:17.292  READ DMA EXT


Error 56 occurred at disk power-on lifetime: 25691 hours (1070 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 4f 00   8d+00:26:18.664  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:26:00.577  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:26:00.558  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:26:00.538  READ DMA EXT
  25 00 08 ff ff ff 4f 00   8d+00:26:00.515  READ DMA EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%     25814         -
# 2  Short offline       Completed without error       00%     25807         -
# 3  Short offline       Interrupted (host reset)      00%     25807         -
# 4  Extended offline    Completed: read failure       90%     25267         -
# 5  Extended offline    Interrupted (host reset)      00%     20419         -


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





```

---

### Post by yancek on 2018-04-20
One of your commands shows "DOS/MBR boot sector" and another shows DiskLabel Type: GPT, which is it.  Additionally, your fdisk output shows:

> The primary GPT table is corrupt, but the backup appears OK, so that will be used.

Your mount command is trying to mount the device and your output shows that you have a partition with a filesystem on sdj1.  Try mounting the filesystem on the partition.

---

### Post by TheFu on 2018-04-20
Yes.
* this drive is dying.
* Seagate consumer disks have a history of early failures since 2006-ish.
* Running SMART tests weekly and comparing the changes over time is the best way to foresee failures, but that isn't always correct.  That means running **sudo smartclt -t long /dev/sdj** weekly and "short" tests as needed to update the data the report above shows. Of course, this assumes that sdj doesn't change. I see the drive devices change from time to time.

You can't mount the entire disk. Try  **sudo mount /dev/sdj1 /mnt/SG-4TB-3** - see how the partition number is added? A simple, but important difference.  Same for fsck. It works on file systems, not entire hdd devices.

I found it easier to stop buying seagate than to worry about disk failures constantly. Saving $10-$20 on soon-to-die vendors just isn't worth it to me. Every quarter backblaze makes a report about the HDDs they use in their business.  Google will find those reports.

Did I miss some question in the post?  I don't see one.

---

### Post by Ackis on 2018-04-24
Just wanted to post a follow-up.

First thank you for pointing out the difference between /dev/sdj and /dev/sdj1 - I was missing that in this process and possibly messed things up more. C'est la vi.

I was able to get the crappy drive mounted by running fdisk on it, and just re-writing the partition table.  After that it mounted and I was able to access most of the files until it crapped itself again.

Now it seems I'm only able to mount it if I run fdisk -l on it.  Not a huge deal, but in case someone googles this at a later date I wanted to let them know what I've done. (And what I've done wrong)

What's also interesting is that when I am able to mount the drive, and it fails it messes up all of the /dev/sdXXX on my system - for example this drive I'm talking about moves from sdj to sdk and other drives get bumped as well.

---

### Post by TheFu on 2018-04-24
Which is why using partition UUID to mount is very important.  UUIDs don't change without deliberate action.  The **blkid** command  will show the device-to-UUID mapping.

USB connected storage will almost always change devices, BTW.

Please mark the thread as solved - Thread Tools button near the top. This helps others in the community.

---

### Post by Ackis on 2018-04-25
> **TheFu said:**
> Which is why using partition UUID to mount is very important.  UUIDs don't change without deliberate action.  The **blkid** command  will show the device-to-UUID mapping.

I already do. :)

> **TheFu said:**
> USB connected storage will almost always change devices, BTW.

Didn't realize this - the three 4TB drives are in a USB enclosure now.

> **TheFu said:**
> Please mark the thread as solved - Thread Tools button near the top. This helps others in the community.

Will do. Thanks again.

---

