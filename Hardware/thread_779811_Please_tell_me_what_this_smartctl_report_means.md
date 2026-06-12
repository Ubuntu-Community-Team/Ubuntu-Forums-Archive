---
title: "Please tell me what this smartctl report means:"
date: 2008-05-03
forum: Hardware
---

### Post by Keyper7 on 2008-05-03
Hi all,

I just saw that smartctl gave me the following report for my SAMSUNG HM160HI:

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       7
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       1937
  4 Start_Stop_Count        0x0032   079   079   000    Old_age   Always       -       213145
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1764
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       283
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2276
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       31
194 Temperature_Celsius     0x0022   127   094   000    Old_age   Always       -       37 (Lifetime Min/Max 22/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       101985
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       793
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       2508
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

```

There seems to be some scary stuff there, such as the insanely high values for Start_Stop_Count and Reallocated_Event_Count and the high value for Offline_Uncorrectable. My laptop is a Dell Vostro 1400 and only a couple of months old. I didn't notice any failures and both fsck and badblocks report no problems at all. How worried should I be?

---

### Post by Keyper7 on 2008-05-03
Guys?

Sorry for bumping this, but I'm very worried.

---

### Post by Whiffle on 2008-05-03
I think its likely those numbers are incorrect for some reason or another.  The start/stop on my 6 year old desktop is 1067, and my laptop is 4882, and its only a year or so old.  Neither of my computers have the other number.  I'd do some googling and look for some information on what these counts are before I get all worried.

---

### Post by Keyper7 on 2008-05-03
Thanks, Whiffle.

By the way, I'm also wondering why there's no Load_Cycle_Count listed.
How can I know if I'm suffering from the infamous head parking problem if it's not listed?

Can someone shed a light on this?

---

### Post by Keyper7 on 2008-05-03
Okay, I'm getting more and more confused...

If I understood correctly, the VALUE field is nothing more than a normalized version of RAW VALUE. So why the RAW VALUE of Reallocated_Event_Count, Current_Pending_Sector and Offline_Uncorrectable are increasing quite rapidly while VALUE stays unaltered?

Need some help from a S.M.A.R.T. expert...

---

