---
title: "Is this hdd dead or are the readings sensitive?"
date: 2015-07-21
forum: Hardware
---

### Post by Higgins909 on 2015-07-21
I was hoping I could salvage this old drive that I thought was dead along time ago, but was able to install a minimal server on it, using my lappy (easy to test drives on)
The values and then the worst confuse me.  If it only had that error once, it it really failing?


sudo smartctl --all /dev/sda
```

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   001   001   051    Pre-fail  Always   FAILING_NOW 65847
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   086   086   025    Pre-fail  Always       -       4467
  4 Start_Stop_Count        0x0032   087   087   000    Old_age   Always       -       13994
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       7577
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       844
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1101
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       962392
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       6
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   059   059   000    Old_age   Always       -       41 (Min/Max 14/41)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       40
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       844
225 Load_Cycle_Count        0x0032   076   076   000    Old_age   Always       -       248272

```

sudo badblocks -b 4096 -c 4096 -s /dev/sda
Its got no error sofar but at about 97% it started taking a really real long time.

Thanks,
Higgins909

---

### Post by dino99 on 2015-07-21
i've never trusted hdd smart output; my hdds looks as yours since ages, and they still works smootly. That did not meant backups are useless indeed.

---

### Post by Irihapeti on 2015-07-21
What brand is it? Some Seagate drives can have crazy values for #1 and be OK.

I think I would still want to have backups, though.

---

### Post by tgalati4 on 2015-07-21
You have almost a million:

> 181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       962392

So, something is not right with this drive.  It could be a bad controller, or some other electronic problem that is causing firmware errors within the drive.  The drive surface and heads may be OK.

You can run the manufacturer's diagnostics.  Many can be loaded from Ultimate Boot CD (UBCD).  I wouldn't use it unless I knew exactly what the problem is.  I have repartitioned bad drives that have crashed (Put a dummy partition that completely brackets the bad blocks.) and they have worked for years.  So I know it is possible to work around some issues.  If it is electronic or if you have a head, bearing, or drive mechanism problem, those tend to be fatal for a drive.

---

### Post by weatherman2 on 2015-07-21
Run the Extended S.M.A.R.T. test - takes a few hours.

---

### Post by Higgins909 on 2015-07-21
I was using ssh and failed to notice a bunch of errors on the screen of my laptop that had no one logged in. (screen turned off)
I ended up calling it quits before it could complete.  I tried to open up another ssh and it wouldn't. (something like that)
I'm just going to call it dead and move on with my build.

---

