---
title: "Hard Drive issues and load count Hardy"
date: 2008-04-26
forum: Hardware
---

### Post by revelationman on 2008-04-26
I check to see if the Hard Drive was resolved with Hardy and maybe I am wrong but it appears that the issue is still there. I have submitted this to bug report but this is very serious. 

What is sad is that Hardy is very smooth boot times are great my laptop does not get hot like it did and then this nonsense with the hard drive still rears it's ugly head.

So if you do see anything that I missed or did wrong please advise me if I am correct sadly I will go back to Windows XP which I really do not want to.

Maybe I am not doing this right but here is my stats

 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 32851
 Power_On_Hours 0x0032 100 100 000 Old_age Always - 378

You can get the average per hour by the following division:
Load_Cycle_Count / Power_On_Hours

That works out to 86.907407407 YIKES !!!!

Just in case I did it wrong I will post my entire results

=== START OF INFORMATION SECTION ===
Device Model: ST9120822AS
Serial Number: 5LZ34Z5F
Firmware Version: 3.ALB
User Capacity: 120,034,123,776 bytes
Device is: Not in smartctl database [for details use: -P showall]
ATA Version is: 7
ATA Standard is: Exact ATA specification draft version not indicated
Local Time is: Sat Apr 26 08:46:19 2008 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status: (0x82) Offline data collection activity
     was completed without error.
     Auto Offline Data Collection: Enabled.
Self-test execution status: ( 25) The self-test routine was aborted by
     the host.
Total time to complete Offline
data collection: ( 426) seconds.
Offline data collection
capabilities: (0x5b) SMART execute Offline immediate.
     Auto Offline data collection on/off support.
     Suspend Offline collection upon new
     command.
     Offline surface scan supported.
     Self-test supported.
     No Conveyance Self-test supported.
     Selective Self-test supported.
SMART capabilities: (0x0003) Saves SMART data before entering
     power-saving mode.
     Supports SMART auto save timer.
Error logging capability: (0x01) Error logging supported.
     No General Purpose Logging support.
Short self-test routine
recommended polling time: ( 1) minutes.
Extended self-test routine
recommended polling time: ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate 0x000f 100 253 006 Pre-fail Always - 0
  3 Spin_Up_Time 0x0003 099 099 000 Pre-fail Always - 0
  4 Start_Stop_Count 0x0032 100 100 020 Old_age Always - 242
  5 Reallocated_Sector_Ct 0x0033 100 100 036 Pre-fail Always - 0
  7 Seek_Error_Rate 0x000f 069 060 030 Pre-fail Always - 9499978
  9 Power_On_Hours 0x0032 100 100 000 Old_age Always - 378
 10 Spin_Retry_Count 0x0013 100 100 034 Pre-fail Always - 0
 12 Power_Cycle_Count 0x0032 100 100 020 Old_age Always - 219
187 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 0
189 Unknown_Attribute 0x003a 100 100 000 Old_age Always - 0
190 Temperature_Celsius 0x0022 067 050 045 Old_age Always - 588447777
192 Power-Off_Retract_Count 0x0032 100 100 000 Old_age Always - 140
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 32851
194 Temperature_Celsius 0x0022 033 050 000 Old_age Always - 33 (Lifetime Min/Max 0/16)
195 Hardware_ECC_Recovered 0x001a 083 064 000 Old_age Always - 193176778
197 Current_Pending_Sector 0x0012 100 100 000 Old_age Always - 2
198 Offline_Uncorrectable 0x0010 100 100 000 Old_age Offline - 2
199 UDMA_CRC_Error_Count 0x003e 200 199 000 Old_age Always - 147
200 Multi_Zone_Error_Rate 0x0000 100 253 000 Old_age Offline - 0
202 TA_Increase_Count 0x0032 100 253 000 Old_age Always - 0

SMART Error Log Version: 1
ATA Error Count: 147 (device log contains only the most recent five errors)
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

Error 147 occurred at disk power-on lifetime: 177 hours (7 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 23 02 63 7f e0 Error: ABRT at LBA = 0x007f6302 = 8348418

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
  -- -- -- -- -- -- -- -- ---------------- --------------------
  24 00 40 e5 62 7f e0 00 00:44:11.540 READ SECTOR(S) EXT
  24 00 10 45 eb 7d e0 00 00:44:11.532 READ SECTOR(S) EXT
  24 00 08 7d c7 7d e0 00 00:44:11.527 READ SECTOR(S) EXT
  24 00 08 c5 b7 87 e0 00 00:44:11.519 READ SECTOR(S) EXT
  24 00 08 0d af 87 e0 00 00:44:11.509 READ SECTOR(S) EXT

Error 146 occurred at disk power-on lifetime: 177 hours (7 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 1f 10 7c f2 e1 Error: ICRC, ABRT 31 sectors at LBA = 0x01f27c10 = 32668688

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
  -- -- -- -- -- -- -- -- ---------------- --------------------
  c8 00 80 af 7b f2 e1 00 01:08:41.903 READ DMA
  c8 00 80 2f 7b f2 e1 00 01:08:41.898 READ DMA
  c8 00 80 af 7a f2 e1 00 01:08:41.897 READ DMA
  c8 00 80 2f 7a f2 e1 00 01:08:41.892 READ DMA
  c8 00 80 af 79 f2 e1 00 01:08:41.891 READ DMA

Error 145 occurred at disk power-on lifetime: 177 hours (7 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 1f 40 c7 6b e1 Error: ICRC, ABRT 31 sectors at LBA = 0x016bc740 = 23840576

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
  -- -- -- -- -- -- -- -- ---------------- --------------------
  c8 00 80 df c6 6b e1 00 01:06:04.477 READ DMA
  c8 00 80 5f c6 6b e1 00 01:06:04.469 READ DMA
  c8 00 80 df c5 6b e1 00 01:06:04.428 READ DMA
  c8 00 80 5f c5 6b e1 00 01:06:04.427 READ DMA
  c8 00 80 5f c3 6b e1 00 01:06:04.421 READ DMA

Error 144 occurred at disk power-on lifetime: 177 hours (7 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 fe 49 73 e2 Error: ICRC, ABRT at LBA = 0x027349fe = 41110014

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
  -- -- -- -- -- -- -- -- ---------------- --------------------
  c8 00 80 7f 49 73 e2 00 01:05:28.061 READ DMA
  c8 00 80 ff 48 73 e2 00 01:05:28.056 READ DMA
  c8 00 80 7f 48 73 e2 00 01:05:28.055 READ DMA
  c8 00 80 ff 47 73 e2 00 01:05:28.050 READ DMA
  c8 00 80 7f 47 73 e2 00 01:05:28.049 READ DMA

Error 143 occurred at disk power-on lifetime: 176 hours (7 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 4f 18 70 b2 e2 Error: ICRC, ABRT 79 sectors at LBA = 0x02b27018 = 45248536

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC Powered_Up_Time Command/Feature_Name
  -- -- -- -- -- -- -- -- ---------------- --------------------
  c8 00 80 e7 6f b2 e2 00 00:52:21.492 READ DMA
  c8 00 80 67 6f b2 e2 00 00:52:21.480 READ DMA
  c8 00 80 e7 6e b2 e2 00 00:52:21.475 READ DMA
  c8 00 80 67 6e b2 e2 00 00:52:21.470 READ DMA
  c8 00 80 e7 6d b2 e2 00 00:52:21.465 READ DMA

SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Extended offline Aborted by host 90% 182 -
# 2 Short offline Completed without error 00% 182 -
# 3 Extended offline Aborted by host 90% 182 -

SMART Selective self-test log data structure revision number 1
 SPAN MIN_LBA MAX_LBA CURRENT_TEST_STATUS
    1 0 0 Not_testing
    2 0 0 Not_testing
    3 0 0 Not_testing
    4 0 0 Not_testing
    5 0 0 Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
Actions

---

### Post by quanumphaze on 2008-04-26
You are not alone.

I used ubuntu_demon's [ugly hack]("http://ubuntuforums.org/showthread.php?t=591503&highlight=Load_Cycle_Count") to fix this problem in Gutsy. I also hoped that the problem was fixed in Hardy.

This isn't just a minor bug affecting only some users. This is a serious risk of data loss, and should have been a top priority.

Let's hope it's fixed by Ubuntu 12.4

---

### Post by JimmyK377 on 2008-04-26
Does the gutsy ugly fix still actually work in Hardy? I haven't seen a firm answer to this.

---

### Post by revelationman on 2008-04-26
> **JimmyK377 said:**
> Does the gutsy ugly fix still actually work in Hardy? I haven't seen a firm answer to this.

sorry i am  not going to do a hack on this laptop sadly it seems the issue has not been dealt with

i have submitted my report to bug team

---

### Post by _Stevie_ on 2008-04-30
im a bit concerned about this.
i executed
```
sudo smartctl -a /dev/hda | grep Load_Cycle_Count
```

and it gave me the following data:

```
193 Load_Cycle_Count        0x0032   197   197   000    Old_age   Always       -       11466

```

i have problems interpreting these values. am i affected by the issue?

---

### Post by jimv on 2008-04-30
This doesn't seem like a big issue to me.  If you're averaging 80 load cycles per hour, and you use your laptop for 8 hours a day, 365 days per year, your HD should last about 2.5 years (based on a 600,000 load cycle rating on the drive.)

2.5 years seems about what I would expect out of a laptop drive.

---

### Post by _Stevie_ on 2008-04-30
thanks jimv!

good to know :)

what is the value i should pay attention to?

---

### Post by jimv on 2008-05-01
Load_Cycle_Count divided by Power_on_Hours = Load Cycles per hour.  According to some document I read, a laptop harddrive can take about 600,000 load cycles before failing.  So divide 600,000 by whatever number you get for the Load Cyles per hour, and that will tell you how many hours your hard drive *should* last.

---

### Post by _Stevie_ on 2008-05-01
okay thanks!

i thought the 193 is the number to pay attention :D
realized now that it is the 11xxx.

cheers,

stevie

---

