---
title: "SATA hard disk gets disconnected during use"
date: 2010-12-26
forum: Hardware
---

### Post by xp_even on 2010-12-26
I recently upgraded from Ubuntu 10.04 to 10.10.  I have two SATA hard disks on my PC: 160GB and 1TB. The system was working fine till this morning but now my 1TB disk (sda) keeps getting disconnected on its own. 

It does not get detected until I reboot the system. After reboot, it works fine for a while and again it goes offline. I am totally confused. I have checked the SATA connectors on the motherboard and it all seems to be properly connected.

I got the following from the log viewer:

```
[ 4571.689597] sd 2:0:0:0: [sda] Unhandled error code
[ 4571.689603] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 4571.689614] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 4571.689631] end_request: I/O error, dev sda, sector 0
[ 4571.689637] Buffer I/O error on device sda, logical block 0
[ 4628.386967] sd 2:0:0:0: [sda] Unhandled error code
[ 4628.386975] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 4628.386986] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 00 48 02 00 00 02 00
[ 4628.387011] end_request: I/O error, dev sda, sector 18434
[ 4628.387053] EXT4-fs (sda5): unable to read superblock
```Any guidance will be gratefully accepted.

---

### Post by Fafler on 2010-12-26
Bad powersupply? Does smartctl --all /dev/sda tell you anything?

---

### Post by xp_even on 2010-12-26
After a reboot (when the disk is detected), I get the following:

```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WCAV5A757802
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Dec 26 18:29:17 2010 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (19380) seconds.
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
recommended polling time:      ( 223) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   178   132   021    Pre-fail  Always       -       4091
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       377
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1239
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       373
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       131
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       13694
194 Temperature_Celsius     0x0022   113   104   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   197   000    Old_age   Always       -       17312
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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
```When the disk disconnects, it says:

```
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Device: /2:0:0:0  Version: 
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

---

