---
title: "DIsk Utility test problems"
date: 2013-04-28
forum: Hardware
---

### Post by HDTimeshifter on 2013-04-28
> **psusi said:**
> It takes however long the drive needs to complete the test.  For a TB class drive, this should be quite a few hours.  There is a progress bar.

I tried running the test on a new 2TB drive, however the progress bar reaches about 75% and never seems to go further. I've let it run for several days and turned off hibernation so it will keep running. I'm concerned because Western Digital's utility fails it with too many bad blocks, but the Disk Utility says the smart data says it's ok.

---

### Post by ahallubuntu on 2013-04-28
~

---

### Post by HDTimeshifter on 2013-04-28
I ran the GSmartControl and the pink numbers don't look significant. It's strange that SMART data is all green, but WD's quick test fails on the SMART data and the extended test fails with too many bad blocks. Anyway I bought this April 1, and after running tests the first week, formatted it with Ubuntu and tried copying lots of data (GBs of photos), which sometimes works, but other times I get a read-only error and after that error tried unmounting and remounting, but get an error trying to remount. This drive seems to cause many problems even when not reading/writing files to it as my PC becomes very sluggish and appears locked up at times. I went ahead and requested a RMA from WD. Can't believe they don't have quality control worth a sh*t! I've read a lot of reviews on Newegg about DOA drives and high failure rates, but couldn't believe WD would have that high a failure rate. I buy WD because I've never had one fail (even dozens of old 40GB IDEs) and had lots of problems with Seagate from way back in the early days of 10MB externals (late 80s Macs!).

---

### Post by cariboo on 2013-04-28
Moved to a thread of it's own, as is right and proper.

---

### Post by HDTimeshifter on 2013-04-28
Also ran the GSmartControl quick tests which failed on this drive. They all pass on my other 2 drives (750 GB WD and 1 TB Hitachi).

---

### Post by ahallubuntu on 2013-04-28
~

---

### Post by HDTimeshifter on 2013-04-28
Already requested RMA, but here are the pink line items:
[FONT=Courier New]
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   198   198   140    Pre-fail  Always       -       88
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       31
[/FONT][FONT=Courier New]
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   198   198   140    Pre-fail  Always       -       88
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       31
[/FONT][FONT=Courier New]
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   198   198   140    Pre-fail  Always       -       88
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       31
[/FONT]

---

