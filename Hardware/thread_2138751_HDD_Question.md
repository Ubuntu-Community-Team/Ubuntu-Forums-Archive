---
title: "HDD Question"
date: 2013-04-25
forum: Hardware
---

### Post by roly33 on 2013-04-25
I've done a S.M.A.R.T Test on my Notebook HDD and got this output:

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   200   200   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       2363
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   092   092   000    Old_age   Always       -       3556
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       2289
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       140
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       17738
194 Temperature_Celsius     0x0002   144   144   000    Old_age   Always       -       38 (Min/Max 8/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

Does this mean that my HDD needs replacing, it's the original one that came in my Toshiba Satellite C660-15R that I've had since Nov/Dec 2010?

Roland

---

### Post by TheFu on 2013-04-25
Turns out that SMART data can't really be used to tell if a drive is failing unless it tells you specifically that it is failing. Most of the time, that is much to late to do anything useful.
The only way to use SMART data is to watch how it changes over time - perhaps weekly - then compare the changes from week to week. This **can** be a useful indicator of a pending drive failure.

For most people, it is easier to just have good, automatic, daily, versioned, backups and not bother with reading "tea leaves" which may or may not be correct.
Backups solve many more problems than just data loss and we all know that we should be backing up our data constantly anyway.

Personally, I do replace HDDs holding critical data periodically. Crucial data is also stored on a RAID system, so a single failure doesn't prevent access and I backup the data to another device.  For me, the data is worth more than the computer. Computers can be replaced, but data cannot.  **If you don't have at least 3 copies of your important data, then you really don't have any copies.** That is a quote from someone much smarter than me.

If you really care about your data, you'd also run only LTS releases, IMHO.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by roly33 on 2013-04-25
> **ahallubuntu said:**
> These two Attributes are the only ones that look significant for your drive.  They mean that one sector failed and was marked "do not use" by the drive firmware but was replaced by a spare sector on the drive (every modern hard drive has at least a few spare sectors).

One failed sector on a drive that old isn't alarming - but it means you should keep an eye on the drive and make regular backups.  If the number of reallocated sectors continues to rise, that means more sectors are failing and the drive is probably failing and should be replaced.

Should you replace it now?  I wouldn't call it urgent, but maybe this is a good excuse to upgrade now to a faster drive or an SSD?  Prices come down all the time and/or size goes up.

I keep everything synced with my Ubuntu 1 Account, so everything is backed up more or less as something gets added or a document is changed.

SSD's seem a little bit over priced for a smaller disk at the moment, so if it starts to get really bad I might end up going for a 1TB HDD until the price of an SSD becomes mor comparible to prices (but then again ebay probably isn't the best place to look for an SSD due to some sellers trying to get rich quick).

Roland

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by roly33 on 2013-04-25
> **TheFu said:**
> Turns out that SMART data can't really be used to tell if a drive is failing unless it tells you specifically that it is failing. Most of the time, that is much to late to do anything useful.
The only way to use SMART data is to watch how it changes over time - perhaps weekly - then compare the changes from week to week. This **can** be a useful indicator of a pending drive failure.

For most people, it is easier to just have good, automatic, daily, versioned, backups and not bother with reading "tea leaves" which may or may not be correct.
Backups solve many more problems than just data loss and we all know that we should be backing up our data constantly anyway.

Personally, I do replace HDDs holding critical data periodically. Crucial data is also stored on a RAID system, so a single failure doesn't prevent access and I backup the data to another device.  For me, the data is worth more than the computer. Computers can be replaced, but data cannot.  **If you don't have at least 3 copies of your important data, then you really don't have any copies.** That is a quote from someone much smarter than me.

If you really care about your data, you'd also run only LTS releases, IMHO.

Everything that is important is backed up to Ubuntu 1, Google Drive and my Sky Drive as well as being on a HDD attached to my Router and then the physical copies that I use regular are on my HDD so I think I'm well and truly backed up for any HDD problem.

Roland

---

