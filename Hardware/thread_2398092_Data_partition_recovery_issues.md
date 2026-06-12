---
title: "Data partition recovery issues"
date: 2018-08-07
forum: Hardware
---

### Post by gumbo64 on 2018-08-07
Ok so here's the facts.

- 300Gb Hard drive with 20 GB of backed up data on it, on a removable tray on Ubuntu 12.04. 
- Need to create a new partition on it, as I need to install Win764 (...got to install a specific CAD software which dont run on Linux :( ) so I fire up Gparted.

Gparted
- Resized partition with Gparted to 40GB --> OK
- Moved resized 40GB partition to the right of the unollacated space --> Got 4-5 read/write errors during the process but were easily solved by "retry" (got some oddly clicking noises at times during the process though). 
- Gparted says process completed successfully
- Looks like Gparted is lying to me as whole disk is now unallocated space. I assume Gparted failed writing partition table.

So I move on to Testdisk

Testdisk
- The disk is recognized properly (Maxtor 300Gb) and the two partitions (i.e. the partition and the unallocated space) are both recognized
- Unollacated space is suggested as * = bootable (but I don't care)
- Other partition with data on it is suggested as p = logical (the one I care for)
- I select the partition with my data on it, click on write and TestDisk returns a "write error" message. Guess it's failing in writing the partition table, same as Gparted.

Any help in recovering my data would be GREATLY appreciated.

PS. 
_My feeling_ (also due to the clicking noises mentioned earlier), is that the partition with the data on it was moved to the end of the disk where possibly there are damaged sectors, and this may be the reason why both Gparted and Test disk fail in rewriting the partition. _This is just my assumption and I am not an expert on this_. Matter of fact the issue arised after moving the partition. Wonder if moving the partiton to another phisical part of the disk before writing the partition table would help, and how to achieve this, if at all possible. No idea if this makes any sense though.

---

### Post by deadflowr on 2018-08-07
Clicking sounds are never good, no matter where the data might be stored on disk.
Run SMART tests to see the state of the drive:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

---

### Post by gumbo64 on 2018-08-07
I did run a smart test before I started the repartitioning. The Disk was flagged as healthy. It had some errors that I generally disregard as I noticed they are common even on brand new drives. 

Anyway here's the result of the smart test I just run on it with smartmontools.
I'm aware the temp is high but these Maxtor drives always were wood stoves. Got four of them on trays  I use for backups and such and they all are within that temp range. Guess the removable tray location don't help much. Temps were not much different before being placed in the trays though.



```
=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax 10 (SATA/300)
Device Model:     Maxtor 6V300F0
Serial Number:    V60EWQWG
LU WWN Device Id: 0 150500 7dd7f24c4
Firmware Version: VA111630
User Capacity:    300.090.728.448 bytes [300 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 T13/1532D revision 0
Local Time is:    Tue Aug  7 19:53:49 2018 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 2763) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 132) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 32
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   185   183   063    Pre-fail  Always       -       24203
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       640
  5 Reallocated_Sector_Ct   0x0033   251   251   063    Pre-fail  Always       -       28
  7 Seek_Error_Rate         0x000a   253   244   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   252   221   187    Pre-fail  Always       -       48418
  9 Power_On_Hours          0x0032   235   235   000    Old_age   Always       -       6411
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   252   252   000    Old_age   Always       -       752
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   038   027   000    Old_age   Always       -       62 (Min/Max 29/62)
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   249   253   000    Old_age   Always       -       62
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       6261
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   251   251   000    Old_age   Offline      -       30
198 Offline_Uncorrectable   0x0008   222   222   000    Old_age   Offline      -       31
199 UDMA_CRC_Error_Count    0x0008   001   001   000    Old_age   Offline      -       56242
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x000a   253   249   000    Old_age   Always       -       1
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       12
204 Soft_ECC_Correction     0x000a   253   252   000    Old_age   Always       -       0
205 Thermal_Asperity_Rate   0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
210 Unknown_Attribute       0x0032   253   249   000    Old_age   Always       -       0
211 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   253   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 20924 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 20924 occurred at disk power-on lifetime: 6007 hours (250 days + 7 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:49:55.016  IDENTIFY DEVICE
  c8 00 08 00 00 00 e0 00      00:49:51.926  READ DMA
  27 00 00 00 00 00 e0 00      00:49:51.925  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:49:51.924  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:49:51.923  SET FEATURES [Set transfer mode]

Error 20923 occurred at disk power-on lifetime: 6007 hours (250 days + 7 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:49:51.815  IDENTIFY DEVICE
  c8 00 08 00 00 00 e0 00      00:49:48.728  READ DMA
  25 00 08 68 49 8a e0 00      00:29:56.755  READ DMA EXT
  25 00 08 60 49 8a e0 00      00:29:56.755  READ DMA EXT
  25 00 08 58 49 8a e0 00      00:29:56.754  READ DMA EXT

Error 20922 occurred at disk power-on lifetime: 6007 hours (250 days + 7 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:29:55.201  IDENTIFY DEVICE
  25 00 08 78 98 86 e0 00      00:29:52.110  READ DMA EXT
  27 00 00 00 00 00 e0 00      00:29:52.109  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:29:52.108  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:29:52.107  SET FEATURES [Set transfer mode]

Error 20921 occurred at disk power-on lifetime: 6007 hours (250 days + 7 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:29:52.008  IDENTIFY DEVICE
  25 00 08 78 98 86 e0 00      00:29:45.193  READ DMA EXT
  25 00 08 58 98 86 e0 00      00:29:45.193  READ DMA EXT
  25 00 08 50 98 86 e0 00      00:29:44.811  READ DMA EXT
  25 00 08 48 98 86 e0 00      00:29:44.810  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6395         -
# 2  Short offline       Completed without error       00%      4079         -
# 3  Short offline       Aborted by host               70%      4075         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by springshades on 2018-08-08
Just to be sure, "sudo parted -l" doesn't see anything on the drive? If only testdisk is seeing the partition and it can't write to the drive's partition table (which is actually in the front of the drive), you might want to think about doing the freezer trick before things get any worse. Maybe testdisk will at least be able to get you a copy of most of the data on an external drive.

---

### Post by gumbo64 on 2018-08-08
sudo parted /dev/sdc: unrecognized disk label. 
Which was to be expected as Gparted can't see the volume since it started acting up...

Testdisk recognize the drive. I'll fit a big fan onto the drive to keep within acceptable temps and see what happens.

---

### Post by springshades on 2018-08-09
By the way, I just looked it up, and apparently the freezer trick that I suggested isn't a thing anymore. The problem that it is believed to have fixed for 15-20 minutes of use doesn't seem to happen anymore due to new technology. Sorry. :(

---

