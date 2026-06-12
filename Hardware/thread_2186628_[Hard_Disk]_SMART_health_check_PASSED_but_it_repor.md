---
title: "[Hard Disk] SMART health check PASSED but it reports errors ?!"
date: 2013-11-08
forum: Hardware
---

### Post by grigio2 on 2013-11-08
Hi, after the command:
```
sudo smartctl -a /dev/sda
```

I get:
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

...

SMART Error Log Version: 1
ATA Error Count: 2
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


Error 2 occurred at disk power-on lifetime: 12349 hours (514 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5a 3c 07 01  Error: UNC at LBA = 0x01073c5a = 17251418


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 d7 3b 07 41 00      00:01:04.995  READ FPDMA QUEUED
  60 00 08 ff 3b 07 41 00      00:01:04.995  READ FPDMA QUEUED
  60 00 08 0f 3c 07 41 00      00:01:04.995  READ FPDMA QUEUED
  60 00 08 3f 3c 07 41 00      00:01:04.994  READ FPDMA QUEUED
  60 00 08 47 3c 07 41 00      00:01:04.994  READ FPDMA QUEUED


Error 1 occurred at disk power-on lifetime: 12349 hours (514 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5a 3c 07 01  Error: UNC at LBA = 0x01073c5a = 17251418


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 5f 3c 07 41 00      00:00:56.735  READ FPDMA QUEUED
  60 00 08 07 e0 06 41 00      00:00:56.367  READ FPDMA QUEUED
  60 00 08 ff df 06 41 00      00:00:56.367  READ FPDMA QUEUED
  60 00 08 f7 df 06 41 00      00:00:56.367  READ FPDMA QUEUED
  60 00 08 ef df 06 41 00      00:00:56.366  READ FPDMA QUEUED


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12806         -
# 2  Extended offline    Completed without error       00%     12614         -
# 3  Extended offline    Aborted by host               90%     12612         -
# 4  Extended offline    Aborted by host               90%     12612         -
# 5  Extended offline    Aborted by host               90%     12612         -
# 6  Extended offline    Aborted by host               90%     12612         -
# 7  Short offline       Completed without error       00%         0         -


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

What do you think, it good or bad? tnx

---

### Post by tgalati4 on 2013-11-08
DMA Read errors could be a cable problem or controller problem on the motherboard.  Try reseating connections.  12.8K hours is a lot for a spinner.  Although I have a few disks that are pushing 50K hours.  Back up your data regardless.  Check the tightness of the power connector.  They can wiggle lose over time.  Any power outages during the last week?

---

