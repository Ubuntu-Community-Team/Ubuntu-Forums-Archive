---
title: "How to clone boot drive"
date: 2017-05-21
forum: Hardware
---

### Post by SeijiSensei on 2017-05-21
My primary drive has started to fail SMART testing, running afoul of the "reallocated sectors" problem.  Since this device has the UEFI boot sector, and three operating systems on it, I'd like to clone the device to a new disk.  Can I just do this with dd, e.g.,
```
dd if=/dev/sda of=/dev/sdb
```
or do I need something more sophisticated?

---

### Post by TheFu on 2017-05-21
Hey!!!!  I feel your pain.

The boot disk on my NAS is dying too.    Started showing issues 2 days ago. Installed a replacement (same size) yesterday.  Has Legacy BIOS boot, GPT, and LVM on the disk.

I'm doing a 
```
$ sudo ddrescue --force /dev/sdb /dev/sda /tmp/log.file
```
where
* sdb is the **source**
* sda is the **target**
This is backwards from what most people would see.  I swapped the ports on purpose and powered down/removed all other storage (about 20TB) to prevent issues.

Using **ddrescue** is important since it will continue AFTER errors are seen.

When all done, I'll restore the backup from 3 days ago to fix any failed sectors from the original.  Last time I looked about 90MB of errors was shown in the ddrescue output.  

That single command will create all the formatting, partitions, LVM stuff, everything.  At first reboot, I expect to have to change the UUIDs for the partitions.  But since I'm still trying to recovery the last possible bits, I cannot say for certain that my plan will work.

I made a copy of the SMART data for the old disk AND the new disk to use as reference later. On the **new disk** ...
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   054    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   100   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       18
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       2
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       2
194 Temperature_Celsius     0x0002   146   146   000    Old_age   Always       -       41 (Min/Max 25/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       3

```
That's with 18 hrs of power. It was sync'ing overnight.

The older drive:
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       101
  3 Spin_Up_Time            0x0007   134   134   024    Pre-fail  Always       -       532 (Average 508)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       67
  5 Reallocated_Sector_Ct   0x0033   001   001   005    Pre-fail  Always   FAILING_NOW 1115
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   111   111   020    Pre-fail  Offline      -       43
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       28032
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1124
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       1124
194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 17/49)
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       2054
197 Current_Pending_Sector  0x0022   001   001   000    Old_age   Always       -       44120
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```
3.2 yrs of use.  It had a 3 yr warranty, so looks like Amex insurance gets to pay for the replacement. Nice.  Both are HGST 4T disks.

---

### Post by SeijiSensei on 2017-05-22
Thanks!  The replacement drive is on order.  I'll check back after I've given ddrescue a try.

---

### Post by TheFu on 2017-05-22
> **SeijiSensei said:**
> Thanks!  The replacement drive is on order.  I'll check back after I've given ddrescue a try.

ddrescue completed here.  Lots of bad sectors, a few important, but the system booted.  boot, lvm, partitions and most data were all handled as expected. The 2nd GPT record was corrupted. Easily fixed.  Replicated the data from the backup disk back over.  Life is good. 

Had a corrupt DB (it was a media center), restore fixed that.

If the clone hadn't worked, I would have followed my normal restore processes for that machine.

---

### Post by SeijiSensei on 2017-05-25
Happy to report that ddrescue did the trick, although the drive did not display any errors.  I guess the SMART warning was early enough that the problematic sectors had yet to be used.  Plugged in the replacement drive, ran 
```
sudo ddrescue -f /dev/sda /dev/sdb /tmp/mapfile
```
and waited for it to complete.  Swapped the cables and booted successfully off the replica.

Thanks for the advice, Fu.

---

### Post by TheFu on 2017-05-25
So ... solved?

---

