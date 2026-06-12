---
title: "LBA reported wrong with Fujitsu disk"
date: 2020-01-24
forum: Hardware
---

### Post by hstoellinger on 2020-01-24
Hello,
I use the smartmontools (smartctl) to check the health of the FUJITSU MHZ2320B  disk on my Sony VIAO laptop. 
It keeps reporting as shown below. By the way, I am on Kubuntu 19.10.
The disk has a capacity of 300GB. I tried to follow various tutorials to ascertain where the defective block exactly is. 
However, as I understand it, LBA 0x1a7a008f5f = 113716006751 seems to be far beyond the the disk's capacity. 
Do I miss something or might this be a bug in the firmware for the disk, which reports a wrong LBA.
Thanks for any hints.
H. Stoellinger, Salzburg

```

  Error 19 [18] occurred at disk power-on lifetime: 11161 hours (465 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.
  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 41 00 03 00 1a 7a 00 8f 5f 40 00  Error: UNC at LBA = 0x1a7a008f5f = 113716006751

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 fc 00 00 00 1a 79 00 8f 64 40 00     03:30:34.137  READ FPDMA QUEUED
  2f 00 00 00 01 00 00 00 00 00 10 40 00     03:30:34.016  READ LOG EXT
  60 00 fc 00 f8 00 1a 79 00 8f 64 40 00     03:30:29.348  READ FPDMA QUEUED
  ef 00 03 00 45 00 00 00 00 00 00 40 00     03:30:28.354  SET FEATURES [Set transfer mode]
  c6 00 00 00 10 00 00 00 00 00 00 40 00     03:30:28.354  SET MULTIPLE MODE

```

---

