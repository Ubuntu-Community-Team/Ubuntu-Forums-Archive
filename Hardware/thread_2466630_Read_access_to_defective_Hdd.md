---
title: "Read access to defective Hdd"
date: 2021-09-01
forum: Hardware
---

### Post by yayou on 2021-09-01
Hello everyone,

I have a 2.5" Seagate 4 TiB external HDD, bought new about 5 years ago, which let me down several months ago (ls /dev just gives sdb and not sdb1). It has never suffered physical shocks, has never been used by anyone other than me and has always been plugged into my one and only Asus laptop (i7, 8 GiB of Ram, ...) and almost always on the one and only USB 3.0 port of the computer.
Last week I launched a DDrescue on him in the hope of recovering as many files as possible on his twin (I had bought 2 HDDs only differentiated by their colors). After several days the command bugged with this message:

```
Initial status (read from mapfile)
rescued: 970584 MB, tried: 4280 kB, bad-sector: 4096 B, bad areas: 1

Current status
     ipos:  186976 MB, non-trimmed:    1911 MB,  current rate:       0 B/s
     opos:  186976 MB, non-scraped:        0 B,  average rate:   8505 kB/s
non-tried:    2285 GB,  bad-sector:     8192 B,    error rate:  22675 kB/s
  rescued:    1713 GB,   bad areas:        2,        run time:  1d 14m 57s
pct rescued:   42.81%, read errors:    29160,  remaining time:         n/a
                              time since last successful read:          2s
Copying non-tried blocks... Pass 5 (forwards) 
ddrescue: Input file disappeared: No such file or directory
```
None of the Hdds were hot.

When I tried to relaunch hours later I got this:

```
ddrescue: Last block in mapfile begins past end of input file.
          Use '-C' if you are reading from a partial copy.
Try 'ddrescue --help' for more information.
```

The worst part is that by looking in the recovery HDD, to my surprise, the root tree has absolutely not disappeared while normally DDrescue is supposed to overwrite the contents of the recovery HDD. Several of the files it contained are no longer readable (but their names are still there) and others are still, but no trace of the files recovered by DDrescue (which claimed to have recovered more than 1.7 TiB). This is really a bad surprise after 3 days of execution.

Now I can no longer hope to resume the operation and finish it. The lost files, I can recover them (with luck). What I really lost is the history of activities contained in this HDD. My only hope for now is a faster command than this:

sudo ddrescue -f -n -b4096 / dev / disk / by-id / ata-ST4000LM016-1N2170_W801B8DY / dev / disk / by-id / "usb-Seagate_BUP_BL_NA7PKKV2-0: 0" $ HOME / tracked

but apparently there isn't, so I just have to get read access to the content by a special command. On my other HDDs, I have a history of my files with:

ls -alR > $HOME/History

Seeing that commands like DDrescue can access parts of the contents of faulty HDDs, is it possible to get (by DDrescue or some other means) just a listing of these still readable faulty HDD contents?

Thanks for having read.

---

### Post by TheFu on 2021-09-01
You got 5 years from a Seagate manufactured after 2005!  Wow!  Longest I've ever gotten was 18 months. Others lasted 13 months.  I have a few Seagate 320G drives from 2005-ish that have over 10 yrs powered on AND spinning that all show perfect SMART data.

 ```
sudo ddrescue -f -n -b4096 / dev / disk / by-id / ata-ST4000LM016-1N2170_W801B8DY / dev / disk / by-id / "usb-Seagate_BUP_BL_NA7PKKV2-0: 0" 
$ HOME / tracked
```
will never work. Too many spaces - that's obvious. No log file seems like an issue too.  With ddrescue, always, always, always use a log file pointed to storage not involved as the source or target. 
When posting commands, please be exact so we can tell if it is a typo or truly bad input.
And please wrap terminal commands AND output with forum code-tags. See my example above.

I've never used ddrescue using the /dev/disk/by-ANYTHING links.  Those point to specific devices, which should be used.  lsblk should show that.

Of course, a dying HDD will be dead eventually.  Every read and write makes that happen just a little sooner.  What does SMART say?

---

### Post by yayou on 2021-09-01
I have another desktop Seagate of 1 Tio which works fine after about 10 years, so I'm a bit surprised by what you say. What happen to Seagate from 2005 please?

---

### Post by yayou on 2021-09-01
Sorry, I'm in a hurry so I missed that mistake. This command is not the good one. What I should have sent is:

```
sudo ddrescue   -f    -n  -b4096  /dev/disk/by-id/ata-ST4000LM016-1N2170_W801B8DY    /dev/disk/by-id/"usb-Seagate_BUP_BL_NA7PKKV2-0:0"   $HOME/follow
```

SMART say very bad things:

```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-80-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Laptop HDD
Device Model:     ST4000LM016-1N2170
Serial Number:    W801B8DY
LU WWN Device Id: 5 000c50 09bf5ded8
Firmware Version: 0003
User Capacity:    4000787030016 bytes [4,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Aug  6 12:35:21 2021 CEST
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
data collection:                (    0) seconds.
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
recommended polling time:        ( 695) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   104   100   006    Pre-fail  Always       -       832713813
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       299
  5 Reallocated_Sector_Ct   0x0033   099   099   036    Pre-fail  Always       -       1040
  7 Seek_Error_Rate         0x000f   047   042   030    Pre-fail  Always       -       403732158390
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       64 (39 196 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       255
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   087   087   000    Old_age   Always       -       13
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       21475164165
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   052   045    Old_age   Always       -       35 (Min/Max 29/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       143
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1353
194 Temperature_Celsius     0x0022   035   048   000    Old_age   Always       -       35 (0 24 0 0 0)
197 Current_Pending_Sector  0x0012   099   085   000    Old_age   Always       -       120
198 Offline_Uncorrectable   0x0010   099   085   000    Old_age   Offline      -       120
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       51 (130 241 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       5504799069
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       5500613653

SMART Error Log Version: 1
ATA Error Count: 19 (device log contains only the most recent five errors)
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

Error 19 occurred at disk power-on lifetime: 64 hours (2 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 00  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 07 01 00 00 40 00      00:01:38.844  READ DMA EXT
  25 00 01 00 00 00 40 00      00:01:33.902  READ DMA EXT
  25 00 08 00 00 00 40 00      00:01:30.684  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.682  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.654  READ DMA EXT

Error 18 occurred at disk power-on lifetime: 64 hours (2 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 00 00 00 40 00      00:01:33.902  READ DMA EXT
  25 00 08 00 00 00 40 00      00:01:30.684  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.682  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.654  READ DMA EXT
  ec 00 01 00 00 00 00 00      00:01:30.638  IDENTIFY DEVICE

Error 17 occurred at disk power-on lifetime: 64 hours (2 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 00 00 00 40 00      00:01:30.684  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.682  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:30.654  READ DMA EXT
  ec 00 01 00 00 00 00 00      00:01:30.638  IDENTIFY DEVICE
  25 d5 07 19 00 00 40 00      00:01:30.543  READ DMA EXT

Error 16 occurred at disk power-on lifetime: 64 hours (2 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 09 00 00 00  Error: UNC at LBA = 0x00000009 = 9

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 d5 07 09 00 00 40 00      00:01:23.650  READ DMA EXT
  25 d5 01 08 00 00 40 00      00:01:03.467  READ DMA EXT
  25 d5 01 00 00 00 40 00      00:01:03.466  READ DMA EXT
  25 d5 07 01 00 00 40 00      00:00:56.548  READ DMA EXT
  25 d5 01 00 00 00 40 00      00:00:53.520  READ DMA EXT

Error 15 occurred at disk power-on lifetime: 64 hours (2 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 08 00 00 00  Error: UNC at LBA = 0x00000008 = 8

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 d5 01 08 00 00 40 00      00:01:03.467  READ DMA EXT
  25 d5 01 00 00 00 40 00      00:01:03.466  READ DMA EXT
  25 d5 07 01 00 00 40 00      00:00:56.548  READ DMA EXT
  25 d5 01 00 00 00 40 00      00:00:53.520  READ DMA EXT
  b0 d5 01 c0 4f c2 00 00      00:00:53.483  SMART READ LOG

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
```


That's better and sorry for the mistake above.

---

