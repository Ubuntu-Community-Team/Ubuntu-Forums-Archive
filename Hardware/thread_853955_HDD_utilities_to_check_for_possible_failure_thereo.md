---
title: "HDD utilities to check for possible failure thereof."
date: 2008-07-09
forum: Hardware
---

### Post by TheAJKMan on 2008-07-09
Hi there guys.

I'm possibly facing a hdd failure as there seems to be problems the last few boot times. I've gotten a BIOS message saying something about impending failure/not detecting the HDD. It takes a couple of reboots and I can get in and there don't appear to be any problems. My concern is that if it is going to happen, is there any  kind of utility in Ubuntu that I can install that can check the HDD status and determine it's overall "health" and hence if there actually is an impending death on my hands. I have taken the precaution of backing up all the info I do not want to loose onto the slaved HDD, just in case. I have learnt that much at least :)

---

### Post by sdennie on 2008-07-09
There is.  Try:

```

sudo apt-get install smartmontools

```

Then, to check the disk, try:

```

sudo smartctl --all /dev/sda

```

(Assuming /dev/sda is the disk you want to check)

---

### Post by hardyn on 2008-07-09
hard disks are too cheap right now to gamble with potential hard disk failures.  If you are getting bios post warnings... your drive probably has/is failed/failing... just replace it and be done with it.

---

### Post by TheAJKMan on 2008-07-09
hardyn, had I the money to spare, I would do it without hesitation, that and have the mobo checked as well. But, alas, finances are scarcer than hens teeth in my household at the moment. And as my Linux HDD are separate from my windows ones, it would be an anooyance at best should it crash.

vor, I'm going to try that now and get back to you on how succcesful that was :) Thanks for that suggestion, is appreciated.

---

### Post by TheAJKMan on 2008-07-09
Okay, here is part of the log and I'm not sure I understand what it means....

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   166   160   021    Pre-fail  Always       -       2675
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       933
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6538
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       911
194 Temperature_Celsius     0x0022   111   088   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       123
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

---

### Post by TheAJKMan on 2008-07-09
Would I be correct in interpreting the above as stating that the drive is on it's way out??

---

### Post by Qinjuehang on 2008-07-09
Try "sudo smartctl -t offline". You will get the time required for the test to finish. When it does, run "sudo smartctl -l selftest /dev/sda"

Assuming your disk is sda

---

