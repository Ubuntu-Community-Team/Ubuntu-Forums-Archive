---
title: "Failed hard drive or kernel bug? Emask 0x9 (media error)"
date: 2009-04-08
forum: Hardware
---

### Post by Endolith on 2009-04-08
I bought a new Seagate hard drive two months ago, and I'm getting errors on it that screw up Ubuntu.

I ran GNU ddrescue on it, and it only found 1 error (1024 bytes).  I'm confused as to what that means.  If this is just a bad block, wouldn't the hard drive automatically mark it "bad" and carry on?  What else would cause a single kilobyte of error on a 160 GB drive?

```
% ddrescue --direct -r 7 -v /dev/sda sdaimage sdalog    


About to copy 160041 MBytes from /dev/sda to sdaimage
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 7    
Direct: yes    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:   160041 MB,  errsize:    1024 B,  errors:       1
Current status
rescued:   160041 MB,  errsize:    1024 B,  current rate:        0 B/s
   ipos:   102334 MB,   errors:       1,    average rate:        0 B/s
   opos:   102334 MB
Finished                   
```Here are some of the errors I'm getting.  Does anyone know what these errors mean?

Is there a way to find out what's at "block 134574880" (using dd to terminal?) to find out if the error occurs in a critical file?

```
Apr  3 00:02:05 inspiron kernel: [  474.208024] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 00:02:05 inspiron kernel: [  474.208024] ata1.00: BMDMA stat 0x24
Apr  3 00:02:05 inspiron kernel: [  474.208024] ata1.00: cmd c8/00:08:75:ff:3a/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 00:02:05 inspiron kernel: [  474.208024]          res 58/00:76:76:3a:3a/00:00:00:00:00/58 Emask 0x2 (HSM violation)
Apr  3 00:02:05 inspiron kernel: [  474.208024] ata1.00: status: { DRDY DRQ }
Apr  3 00:02:05 inspiron kernel: [  474.374450] ata1.00: revalidation failed (errno=-5)
Apr  3 00:02:40 inspiron kernel: [  514.210201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 00:02:55 inspiron kernel: [  514.210254] ata1.00: BMDMA stat 0x24
Apr  3 00:02:56 inspiron kernel: [  514.210316] ata1.00: cmd ca/00:08:bd:63:52/00:00:00:00:00/e4 tag 0 dma 4096 out
Apr  3 00:02:58 inspiron kernel: [  514.210332]          res 58/00:be:be:52:52/00:00:00:00:00/58 Emask 0x2 (HSM violation)
Apr  3 00:02:58 inspiron kernel: [  514.210369] ata1.00: status: { DRDY DRQ }
Apr  3 00:03:01 inspiron kernel: [  514.384015] ata1.00: revalidation failed (errno=-5)
Apr  3 00:09:16 inspiron kernel: [  870.205706] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 00:09:16 inspiron kernel: [  870.205706] ata1.00: BMDMA stat 0x24
Apr  3 00:09:16 inspiron kernel: [  870.205746] ata1.00: cmd ca/00:08:a5:2a:28/00:00:00:00:00/e5 tag 0 dma 4096 out
Apr  3 00:09:16 inspiron kernel: [  870.205764]          res 58/00:a5:a5:28:28/00:00:00:00:00/58 Emask 0x2 (HSM violation)
Apr  3 00:09:16 inspiron kernel: [  870.205801] ata1.00: status: { DRDY DRQ }
Apr  3 00:09:16 inspiron kernel: [  900.384273] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 00:09:16 inspiron kernel: [  900.384366] ata1.00: cmd ca/00:08:a5:2a:28/00:00:00:00:00/e5 tag 0 dma 4096 out
Apr  3 00:09:16 inspiron kernel: [  900.384383]          res 40/00:a5:a5:28:28/00:00:00:00:00/58 Emask 0x4 (timeout)
Apr  3 00:09:16 inspiron kernel: [  900.384420] ata1.00: status: { DRDY }




Apr  3 01:14:36 inspiron kernel: [ 4830.208405] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 01:53:01 inspiron kernel: [  297.455775] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:53:01 inspiron kernel: [  297.455838] ata1.00: BMDMA stat 0x25
Apr  3 01:53:01 inspiron kernel: [  297.455894] ata1.00: cmd c8/00:08:65:1e:5d/00:00:00:00:00/e7 tag 0 dma 4096 in
Apr  3 01:53:01 inspiron kernel: [  297.455896]          res 51/04:9c:9c:5d:5d/00:00:00:00:00/51 Emask 0x1 (device error)
Apr  3 01:53:01 inspiron kernel: [  297.456061] ata1.00: status: { DRDY ERR }
Apr  3 01:53:01 inspiron kernel: [  297.456113] ata1.00: error: { ABRT }
Apr  3 01:53:01 inspiron kernel: [  297.475262] ata1.00: revalidation failed (errno=-5)




Apr  3 02:44:54 inspiron kernel: [ 2773.107082] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2773.107099] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2773.107117] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2773.107122]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2773.107133] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2773.107140] ata1.00: error: { UNC }
Apr  3 02:44:54 inspiron kernel: [ 2777.411384] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2777.411400] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2777.411418] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2777.411423]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2777.411434] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2777.411441] ata1.00: error: { UNC }
Apr  3 02:44:54 inspiron kernel: [ 2781.793435] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2781.793451] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2781.793470] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2781.793475]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2781.793486] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2781.793493] ata1.00: error: { UNC }
Apr  3 02:44:54 inspiron kernel: [ 2786.175472] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2786.175488] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2786.175506] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2786.175511]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2786.175522] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2786.175529] ata1.00: error: { UNC }
Apr  3 02:44:54 inspiron kernel: [ 2790.513154] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2790.513170] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2790.513188] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2790.513193]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2790.513204] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2790.513211] ata1.00: error: { UNC }
Apr  3 02:44:54 inspiron kernel: [ 2794.806552] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:54 inspiron kernel: [ 2794.806569] ata1.00: BMDMA stat 0x25
Apr  3 02:44:54 inspiron kernel: [ 2794.806587] ata1.00: cmd c8/00:28:6d:cc:e9/00:00:00:00:00/eb tag 0 dma 20480 in
Apr  3 02:44:54 inspiron kernel: [ 2794.806592]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:54 inspiron kernel: [ 2794.806602] ata1.00: status: { DRDY ERR }
Apr  3 02:44:54 inspiron kernel: [ 2794.806610] ata1.00: error: { UNC }
Apr  3 02:44:55 inspiron kernel: [ 2794.828650] end_request: I/O error, dev sda, sector 199871623
Apr  3 02:44:56 inspiron kernel: [ 2799.521441] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:56 inspiron kernel: [ 2799.521458] ata1.00: BMDMA stat 0x25
Apr  3 02:44:56 inspiron kernel: [ 2799.521476] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:56 inspiron kernel: [ 2799.521481]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:56 inspiron kernel: [ 2799.521492] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2799.521499] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2803.881338] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:57 inspiron kernel: [ 2803.881354] ata1.00: BMDMA stat 0x25
Apr  3 02:44:57 inspiron kernel: [ 2803.881372] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:57 inspiron kernel: [ 2803.881377]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:57 inspiron kernel: [ 2803.881388] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2803.881395] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2808.263418] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:57 inspiron kernel: [ 2808.263433] ata1.00: BMDMA stat 0x25
Apr  3 02:44:57 inspiron kernel: [ 2808.263451] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:57 inspiron kernel: [ 2808.263457]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:57 inspiron kernel: [ 2808.263467] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2808.263474] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2812.601141] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:57 inspiron kernel: [ 2812.601157] ata1.00: BMDMA stat 0x25
Apr  3 02:44:57 inspiron kernel: [ 2812.601175] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:57 inspiron kernel: [ 2812.601180]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:57 inspiron kernel: [ 2812.601190] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2812.601198] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2816.894486] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:57 inspiron kernel: [ 2816.894502] ata1.00: BMDMA stat 0x25
Apr  3 02:44:57 inspiron kernel: [ 2816.894521] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:57 inspiron kernel: [ 2816.894526]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:57 inspiron kernel: [ 2816.894537] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2816.894544] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2821.198926] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 02:44:57 inspiron kernel: [ 2821.198942] ata1.00: BMDMA stat 0x25
Apr  3 02:44:57 inspiron kernel: [ 2821.198960] ata1.00: cmd c8/00:08:85:cc:e9/00:00:00:00:00/eb tag 0 dma 4096 in
Apr  3 02:44:57 inspiron kernel: [ 2821.198965]          res 51/40:00:87:cc:e9/00:00:00:00:00/eb Emask 0x9 (media error)
Apr  3 02:44:57 inspiron kernel: [ 2821.198976] ata1.00: status: { DRDY ERR }
Apr  3 02:44:57 inspiron kernel: [ 2821.198983] ata1.00: error: { UNC }
Apr  3 02:44:57 inspiron kernel: [ 2821.220662] end_request: I/O error, dev sda, sector 199871623







Apr  3 19:08:24 inspiron kernel: [  422.088998] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 19:08:24 inspiron kernel: [  422.089013] ata1.00: BMDMA stat 0x24
Apr  3 19:08:25 inspiron kernel: [  422.089032] ata1.00: cmd c8/00:10:55:2b:83/00:00:00:00:00/e4 tag 0 dma 8192 in
Apr  3 19:08:25 inspiron kernel: [  422.089036]          res 58/00:ff:ad:28:83/00:00:00:00:00/e4 Emask 0x2 (HSM violation)
Apr  3 19:08:25 inspiron kernel: [  422.089047] ata1.00: status: { DRDY DRQ }
``````
root@sysresccd /root % smartctl --all /dev/sda
smartctl version 5.38 [i486-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.3
Device Model:     ST9160821A
Serial Number:    5MACX6PR
Firmware Version: 3.ALE
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sun Apr  5 19:58:04 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:          ( 426) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 165) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   091   006    Pre-fail  Always       -       225218
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       38
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   057   057   030    Pre-fail  Always       -       274918978938
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1615
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       63
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       151
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   057   048   045    Old_age   Always       -       43 (Lifetime Min/Max 20/43)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       45
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       483
194 Temperature_Celsius     0x0022   043   052   000    Old_age   Always       -       43 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   059   056   000    Old_age   Always       -       52322168
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 152 (device log contains only the most recent five errors)
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

Error 152 occurred at disk power-on lifetime: 1612 hours (67 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 7a 86 cc e9 e0  Error: UNC at LBA = 0x00e9cc86 = 15322246

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 00 00 cc e9 e0 00      03:13:46.031  READ VERIFY SECTOR(S) EXT
  42 00 00 00 ca e9 e0 00      03:13:46.022  READ VERIFY SECTOR(S) EXT
  42 00 00 00 c8 e9 e0 00      03:13:46.016  READ VERIFY SECTOR(S) EXT
  42 00 00 00 c6 e9 e0 00      03:13:46.007  READ VERIFY SECTOR(S) EXT
  42 00 00 00 c4 e9 e0 00      03:13:46.117  READ VERIFY SECTOR(S) EXT

Error 151 occurred at disk power-on lifetime: 1574 hours (65 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 87 cc e9 eb  Error: UNC at LBA = 0x0be9cc87 = 199871623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 85 cc e9 eb 00      01:18:18.390  READ DMA
  27 00 00 00 00 00 e0 00      01:18:18.390  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      01:18:18.384  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:18:27.061  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      01:18:27.061  READ NATIVE MAX ADDRESS EXT

Error 150 occurred at disk power-on lifetime: 1574 hours (65 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 87 cc e9 eb  Error: UNC at LBA = 0x0be9cc87 = 199871623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 85 cc e9 eb 00      01:18:18.390  READ DMA
  27 00 00 00 00 00 e0 00      01:18:18.390  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      01:18:18.384  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:18:18.374  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      01:18:18.374  READ NATIVE MAX ADDRESS EXT

Error 149 occurred at disk power-on lifetime: 1574 hours (65 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 87 cc e9 eb  Error: UNC at LBA = 0x0be9cc87 = 199871623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 85 cc e9 eb 00      01:18:18.390  READ DMA
  27 00 00 00 00 00 e0 00      01:18:18.390  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      01:18:18.384  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:18:18.374  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      01:18:18.374  READ NATIVE MAX ADDRESS EXT

Error 148 occurred at disk power-on lifetime: 1574 hours (65 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 87 cc e9 eb  Error: UNC at LBA = 0x0be9cc87 = 199871623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 85 cc e9 eb 00      01:18:09.611  READ DMA
  27 00 00 00 00 00 e0 00      01:18:09.611  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      01:18:09.604  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:18:05.304  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      01:18:05.304  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1

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

``````
> sudo ./st -T 100 /dev/sg0
Drive /dev/sg0 does not support DST - generic long test will be run
Starting generic long (full sequential verify) test (312581807 blocks) on drive /dev/sg0 (^C will abort test)
    Sequential Test 5 % complete on drive /dev/sg0
    Sequential Test 10 % complete on drive /dev/sg0
    Sequential Test 15 % complete on drive /dev/sg0
    Sequential Test 20 % complete on drive /dev/sg0
    Sequential Test 25 % complete on drive /dev/sg0
    Sequential Test 30 % complete on drive /dev/sg0
    Sequential Test 35 % complete on drive /dev/sg0
    Sequential Test 40 % complete on drive /dev/sg0
    Sequential Test 45 % complete on drive /dev/sg0
    Sequential Test 50 % complete on drive /dev/sg0
    Sequential Test 55 % complete on drive /dev/sg0
    Sequential Test 60 % complete on drive /dev/sg0
    VERIFY  failed on block 199871488   Sense data = 11/00/00
TEST FAILED at block 134574880 on drive /dev/sg0
```

---

### Post by Endolith on 2009-04-09
So I ran DBAN on the disk to prepare it for sending back, and then ran tests on it again.  Sure enough, they pass now.  Does this just mean it had two bad blocks and now it's marked them or put them back into active duty?  Is the drive trustworthy?  Is there something about Ubuntu that prevents the drive from marking bad sectors like it normally would?

Current_Pending_Sector and Offline_Uncorrectable were previously "2", and now both are "0", and everything checks out.  What's going on?

```
> sudo ./st -T 100 /dev/sg0
Drive /dev/sg0 does not support DST - generic long test will be run
Starting generic long (full sequential verify) test (312581807 blocks) on drive /dev/sg0 (^C will abort test)
    Sequential Test 5 % complete on drive /dev/sg0
    Sequential Test 10 % complete on drive /dev/sg0
    Sequential Test 15 % complete on drive /dev/sg0
    Sequential Test 20 % complete on drive /dev/sg0
    Sequential Test 25 % complete on drive /dev/sg0
    Sequential Test 30 % complete on drive /dev/sg0
    Sequential Test 35 % complete on drive /dev/sg0
    Sequential Test 40 % complete on drive /dev/sg0
    Sequential Test 45 % complete on drive /dev/sg0
    Sequential Test 50 % complete on drive /dev/sg0
    Sequential Test 55 % complete on drive /dev/sg0
    Sequential Test 60 % complete on drive /dev/sg0
    Sequential Test 65 % complete on drive /dev/sg0
    Sequential Test 70 % complete on drive /dev/sg0
    Sequential Test 75 % complete on drive /dev/sg0
    Sequential Test 80 % complete on drive /dev/sg0
    Sequential Test 85 % complete on drive /dev/sg0
    Sequential Test 90 % complete on drive /dev/sg0
    Sequential Test 95 % complete on drive /dev/sg0
Generic Long Test PASSED on drive /dev/sg0 

```
```
> sudo smartctl --all /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.3
Device Model:     ST9160821A
Serial Number:    5MACX6PR
Firmware Version: 3.ALE
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Fri Apr 10 01:39:14 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 426) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 165) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   091   006    Pre-fail  Always       -       233470036
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       44
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   058   057   030    Pre-fail  Always       -       283512589616
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1669
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       74
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       1075
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   055   048   045    Old_age   Always       -       45 (Lifetime Min/Max 35/48)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       556
194 Temperature_Celsius     0x0022   045   052   000    Old_age   Always       -       45 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   060   056   000    Old_age   Always       -       38084527
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1076 (device log contains only the most recent five errors)
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

Error 1076 occurred at disk power-on lifetime: 1626 hours (67 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 88 cc e9 eb  Error: UNC at LBA = 0x0be9cc88 = 199871624

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 88 cc e9 eb 00      06:03:08.871  READ DMA
  27 00 00 00 00 00 e0 00      06:03:08.871  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      06:03:08.869  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      06:03:04.567  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      06:03:04.567  READ NATIVE MAX ADDRESS EXT

Error 1075 occurred at disk power-on lifetime: 1626 hours (67 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 88 cc e9 eb  Error: UNC at LBA = 0x0be9cc88 = 199871624

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 88 cc e9 eb 00      06:02:55.936  READ DMA
  27 00 00 00 00 00 e0 00      06:02:55.936  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      06:02:55.930  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      06:03:04.567  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      06:03:04.567  READ NATIVE MAX ADDRESS EXT

Error 1074 occurred at disk power-on lifetime: 1626 hours (67 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 88 cc e9 eb  Error: UNC at LBA = 0x0be9cc88 = 199871624

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 88 cc e9 eb 00      06:02:55.936  READ DMA
  27 00 00 00 00 00 e0 00      06:02:55.936  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      06:02:55.930  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      06:02:55.914  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      06:02:55.913  READ NATIVE MAX ADDRESS EXT

Error 1073 occurred at disk power-on lifetime: 1626 hours (67 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 88 cc e9 eb  Error: UNC at LBA = 0x0be9cc88 = 199871624

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 88 cc e9 eb 00      06:02:55.936  READ DMA
  27 00 00 00 00 00 e0 00      06:02:55.936  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      06:02:55.930  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      06:02:55.914  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      06:02:55.913  READ NATIVE MAX ADDRESS EXT

Error 1072 occurred at disk power-on lifetime: 1626 hours (67 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 88 cc e9 eb  Error: UNC at LBA = 0x0be9cc88 = 199871624

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 88 cc e9 eb 00      06:02:47.294  READ DMA
  27 00 00 00 00 00 e0 00      06:02:47.293  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      06:02:47.290  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      06:02:43.011  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      06:02:43.011  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1658         -
# 2  Extended offline    Completed: read failure       90%      1651         199871624
# 3  Extended offline    Completed: read failure       90%      1651         199871624
# 4  Short offline       Completed: read failure       90%      1651         199871624

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

