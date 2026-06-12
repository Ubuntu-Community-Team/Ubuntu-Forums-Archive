---
title: "Hard drive problems"
date: 2009-07-05
forum: Hardware
---

### Post by CP1256 on 2009-07-05
Hello everyone.

Just a few minutes ago I was running Ubuntu without problems, until it just rebooted out of nowhere. After failing to boot, I went to a terminal and I saw an ATA error. 

After letting the computer rest for a few minutes, I booted up the Ubuntu livecd, installed smartmontools and checked the smart values. Nothing has changed, except Current_Pending_Sector is now 1 instead of 0. After running a short test, this is what comes out:

> # 1  Short offline       Completed: read failure       90%      2018         33735180


I also saw this with smartmontools;

> Error 7 occurred at disk power-on lifetime: 2018 hours (84 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 0c c2 02 e2  Error: UNC at LBA = 0x0202c20c = 33735180

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 07 c2 02 02 0a      00:01:07.334  READ DMA
  c8 00 a0 2f c1 fc 01 0a      00:01:07.324  READ DMA
  c8 00 28 ff c0 fc 01 0a      00:01:07.323  READ DMA
  c8 00 30 4f c0 fc 01 0a      00:01:07.323  READ DMA
  c8 00 08 3f c0 fc 01 0a      00:01:07.315  READ DMA


Error 6 occurred at disk power-on lifetime: 2018 hours (84 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 0c c2 02 e2  Error: UNC at LBA = 0x0202c20c = 33735180

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 07 c2 02 02 0a      00:01:04.141  READ DMA
  ec 00 00 00 00 00 00 0a      00:01:04.133  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:01:04.133  SET FEATURES [Set transfer mode]


Strangely the drive is only a few months old, it's a WD5000AAKS. I have a Pentium 4 processor with a 300 Watt PSU and I was stressing the processor for about an hour or two, so my first thought was that the PSU couldn't handle it.

Is there any way I could fix this?

Edit: I'm running a offline test now which will finish in about an hour.

---

