---
title: "SMARTS and hard drive health"
date: 2010-09-05
forum: Hardware
---

### Post by Filmorependrgn on 2010-09-05
I have a ~6 year old Dell Inspiron 630m that's been running Ubuntu for a few years. For legacy sake, I thought I'd share my recent hard drive experience with the community.

```
Model Family:     Toshiba 2.5" HDD Series (30-60GB)
Device Model:     TOSHIBA MK4026GAX
Serial Number:    XXREDACTEDXX
Firmware Version: PA102D
```

This machine has seen daily use for the past half decade, and has accrued the following stats from SMARTS:

```
Start_Stop_Count:    10782
Power_On_Hours:      14148
Power_Cycle_Count:   10706
Load_Cycle_Count:    358501
Loaded_Hours:        12574
Temperature_Celsius: 48 (Lifetime Min/Max 10/55)
ATA Error Count:     775

```

For this particular drive, the power on hours and Load cycle count are down to "65" starting from whatever value TOSHIBA designates.

Until this year, I only ever had one instance of read problems from bad sectors. This year I've had ~3. (Also the metal frame that holds the display on the laptop has fractured). They have always been recoverable through fsck or other, more aggressive methods (using dd to force a write to the bad sector causing it to "relocate").

Nothing in particular to say about it other than Yes, I have backed up my data.

---

