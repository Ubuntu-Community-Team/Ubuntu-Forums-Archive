---
title: "Gsmartcontrol noob"
date: 2012-01-01
forum: Hardware
---

### Post by Wagzle on 2012-01-01
Hi.. 
I guess first off, I have an external hdd with mac os x on it that will no longer start up. It worked fine for about 9 months or so, booting through usb, but now it doesn't get past the white screen on start up (after the drive is recognized and selected through the rEFIt program). 

That being said, I downloaded GSmartControl on my new computer with Ubuntu (Woo!) to see if I could somehow repair my old hdd. Long story short, I did some tests and got this output:

```

Complete error log:

SMART Error Log Version: 1
ATA Error Count: 2820 (device log contains only the most recent five errors)
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

Error 2820 occurred at disk power-on lifetime: 4467 hours (186 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 77 da e8  Error: UNC 8 sectors at LBA = 0x08da7738 = 148535096

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 77 da e0 00      01:22:03.100  READ DMA EXT
  35 00 00 fe f0 0f e0 00      01:22:03.100  WRITE DMA EXT
  25 00 10 78 17 07 e0 00      01:22:03.100  READ DMA EXT
  ef 03 46 00 00 00 a0 00      01:22:03.100  SET FEATURES [Set transfer mode]
  25 00 08 38 77 da e8 04      01:22:03.000  READ DMA EXT

Error 2819 occurred at disk power-on lifetime: 4467 hours (186 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 77 da e8  Error: UNC 8 sectors at LBA = 0x08da7738 = 148535096

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 77 da e0 00      01:21:59.300  READ DMA EXT
  35 00 08 00 82 8d e0 00      01:21:59.300  WRITE DMA EXT
  25 00 10 18 e4 17 e0 00      01:21:59.300  READ DMA EXT
  35 00 08 e0 e4 f9 e0 00      01:21:59.300  WRITE DMA EXT
  35 00 08 90 e4 f9 e0 00      01:21:59.300  WRITE DMA EXT

Error 2818 occurred at disk power-on lifetime: 4467 hours (186 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 77 da e8  Error: UNC 8 sectors at LBA = 0x08da7738 = 148535096

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 77 da e0 00      01:21:55.500  READ DMA EXT
  25 00 10 98 73 07 e0 00      01:21:55.500  READ DMA EXT
  35 00 08 80 78 ad e0 00      01:21:55.500  WRITE DMA EXT
  35 00 08 08 e0 f9 e0 00      01:21:55.500  WRITE DMA EXT
  35 00 08 f8 df f9 e0 00      01:21:55.500  WRITE DMA EXT

Error 2817 occurred at disk power-on lifetime: 4467 hours (186 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 77 da e8  Error: UNC 8 sectors at LBA = 0x08da7738 = 148535096

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 77 da e0 00      01:21:51.600  READ DMA EXT
  25 00 10 d8 2e 07 e0 00      01:21:51.600  READ DMA EXT
  ef 03 46 00 00 00 a0 00      01:21:51.600  SET FEATURES [Set transfer mode]
  25 00 08 38 77 da e8 04      01:21:51.500  READ DMA EXT
  25 00 08 38 77 da e0 00      01:21:47.700  READ DMA EXT

Error 2816 occurred at disk power-on lifetime: 4467 hours (186 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 77 da e8  Error: UNC 8 sectors at LBA = 0x08da7738 = 148535096

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 77 da e0 00      01:21:47.700  READ DMA EXT
  25 00 10 98 e0 17 e0 00      01:21:47.700  READ DMA EXT
  ef 03 46 00 00 00 a0 00      01:21:47.700  SET FEATURES [Set transfer mode]
  25 00 08 38 77 da e8 04      01:21:47.600  READ DMA EXT
  25 00 08 38 77 da e0 00      01:21:43.900  READ DMA EXT

```So I guess I was wondering if someone could tell me what this means, or even better tell me where the best place would be to learn what I'm reading.

Thanks

---

