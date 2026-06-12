---
title: "SMART Tools"
date: 2010-09-01
forum: Hardware
---

### Post by dillzz on 2010-09-01
Having some system stability issues.  A lot of things pointed to a bleeding edge graphics driver, but I got that resolved.  However I am having recent freezes, and crashes.  For example with konsole open i get /bin/bash crashed.  I turned on smart tools and ran against both drives, I have a WD 10,000 RPM drive as the OS drive and 7,200 RPM drive for the data.  The data drive came back fine, however I see these errors when running extensive test using gsmartcontrol.  

Any ideas on what these errors are?  Could I possibly have a disk dying? 

Complete error log:

SMART Error Log Version: 1
ATA Error Count: 5
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

Error 5 occurred at disk power-on lifetime: 406 hours (16 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 41 30 ee 89 77 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 01 30 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 28 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 20 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED

Error 4 occurred at disk power-on lifetime: 406 hours (16 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 41 28 ee 89 77 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 01 28 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 20 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 18 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED

Error 3 occurred at disk power-on lifetime: 406 hours (16 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 41 20 ee 89 77 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 01 20 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 18 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:09.700  READ LOG EXT
  60 01 10 ee 89 77 41 00      00:01:09.700  READ FPDMA QUEUED

Error 2 occurred at disk power-on lifetime: 406 hours (16 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 41 18 ee 89 77 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 01 18 ee 89 77 41 00      00:01:03.850  READ FPDMA QUEUED
  2f 00 01 10 00 00 40 00      00:01:03.850  READ LOG EXT
  60 01 10 ee 89 77 41 00      00:01:03.850  READ FPDMA QUEUED
  e1 00 00 00 00 00 40 00      00:01:03.850  IDLE IMMEDIATE
  ef 10 02 00 00 00 40 00      00:01:03.850  SET FEATURES [Reserved for Serial ATA]

Error 1 occurred at disk power-on lifetime: 406 hours (16 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 41 10 ee 89 77 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 01 10 ee 89 77 41 00      00:00:55.350  READ FPDMA QUEUED
  e1 00 00 00 00 00 40 00      00:00:55.350  IDLE IMMEDIATE
  ef 10 02 00 00 00 40 00      00:00:55.350  SET FEATURES [Reserved for Serial ATA]
  ef 03 46 00 00 00 40 00      00:00:55.350  SET FEATURES [Set transfer mode]
  c6 00 10 00 00 00 40 00      00:00:55.350  SET MULTIPLE MODE

---

### Post by dillzz on 2010-09-01
bump

---

