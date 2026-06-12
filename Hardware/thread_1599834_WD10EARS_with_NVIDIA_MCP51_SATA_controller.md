---
title: "WD10EARS with NVIDIA MCP51 SATA controller"
date: 2010-10-18
forum: Hardware
---

### Post by Alve on 2010-10-18
Hi all!

I have installed new HDD, WD10EARS, and got a problem. System (10.04 and 10.10) freezes on 5-20 seconds 3-5 times for a day and after that I see in dmesg this errors:
```

[14478.051742] ata3: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[14478.051755] ata3: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[14478.051758]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
[14478.051766] ata3: ATA_REG 0x40 ERR_REG 0x0
[14478.051770] ata3: tag : dhfis dmafis sdbfis sacitve
[14478.051776] ata3: tag 0x0: 1 1 0 1  
[14478.051798] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
[14478.051807] ata3.00: failed command: WRITE FPDMA QUEUED
[14478.051823] ata3.00: cmd 61/08:00:70:12:84/00:00:3b:00:00/40 tag 0 ncq 4096 out
[14478.051826]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[14478.051833] ata3.00: status: { DRDY }
[14478.051843] ata3: hard resetting link
[14478.051849] ata3: nv: skipping hardreset on occupied port
[14478.517452] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[14478.545382] ata3.00: configured for UDMA/133
[14478.545398] ata3.00: device reported invalid CHS sector 0
[14478.545425] ata3: EH complete
```SMART info:

```

smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WCAV5E232417
Firmware Version: 80.00A80
User Capacity:    1.000.204.886.016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Oct 18 16:09:51 2010 EEST
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
data collection:          (19800) seconds.
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
recommended polling time:      ( 228) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   144   129   021    Pre-fail  Always       -       5775
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       160
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       880
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       155
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       40
193 Load_Cycle_Count        0x0032   187   187   000    Old_age   Always       -       39778
194 Temperature_Celsius     0x0022   107   092   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 4
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

Error 4 occurred at disk power-on lifetime: 778 hours (32 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 30 4f c2 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 be 4f c2 e0 02      08:32:39.629  SMART WRITE LOG
  b0 da 01 00 4f c2 e0 02      08:32:39.553  SMART RETURN STATUS
  80 44 00 00 44 57 e0 02      08:32:39.553  [VENDOR SPECIFIC]
  b0 d6 01 be 4f c2 e0 02      08:32:39.522  SMART WRITE LOG
  80 45 00 00 44 57 e0 02      08:32:39.522  [VENDOR SPECIFIC]

Error 3 occurred at disk power-on lifetime: 778 hours (32 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 30 4f c2 a0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 be 4f c2 a0 02      08:28:59.353  SMART WRITE LOG
  b0 da 01 00 4f c2 a0 02      08:28:59.266  SMART RETURN STATUS
  80 44 00 00 44 57 a0 02      08:28:59.266  [VENDOR SPECIFIC]
  b0 d6 01 be 4f c2 a0 02      08:28:59.246  SMART WRITE LOG
  80 45 00 01 44 57 a0 02      08:28:59.246  [VENDOR SPECIFIC]

Error 2 occurred at disk power-on lifetime: 516 hours (21 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 30 4f c2 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 be 4f c2 e0 02      00:04:39.988  SMART WRITE LOG
  b0 da 01 00 4f c2 e0 02      00:04:39.901  SMART RETURN STATUS
  80 44 00 00 44 57 e0 02      00:04:39.901  [VENDOR SPECIFIC]
  b0 d6 01 be 4f c2 e0 02      00:04:39.882  SMART WRITE LOG
  80 45 00 00 44 57 e0 02      00:04:39.882  [VENDOR SPECIFIC]

Error 1 occurred at disk power-on lifetime: 516 hours (21 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 30 4f c2 a0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 be 4f c2 a0 02      00:00:59.645  SMART WRITE LOG
  b0 da 01 00 4f c2 a0 02      00:00:59.560  SMART RETURN STATUS
  80 44 00 00 44 57 a0 02      00:00:59.559  [VENDOR SPECIFIC]
  b0 d6 01 be 4f c2 a0 02      00:00:59.538  SMART WRITE LOG
  80 45 00 01 44 57 a0 02      00:00:59.538  [VENDOR SPECIFIC]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%       778         -
# 2  Short offline       Aborted by host               40%       777         -
# 3  Short offline       Interrupted (host reset)      90%       776         -
# 4  Short offline       Interrupted (host reset)      40%       776         -
# 5  Conveyance offline  Completed without error       00%       516         -
# 6  Conveyance offline  Completed without error       00%       496         -
# 7  Short offline       Completed without error       00%       495         -

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

```I found many forums and threads about SWNCQ and problems with its sata_nv support, but one thing I dont' understand - is it HDD bug, or kernel driver bug? I have another WD's HDD and it works 2 years without any problems.

If anybody can help - please, any ideas will be great!

P.S. SATA cabels - ok, tested. In Windows XP I dont' see any errrors in Windows Event journals. Power is ok, tested with new Chieftec 500W.

---

### Post by psusi on 2010-10-18
Hrm... I have the same drive, and I think the same controller at home and it works fine.  You say you already tried swapping the power supply?

---

### Post by Alve on 2010-10-18
> **psusi said:**
> Hrm... I have the same drive, and I think the same controller at home and it works fine.  You say you already tried swapping the power supply?

yes. This drive was working first with my previous power supply and now with new one. Power connector is good quality. I can test prev PS today to compare.

---

### Post by abuster on 2011-05-30
> **Alve said:**
> yes. This drive was working first with my previous power supply and now with new one. Power connector is good quality. I can test prev PS today to compare.

Did you ever solve this problem? I have the same problem with my WD10EARS on MCP51 SATA-controller on a ECS nForce 570 slit-a (v3.1) motherboard.

---

