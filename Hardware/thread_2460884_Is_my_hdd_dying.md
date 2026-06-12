---
title: "Is my hdd dying?"
date: 2021-04-20
forum: Hardware
---

### Post by pellefantus on 2021-04-20
I have an old 3,5 SATA that is from 2008, and my journalctl displayed some errors.

I have always had a hard time knowing how to interpret the logs of smartctl, and I hope you can help me.

** journalctl -p 3 -xb**
```
 Apr 20 20:08:27 pc smartd[881]: Device: /dev/sda [SAT], 6 Currently unreadable (pending) sectors
Apr 20 20:08:27 pc smartd[881]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Apr 20 20:38:27 pc smartd[881]: Device: /dev/sda [SAT], 6 Currently unreadable (pending) sectors
Apr 20 20:38:27 pc smartd[881]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Apr 20 21:08:27 pc smartd[881]: Device: /dev/sda [SAT], 6 Currently unreadable (pending) sectors
Apr 20 21:08:27 pc smartd[881]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Apr 20 21:13:38 pc kernel: ata3.00: exception Emask 0x0 SAct 0x7c0000 SErr 0x0 action 0x0
Apr 20 21:13:38 pc kernel: ata3.00: irq_stat 0x40000008
Apr 20 21:13:38 pc kernel: ata3.00: failed command: READ FPDMA QUEUED
Apr 20 21:13:38 pc kernel: ata3.00: cmd 60/e8:90:20:54:00/00:00:00:00:00/40 tag 18 ncq dma 118784 in
                                    res 41/40:00:c0:54:00/00:00:00:00:00/40 Emask 0x409 (media error) <F>
Apr 20 21:13:38 pc kernel: ata3.00: status: { DRDY ERR }
Apr 20 21:13:38 pc kernel: ata3.00: error: { UNC }
Apr 20 21:13:38 pc kernel: print_req_error: I/O error, dev sda, sector 21696
Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], 6 Currently unreadable (pending) sectors
Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], Self-Test Log error count increased from 3 to 4
Apr 20 21:38:27 pc sSMTP[5849]: Cannot open mail.smtp2go.com:2525
Apr 20 21:38:27 pc smartd[881]: Warning via /usr/share/smartmontools/smartd-runner to root produced unexpected output (168 bytes) to STDOUT/STDERR:
Apr 20 21:38:27 pc smartd[881]: /etc/smartmontools/run.d/10mail:
Apr 20 21:38:27 pc smartd[881]: mail: cannot send message: Process exited with a non-zero status
Apr 20 21:38:27 pc smartd[881]: run-parts: /etc/smartmontools/run.d/10mail exited with return code 36
Apr 20 21:38:27 pc smartd[881]: Warning via /usr/share/smartmontools/smartd-runner to root: failed (32-bit/8-bit exit status: 256/1)


```

** Smartctl output:**
```
sudo smartctl -a /dev/sda
smartctl 6.6 2016-05-31 r4324 [i686-linux-4.15.0-142-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F1 DT
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ1CQA06465
LU WWN Device Id: 5 0000f0 00084c69e
Firmware Version: 1AA01113
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7, ATA8-ACS T13/1699-D revision 3b
Local Time is:    Tue Apr 20 21:25:27 2021 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (12000) seconds.
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
recommended polling time:      ( 201) minutes.
Conveyance self-test routine
recommended polling time:      (  21) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   099   002   051    Pre-fail  Always   In_the_past 284
  3 Spin_Up_Time            0x0007   076   076   011    Pre-fail  Always       -       8060
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3012
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       9995
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       17165
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       1
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3002
 13 Read_Soft_Error_Rate    0x000e   099   002   000    Old_age   Always       -       284
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       5
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       11394
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   056   000    Old_age   Always       -       35 (Min/Max 18/36)
194 Temperature_Celsius     0x0022   065   054   000    Old_age   Always       -       35 (Min/Max 18/36)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       16658918
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       30
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   099   099   000    Old_age   Always       -       12

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     17138         21696
# 2  Short offline       Completed: read failure       20%     16909         21696
# 3  Extended offline    Completed: read failure       90%     16892         21696
# 4  Short offline       Completed without error       00%      8693         -

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

### Post by ipv2 on 2021-04-20
i use this :

[https://www.hdsentinel.com/hard_disk_sentinel_linux.php](https://www.hdsentinel.com/hard_disk_sentinel_linux.php)

can be done via cli & it also has a gui thingy.

---

### Post by CelticWarrior on 2021-04-20
```
[COLOR=#000000][FONT=&amp]Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], 6 Currently unreadable (pending) sectors
[/FONT][/COLOR]Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], 1 Offline uncorrectable sectors
Apr 20 21:38:27 pc smartd[881]: Device: /dev/sda [SAT], Self-Test Log error count increased from 3 to 4
```

Yes, it's dying slowly.

---

### Post by Autodave on 2021-04-20
+1 w/CelticWarrior.  Time to get a new one.

---

