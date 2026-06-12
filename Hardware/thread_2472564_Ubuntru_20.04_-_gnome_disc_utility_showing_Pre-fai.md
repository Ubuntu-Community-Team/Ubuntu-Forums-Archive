---
title: "Ubuntru 20.04 - gnome disc utility showing Pre-fail on brand new disc"
date: 2022-03-03
forum: Hardware
---

### Post by stephen35 on 2022-03-03
Hi, I am running 20.04 desktop on a ten year old x64 box, 16 GB RAM, 2 TB drive.  I recently replaced the drive because the disc's smart data (viewed through the gnome disc utility) was showing 'Pre-fail'.  Also the drive was ten years old  and really did need replacing.

After reinstalling without incident I checked the smart data of the new drive and it also showing pre-fail with huge numbers of retries.  

Could this be caused by a failing disc controller on the motherboard.  Would the driver's diagnostics distinguish between drive and motherboard/controller issues? 

Both old and new drives are Seagate Barracuda drives, the new one a "Compute" drive.

As I have been restoring from backup, I noticed very poor performance from the drive after about an hour of copying, down to about 5 MB/sec, so clearly something isn't right.  Which is worse than the ten year old drive!

Would appreciate any thoughts as to where the problem is.  At the moment, I am thinking of sending the new disc back and putting back the old one.  

Thanks in advance for any assistance

---

### Post by #&amp;thj^% on 2022-03-03
> **stephen35 said:**
>   At the moment, I am thinking of sending the new disc back and putting back the old one.  

Thanks in advance for any assistance
That's exactly what needs to happen, I've had 3 segates and I **_refuse_** to buy anymore.
Maybe just luck of the draw>>>but none the less. Western Digital for me.
SMART tests have been very accurate in my 15 + years using it. I hate being the barer of bad news though.

---

### Post by stephen35 on 2022-03-04
> **1fallen said:**
> That's exactly what needs to happen, I've had 3 segates and I **_refuse_** to buy anymore.
Maybe just luck of the draw>>>but none the less. Western Digital for me.
SMART tests have been very accurate in my 15 + years using it. I hate being the barer of bad news though.

Thanks.  Because the old drive (also a Seagate) lasted ten years I thought I would be OK with another Seagate.  The old Seagate was logging pre-fail errors but it was ten years old.  I will return to Amazon and try a different brand.  They log a 4% failure rate so I guess this time I have lucked out

---

### Post by #&amp;thj^% on 2022-03-04
> **stephen35 said:**
> Thanks.  Because the old drive (also a Seagate) lasted ten years I thought I would be OK with another Seagate.  The old Seagate was logging pre-fail errors but it was ten years old.  I will return to Amazon and try a different brand.  They log a 4% failure rate so I guess this time I have lucked out

I have seen them last as you point out, it just has not been my experience with the brand.
I have one of the first Intel SSD's I think it's 160Gigs that has a 10 year warranty, that one of my servers is on, Is nearing 20 yrs on that one.
Don't let me influence your choice though by a knee-jerk but true statement.:)
EDIT: Important to me>>>Note that Seagate offers a 2-year warranty on the BarraCuda while WD offers a 5-year warranty on the WD Black &#8212; an important consideration when buying an HDD.
PNY has one 1TB SSD i'm using now (for 2 years), still to early for me to rate that one just now. (I'm very hardware critical)

---

### Post by TheFu on 2022-03-04
Pre-fail is what every drive shows in the SMART data.  That field is meaningless.
Look at the raw values for each attribute AND watch it over time.  I run a short test weekly and long tests monthly, keeping the post-test report files for 6 months on each disk.  Then it is easy to see how the values change.  Point-in-time SMART data isn't nearly as useful

I have some 15 yr old Seagate HDDs that have behaved perfect, but those are all 320G and smaller, from a time when Seagate engineering was actually exceptional.
Somewhere when HDD sizes of 600GB became available the Seagate engineering went downhill, drastically.  They were caught lying for nearly a year about engineering faults to all their customers. They didn't want a recall, though that should have been mandated. OTOH, it probably would have bankrupted the company.
I avoided Seagate drives for years, but there was a deal on some 2TB HDDs - I thought it was too good to pass up and got 2 of them. I was wrong.  At 11 months and 13 months, both of those 2TB disks had failed. Research at the time showed a huge, out-of-whack, failure rate for the specific model. Again, Seagate knew it and kept selling them.

For large HDDs, the best source of scientific data, since none of the vendors is sharing, is the quarterly backblaze disk failure reports. I think those have been published since 2013.  Backblaze doesn't buy enterprise HDDs. They ran the numbers and decided that consumer large-size HDDs were more cost effective, but only if the failure rates were low enough.  Seagate had a few years where they did better. HGTS has routinely made the least failure rate HDDs, at least for the workloads that backblaze has, for most of this time.  I've got some HGTS, WD, Toshiba spinning disks.  

All the larger Seagates in my storage all failed around the time the warranty ended.
I've had a few HGTS 4TB drives fail, but the ones that did fail were all used as OS + data disks, which is a different workload than just data disks.

I had some early bad experienced with SSDs, so I avoid them for most data storage needs based on those failures that happened on SSDs ~ 2yr old. Perhaps I had bad luck.  Since then, I've been selective about the brand and model of SSD purchased. I have Samsung and Micron SSDs now. None have failed, yet and all are far below their predicted block write limits. 2 are 4 yrs old, one was installed into a new system last fall, but isn't really being used.

I think Seagate is trying to optimize their failures to match their warranty periods. 100% pure business decision. Some would call it smart.  To some extent, all drive makers are doing that.  For my money, for the OS, I'll be using Samsung SSDs and for data storage, I'll be checking the backblaze reports on specific models, as I compare $/TB pricing.  I will not be buying any HDD with a known failure rate over 1%.  Some models do much better, but 1% seems to be the industry standard for everyone except Seagate.  Beware.

I have a few WD-Black drives. All of them are over 10 yrs old.
I also have a few HGTS DC -line HDDs. These are data center models and have become the WD-Gold line. None of them have failed and picking up a used DC-line 4TB HDD for $45 is a bargain, provided it has useful lifespan remaining.

I also avoid USB enclosure disks. The warranty is usually less (90 days is common) and we never know which actual HDD will be put inside.  WD doesn't always put WD HDDs inside. Beware.  Of course, sometimes they do and some real bargains have been found that way. 

Look at the warranty for HDDs. That tells use what the manufacturer actually thinks about a specific HDD model. Lacking any real data, that is the best we have to use in our buying choice.

---

### Post by #&amp;thj^% on 2022-03-04
> **TheFu said:**
> Pre-fail is what every drive shows in the SMART data.  That field is meaningless.

Do you actually see that? The only time I see it is when a real problem is occurring.
```
sudo smartctl -at long /dev/sdb
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.15.26-hardened1-1-hardened] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       WDC PC SN730 SDBQNTY-256G-1001
Serial Number:                      201429806191
Firmware Version:                   11170101
PCI Vendor/Subsystem ID:            0x15b7
IEEE OUI Identifier:                0x001b44
Total NVM Capacity:                 256,060,514,304 [256 GB]
Unallocated NVM Capacity:           0
Controller ID:                      8215
NVMe Version:                       1.3
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256,060,514,304 [256 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            001b44 8b46045ddb
Local Time is:                      Thu Mar  3 17:54:29 2022 MST
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Log Page Attributes (0x1e):         Cmd_Eff_Lg Ext_Get_Lg Telmtry_Lg Pers_Ev_Lg
Maximum Data Transfer Size:         128 Pages
Warning  Comp. Temp. Threshold:     84 Celsius
Critical Comp. Temp. Threshold:     88 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     5.00W       -        -    0  0  0  0        0       0
 1 +     3.50W       -        -    1  1  1  1        0       0
 2 +     3.00W       -        -    2  2  2  2        0       0
 3 -   0.0700W       -        -    3  3  3  3     4000   10000
 4 -   0.0035W       -        -    4  4  4  4     4000   40000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        49 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    4%
Data Units Read:                    14,346,876 [7.34 TB]
Data Units Written:                 14,533,505 [7.44 TB]
Host Read Commands:                 279,408,987
Host Write Commands:                278,525,512
Controller Busy Time:               496
Power Cycles:                       1,174
Power On Hours:                     1,564
Unsafe Shutdowns:                   171
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Thermal Temp. 1 Transition Count:   3
Thermal Temp. 2 Transition Count:   1
Thermal Temp. 1 Total Time:         584
Thermal Temp. 2 Total Time:         180

Warning: NVMe Get Log truncated to 0x200 bytes, 0x200 bytes zero filled
Error Information (NVMe Log 0x01, 16 of 256 entries)
No Errors Logged

```

---

### Post by TheFu on 2022-03-04
Yes.
After the test finishes, request a report with **-a**, not *-at*.  All of the parameters say "Pre-Fail".

I use **smartctl**.

---

### Post by #&amp;thj^% on 2022-03-04
> **TheFu said:**
> Yes.
After the test finishes, request a report with **-a**, not *-at*.  All of the parameters say "Pre-Fail".

I use **smartctl**.

I'm doing something different then:
```
>> sudo smartctl -a /dev/sdb
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.15.26-hardened1-1-hardened] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       WDC PC SN730 SDBQNTY-256G-1001
Serial Number:                      201429806191
Firmware Version:                   11170101
PCI Vendor/Subsystem ID:            0x15b7
IEEE OUI Identifier:                0x001b44
Total NVM Capacity:                 256,060,514,304 [256 GB]
Unallocated NVM Capacity:           0
Controller ID:                      8215
NVMe Version:                       1.3
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256,060,514,304 [256 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            001b44 8b46045ddb
Local Time is:                      Fri Mar  4 13:44:00 2022 MST
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Log Page Attributes (0x1e):         Cmd_Eff_Lg Ext_Get_Lg Telmtry_Lg Pers_Ev_Lg
Maximum Data Transfer Size:         128 Pages
Warning  Comp. Temp. Threshold:     84 Celsius
Critical Comp. Temp. Threshold:     88 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     5.00W       -        -    0  0  0  0        0       0
 1 +     3.50W       -        -    1  1  1  1        0       0
 2 +     3.00W       -        -    2  2  2  2        0       0
 3 -   0.0700W       -        -    3  3  3  3     4000   10000
 4 -   0.0035W       -        -    4  4  4  4     4000   40000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        48 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    4%
Data Units Read:                    14,380,803 [7.36 TB]
Data Units Written:                 14,574,589 [7.46 TB]
Host Read Commands:                 280,511,756
Host Write Commands:                279,914,627
Controller Busy Time:               498
Power Cycles:                       1,175
Power On Hours:                     1,571
Unsafe Shutdowns:                   171
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Thermal Temp. 1 Transition Count:   3
Thermal Temp. 2 Transition Count:   1
Thermal Temp. 1 Total Time:         584
Thermal Temp. 2 Total Time:         180

Warning: NVMe Get Log truncated to 0x200 bytes, 0x200 bytes zero filled
Error Information (NVMe Log 0x01, 16 of 256 entries)
No Errors Logged

```

---

### Post by TheFu on 2022-03-04
Spinning HDD?  
Sorry - the results say "old_age" sometimes too.  Ran this test over the weekend:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       65536
  2 Throughput_Performance  0x0005   131   131   054    Pre-fail  Offline      -       148
  3 Spin_Up_Time            0x0007   133   133   024    Pre-fail  Always       -       299 (Average 276)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       87
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   131   131   020    Pre-fail  Offline      -       29
  9 Power_On_Hours          0x0012   092   092   000    Old_age   Always       -       57207
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       87
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       859
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       859
194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 21/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       3
```

And this for an SSD:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   000    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0032   100   100   010    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       25209
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       89
171 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   090   090   000    Old_age   Always       -       151
174 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       73
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   066   034   000    Old_age   Always       -       34 (Min/Max 21/66)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
202 Unknown_SSD_Attribute   0x0030   090   090   001    Old_age   Offline      -       10
206 Unknown_SSD_Attribute   0x000e   100   100   000    Old_age   Always       -       0
246 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       54286277233
247 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1697256584
248 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1352258730
180 Unused_Rsvd_Blk_Cnt_Tot 0x0033   000   000   000    Pre-fail  Always       -       2480
210 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0

```

The first disk report tells me that the SATA cable connection has an issue. Parameter 199 is about the cable and the read-errors at the top say most are corrected.  I've been meaning to swap the cable, but always forget.  The spinning disk in that machine doesn't have any important data. It is a scratch area only.

---

### Post by #&amp;thj^% on 2022-03-04
> **TheFu said:**
> Spinning HDD?  
Sorry - the results say "old_age" sometimes too.  Ran this test over the weekend:

You got me curious so I checked with Drive that I bad mouthed. (Seagate)
```
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Pro Compute
Device Model:     ST1000LM049-2GH172

```

```
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   082   064   034    Pre-fail  Always       -       141370080
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       516
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   065   060   045    Pre-fail  Always       -       2952410
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1623 (190 221 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       278
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   052   040    Old_age   Always       -       37 (Min/Max 20/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       5245
194 Temperature_Celsius     0x0022   037   048   000    Old_age   Always       -       37 (0 18 0 0 0)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x000f   099   099   030    Pre-fail  Always       -       1008 (67 20 0)
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged


```
Thanks TheFu I like interacting with you, it's always thought provoking. :)

---

### Post by TheFu on 2022-03-04
I enjoy almost all of these interactions. Everyone has different experiences ... and we all recognize the handles for helpful, smart, people. 

That disks has some scary numbers, but nothing is screaming REPLACE. OTOH, the read/seek error rates are pretty high, without the normal cable CRC errors. I'd keep excellent, versioned, backups for stuff on that disk I didn't want to lose.

The power-cycle-cnt is telling too. Not good or bad, just clearly different.

Anyways, hope that stephen35 gains some knowledge from our posts.

---

### Post by #&amp;thj^% on 2022-03-04
> **TheFu said:**
> 
That disks has some scary numbers, but nothing is screaming REPLACE. OTOH, the read/seek error rates are pretty high,

Anyways, hope that stephen35 gains some knowledge from our posts.

New, brand New Drive. I laughed when I noticed those as well. :D (It came with the Laptop)
It just keeps daily back-ups for a couple of days, then moved to another drive bi-weekly.
 I also hope stephen35 gains some knowledge from our posts.
Regards
One last EDIT: Going through all my older tests,  My experience with Seagate drives is that they tend to fail when the number of errors goes over 1000.YMMV.

---

### Post by stephen35 on 2022-03-10
> **TheFu said:**
> Pre-fail is what every drive shows in the SMART data.  That field is meaningless.
Look at the raw values for each attribute AND watch it over time.  I run a short test weekly and long tests monthly, keeping the post-test report files for 6 months on each disk.  Then it is easy to see how the values change.  Point-in-time SMART data isn't nearly as useful.

Thanks.  After getting a replacement drive i realised that i had been misreading the Smart data report.  It wasn't wholly my fault as many of the values seemed to be exceeding the threshold values but on further reading, I learnt that there are few standards and that the values can be very misleading for the inexperienced to interpret.  Therefore I have kept the second disc I received

---

### Post by stephen35 on 2022-03-10
> **1fallen said:**
> 
 I also hope stephen35 gains some knowledge from our posts.
Regards


I have, yes.  Thanks

---

