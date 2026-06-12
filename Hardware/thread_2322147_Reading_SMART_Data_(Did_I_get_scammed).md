---
title: "Reading SMART Data (Did I get scammed?)"
date: 2016-04-26
forum: Hardware
---

### Post by amethyst2 on 2016-04-26
I just received a "new" hard drive in the mail yesterday. "New" is in quotation marks because I'm unsure of the seller's claims. The first red flag was that it did not come in manufacturer packaging. Fine; maybe the seller didn't want to take up that space in shipping. The next red flag was the manufacture date on the label says, "24 DEC 2010." Sure, "new" in terms of electronic hardware sales is not necessarily a description of its manufacture date, but rather a description of how much(rather, how little) it has been used; but I have a hard time believing a 2TB HDD sat in a small retailer's stock for 5 years without being sold nor used.  I immediately decided to look into the SMART data, but quickly realized I don't know what I'm looking at.  It says "passed," but AFAIK, that only tells whether it's suitable for use, not whether it's in new condition.  If I'm reading the other data correctly, I think I should be alarmed by the column of "pre-fail" and "old_age" under "Vendor Specific SMART Attributes with Thresholds."  Please look over the results and verify my findings.  If this is in fact not a new disk and on the brink of failure, I need to contact the seller to demand a refund immediately.

```
# smartctl -a /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-35-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD2003FYPS-27Y2B0
Serial Number:    WD-WCAVY6441781
LU WWN Device Id: 5 0014ee 205613fbc
Firmware Version: 04.05G11
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Tue Apr 26 12:58:55 2016 EDT
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
data collection:         (43260) seconds.
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
recommended polling time:      ( 492) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   249   243   021    Pre-fail  Always       -       9525
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       46
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   063   063   000    Old_age   Always       -       27661
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       43
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       40
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       5
194 Temperature_Celsius     0x0022   127   112   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1


SMART Error Log Version: 1
ATA Error Count: 1
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


Error 1 occurred at disk power-on lifetime: 27545 hours (1147 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 81 f4 2c 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d4 00 81 4f c2 00 00      00:01:49.474  SMART EXECUTE OFF-LINE IMMEDIATE


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     27660         -
# 2  Extended offline    Completed without error       00%     27639         -
# 3  Short offline       Completed without error       00%     27561         -
# 4  Extended offline    Completed without error       00%     27561         -
# 5  Short captive       Completed: read failure       80%     27545         -
# 6  Short offline       Completed without error       00%     27545         -
# 7  Short offline       Completed: read failure       80%     27545         -
# 8  Short offline       Completed: read failure       80%     27545         -
# 9  Short offline       Completed without error       00%     27545         -
#10  Short offline       Completed without error       00%     26809         -
#11  Short offline       Completed without error       00%     23382         -
#12  Short offline       Completed without error       00%         0         -
#13  Short offline       Completed without error       00%         0         -
#14  Short offline       Completed without error       00%         0         -
3 of 3 failed self-tests are outdated by newer successful extended offline self-test # 2


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

### Post by weatherman2 on 2016-04-26
No, you should not be alarmed by the column that says "pre-fail."  That's the type of S.M.A.R.T. attribute it is.  Even a brand new drive will show these types of attributes.  What matters is the value of the attribute, not the type of attribute it is.

What SHOULD alarm you (and confirm your suspicions) is, first of all, the RAW value of attribute #9: 

```

9 Power_On_Hours 0x0032 063 063 000 Old_age Always - 27661

```

The drive has been used for 27,661 hours.  Should be closer to 0, obviously (but an hour or two of use is normal - for testing, etc.).

Also, a S.M.A.R.T. error was recorded at 27,545 hours:

```
Error 1 occurred at disk power-on lifetime: 27545 hours (1147 days + 17 hours)
When the command that caused the error occurred, the device was active or idle.




After command completion occurred, registers were:
ER ST SC SN CL CH DH
-- -- -- -- -- -- --
04 51 00 81 f4 2c 00 Error: ABRT




Commands leading to the command that caused the error were:
CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
-- -- -- -- -- -- -- -- ---------------- --------------------
b0 d4 00 81 4f c2 00 00 00:01:49.474 SMART EXECUTE OFF-LINE IMMEDIATE

```

Send the drive back for a refund.  If you used Paypal or a credit card to pay, you can always dispute the charge if they refuse.

---

### Post by amethyst2 on 2016-04-26
Thank you very much.

---

### Post by amethyst2 on 2016-04-26
> **weatherman2 said:**
> Send the drive back for a refund.  If you used Paypal or a credit card to pay, you can always dispute the charge if they refuse.
I ALWAYS use PayPal to buy electronic equipment online and only buy equipment guaranteed to arrive long before the deadline to file a claim specifically because of things like this. I'm going to insist that the seller pay the cost of shipping it back. They usually give a refund and decline to take the product back because they know that the literal trash they sent me is not worth what it costs to ship it.

---

### Post by amethyst2 on 2016-04-26
Just an interesting note... At first, I thought maybe it had been used as a workstation for an average of 14 hours a day, but then after realizing what I'm looking at, only 43 power cycles tells me that it's more likely to have been used continuously in a network server for 3 years and 1 month.  Do you agree with this?

---

### Post by weatherman2 on 2016-04-26
Yeah, that sounds likely.  I have had servers that stayed up for 2+ years or more.

---

