---
title: "Ubuntu crashes if I try to write to one ext4 partition"
date: 2011-06-10
forum: Hardware
---

### Post by debsankha on 2011-06-10
Hi,
Whenever I try to write to one specific partition on my laptop's internal hard disk ,  ubuntu becomes unresponsive. If I copy files using nautilus, after some time an error dialog comes up saying: "Error: Read-only file system". 

The file system was *not *mounted read-only, BTW. Lots of error messages generally come at this point on the console, a sample is given below:
```

[2754.990123] ata3.00: status: { DRDY }
[2744.990123] ata3.00: failed command: WRITE FPDMA QUEUED
.
.
[2754.990123] ata3.00: status: { DRDY }
[2764.990123] ata3: COMRESET failed (errno=-16)

[2754.990123] end_request: I/O error, dev sda, sector 221356213

```Disk utility shows that the HDD has "a few bad sectors". Formatting the partition doesn't help. fsck shows that the filesystem is clean.

Is there any chance that these are being caused by some software bug? Or should I read these as signs of imminent hdd failure?

---

### Post by psusi on 2011-06-10
How many is "a few" bad sectors?  Look at the SMART statistics and post the actual counts.  You may be able to fix it by running badblocks in read/write mode, but this will destroy any data there.

---

### Post by debsankha on 2011-06-10
Thanks for the reply. The SMART statistics is:
```

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       1558
  3 Spin_Up_Time            0x0003   194   179   021    Pre-fail  Always       -       1300
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5078
  5 Reallocated_Sector_Ct   0x0033   184   184   140    Pre-fail  Always       -       122
  7 Seek_Error_Rate         0x000e   100   253   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11534
 10 Spin_Retry_Count        0x0012   100   091   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   096   096   000    Old_age   Always       -       4237
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       1072
193 Load_Cycle_Count        0x0032   139   139   000    Old_age   Always       -       183263
194 Temperature_Celsius     0x0022   103   086   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   196   196   000    Old_age   Always       -       4
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   085   085   000    Old_age   Always       -       11407
241 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       208700772757352
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       18231809227

```

Could you please explain how can I "run badblocks in read/write mode" ? 

I don't know enough about SMART to interpret the above statistics. Is it bad enough that I should consider replacing the HDD? (Laptop HDD's don't come cheap in the part of the world I live in :P)

---

### Post by psusi on 2011-06-10
You should certainly consider replacing it.  If you want to try to reformat the drive and continue using it, you should first zero the whole drive with:

```
sudo dd if=/dev/zero of=/dev/sda
```

After that, run the long SMART selftest ( you can do so either with smartctl or the disk utility GUI ), and if that passes, format the drive.  Run the selftest again every week or so to make sure no more bad sectors develop, and keep your important data backed up.

---

### Post by debsankha on 2011-06-10
Thanks for the suggestion. I think I'll buy a new drive. Do you think it'd cause any problem if I clone my root partition (by dd) to the new hdd? 
My root partition is not the one which is turning read-only and causing the OS to freeze.

---

### Post by psusi on 2011-06-10
It depends.  If there is nothing wrong with that part of the disk, then it should be fine.

---

### Post by debsankha on 2011-06-10
Ok. Thanks for your help. I'll mark the thread SOLVED.

---

