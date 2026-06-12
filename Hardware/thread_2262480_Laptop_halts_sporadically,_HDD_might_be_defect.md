---
title: "Laptop halts sporadically, HDD might be defect?"
date: 2015-01-25
forum: Hardware
---

### Post by shizow on 2015-01-25
My laptop halts some times (maybe 2 times a week since 2-3 weeks)
The last time the laptop could not start up, because the journal of ext4 was damaged. I repaired that, now laptop runs again.

smartctl -a /dev/sda 
gives the outout below

what is wrong with the HDD?
better get a new one?

```

Error 14 occurred at disk power-on lifetime: 5740 hours (239 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 88 0e 0c 0c  Error: UNC at LBA = 0x0c0c0e88 = 202116744

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 88 0e 0c 40 00      00:09:22.175  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:09:22.175  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:09:22.175  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:09:22.174  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:09:22.174  SET FEATURES [Set transfer mode]

```

Full output
[ATTACH]259489[/ATTACH]

---

### Post by westie457 on 2015-01-25
Hi the smart report looks okay, maybe not perfect but no real need to panic at the moment.
I suggest you run a Memtest to see if that is failing. Faulty RAM can cause computer lock-ups and/or unexpected restarts.

---

### Post by tgalati4 on 2015-01-25
UNC's are uncorrectable sectors.  A large disk will have a few of those on its magnetic surface.  As long as you don't have an increasing number of UNC's and your disk's mechanical and electrical components are working, then you should be OK.  

Back up your data, run a long test:

```
sudo smartctl -t long /dev/sda
```

To review the results (and post them):

```
sudo smartctl -a /dev/sda
```

Of course, a laptop that has lockups is unacceptable; there may be something else going on.  Perhaps a power problem, like a bad battery that is causing the disk to have problems.  Keep an open mind when troubleshooting, many times the obvious problem is not the root cause.

---

