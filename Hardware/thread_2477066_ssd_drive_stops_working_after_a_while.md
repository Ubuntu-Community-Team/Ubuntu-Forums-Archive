---
title: "ssd drive stops working after a while"
date: 2022-07-13
forum: Hardware
---

### Post by ricardodevpt on 2022-07-13
Hi there,

I have a lenovo ideapad 5.
In this laptop I have 2 hard drives. The one that came with the laptop and 1 ssd that I installed.
This new drive has 2 partitions. One ntfs for use in windows and another one where I installed ubuntu (as dual boot). So basically:

Drive A: Windows
Drive B: Partition 1 -> Windows data; Partition 2 -> ubuntu

Both drives **work great on Windows** however, when I use ubuntu the drive B stops working after a while and the system crashes (usually it takes a few minuts 2~10 min). 
I've tried to reinstall ubuntu multiple times and sometimes the hard drive even fails during installation.

Any idea what could be causing this? Maybe some power settings on ubuntu?

Thank you

---

### Post by Autodave on 2022-07-13
Drive B is the operating drive when you are running Ubuntu, so it is working harder than when Windows is running from the other drive.  Are you sure that it is not overheating?

---

### Post by ricardodevpt on 2022-07-13
Thanks for the asnwer.
I also have VMWare runing windows on that drive and it never failed, so I guess it's not overheating.

---

### Post by TheFu on 2022-07-13
> **ricardodevpt said:**
> Thanks for the asnwer.
I also have VMWare runing windows on that drive and it never failed, so I guess it's not overheating.

I wouldn't guess.  I'd look at the drive data using the SMART data.  smartctl is the tool I'd use to run a test, then when that finishes, look at the data. There might be a GUI tool for this - perhaps gnome-disks. Last time I looked at that tool, it wasn't providing the most useful data. Perhaps that has changed?

---

### Post by Yellow Pasque on 2022-07-13
I'd also be looking at RAM and swap size, especially if you're running something heavy like VMWare on Linux.
```
free -m
```

---

### Post by ricardodevpt on 2022-07-13
> **TheFu said:**
> I wouldn't guess.  I'd look at the drive data using the SMART data.  smartctl is the tool I'd use to run a test, then when that finishes, look at the data. There might be a GUI tool for this - perhaps gnome-disks. Last time I looked at that tool, it wasn't providing the most useful data. Perhaps that has changed?
Thanks, I've just run a couple of tests and the teperature is around 50C (122F) and the max I saw was 56C (132F).
Before crashing the last measurement was 52C.

---

### Post by ricardodevpt on 2022-07-13
> **Yellow Pasque said:**
> I'd also be looking at RAM and swap size, especially if you're running something heavy like VMWare on Linux.
```
free -m
```
I'm running VMWare on Windows not on linux. Windows 11 as host and windows xp as guest. I also have a ubuntu guest that I run from time to time without problems.
Thanks

---

### Post by Yellow Pasque on 2022-07-13
Okay, let's try a more direct approach. Please run these commands and give the output (remember to use code tags):
```
sudo apt-get install smartmontools
sudo smartctl -a /dev/nvme0
sudo smartctl -a /dev/nvme1
free -m
```

---

### Post by ricardodevpt on 2022-07-13
> **Yellow Pasque said:**
> Okay, let's try a more direct approach. Please run these commands and give the output (remember to use code tags):
```
sudo apt-get install smartmontools
sudo smartctl -a /dev/nvme0
sudo smartctl -a /dev/nvme1
free -m
```
Here you have it

Drive A:
```
[COLOR=#000000][FONT=&amp]=== START OF SMART DATA SECTION ===[/FONT][/COLOR]SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        46 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    6%
Data Units Read:                    118.217.927 [60,5 TB]
Data Units Written:                 117.066.194 [59,9 TB]
Host Read Commands:                 1.451.400.825
Host Write Commands:                829.039.518
Controller Busy Time:               2.811
Power Cycles:                       9.246
Power On Hours:                     3.591
Unsafe Shutdowns:                   645
Media and Data Integrity Errors:    0
Error Information Log Entries:      2.954
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               46 Celsius
Temperature Sensor 2:               41 Celsius
Thermal Temp. 1 Transition Count:   5
Thermal Temp. 1 Total Time:         206

Error Information (NVMe Log 0x01, 16 of 64 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       2954     0  0x100a  0x4004      -            0     0     -



```

Drive B:
```
=== START OF READ SMART DATA SECTION ===SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x71) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (   2) minutes.
Conveyance self-test routine
recommended polling time:      (   1) minutes.


SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       2705
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       1350
148 Total_SLC_Erase_Ct      0x0000   100   100   000    Old_age   Offline      -       10293
149 Max_SLC_Erase_Ct        0x0000   100   100   000    Old_age   Offline      -       134
150 Min_SLC_Erase_Ct        0x0000   100   100   000    Old_age   Offline      -       0
151 Average_SLC_Erase_Ct    0x0000   100   100   000    Old_age   Offline      -       75
164 Total_Erase_Count       0x0000   100   100   000    Old_age   Offline      -       12383
165 Max_Erase_Count         0x0000   100   100   000    Old_age   Offline      -       33
166 Min_Erase_Count         0x0000   100   100   000    Old_age   Offline      -       0
167 Average_Erase_Count     0x0000   100   100   000    Old_age   Offline      -       4
159 DRAM_1_Bit_Error_Count  0x0000   100   100   000    Old_age   Offline      -       0
160 Uncorrectable_Error_Cnt 0x0000   100   100   000    Old_age   Offline      -       0
161 Valid_Spare_Block_Cnt   0x0000   100   100   000    Old_age   Offline      -       160
163 Initial_Bad_Block_Count 0x0000   100   100   000    Old_age   Offline      -       87
168 Max_Erase_Count_of_Spec 0x0000   100   100   000    Old_age   Offline      -       1000
169 Remaining_Lifetime_Perc 0x0000   100   100   000    Old_age   Offline      -       100
177 Wear_Leveling_Count     0x0000   100   100   050    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       26
194 Temperature_Celsius     0x0000   100   100   000    Old_age   Offline      -       48 (Min/Max 5/76)
195 Hardware_ECC_Recovered  0x0000   100   100   000    Old_age   Offline      -       0
196 Reallocated_Event_Count 0x0000   100   100   016    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Host_Writes_32MiB       0x0000   100   100   000    Old_age   Offline      -       27946
242 Host_Reads_32MiB        0x0000   100   100   000    Old_age   Offline      -       22221
245 TLC_Writes_32MiB        0x0000   100   100   000    Old_age   Offline      -       94884


SMART Error Log Version: 1
Warning: ATA error count 0 inconsistent with error log pointer 2


ATA Error Count: 0
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


Error -1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 ec 00 00 00 00 00  Device Fault


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 00 00 00 00 00      00:00:00.000  READ DMA


SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
    6        0    65535  Read_scanning was never started
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



```

Free:
```

               total        used        free      shared  buff/cache   available
Mem:           15346        1401       12543          75        1401       13589
Swap:           2047           0        2047
```

Thank you

---

### Post by TheFu on 2022-07-13
Looks like no smart tests have been performed.  Run either a short or long test to capture some data, then re-run the reports.

```
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       2954     0  0x100a  0x4004      -            0     0     -

```
is a bit concerning, but since the brand and model of the SSD are being hidden, we can't look up what that means, if anything.

BTW. Windows is well-known for ignoring hardware errors.  I've never seen a reason why MSFT has been doing this, but it is common for every other OS to complain about hardware issues that Windows ignores, until the blue screen.  Other OSes log the errors much earlier.  Is there anything in the system logs?  I'd look for errors and warnings over the last few weeks.

---

### Post by Yellow Pasque on 2022-07-13
```
Unsafe Shutdowns:                   645
```
Did you turn off Fast Startup/Boot in Windows?

---

### Post by ricardodevpt on 2022-07-13
> **TheFu said:**
> Looks like no smart tests have been performed.  Run either a short or long test to capture some data, then re-run the reports.

```
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       2954     0  0x100a  0x4004      -            0     0     -

```
is a bit concerning, but since the brand and model of the SSD are being hidden, we can't look up what that means, if anything.

BTW. Windows is well-known for ignoring hardware errors.  I've never seen a reason why MSFT has been doing this, but it is common for every other OS to complain about hardware issues that Windows ignores, until the blue screen.  Other OSes log the errors much earlier.  Is there anything in the system logs?  I'd look for errors and warnings over the last few weeks.
That is in drive A, which is not being mounted in ubuntu. I'll take a look at the system logs tomorrow and see if something stands out.
The drive A is SAMSUNG MZVLB512HBJQ-000L2
Drive B is Silicon Motion based SSDs - model TS512GMTS430S
Thanks

---

### Post by ricardodevpt on 2022-07-13
> **Yellow Pasque said:**
> ```
Unsafe Shutdowns:                   645
```
Did you turn off Fast Startup/Boot in Windows?
No, it's still enabled.
Should I disable it?

---

### Post by TheFu on 2022-07-13
> **ricardodevpt said:**
> No, it's still enabled.
Should I disable it?

YES!  If any file system is shared/accessed by both OSes.  Disabling both of those is SOP - standard operating procedure and has been since MSFT decided that closing file systems was an unnecessary luxury, incorrectly.

Odd branded SSDs tend to wear out much faster than the reputable brands too.  I had a few no-name SSDs that died after about 2 yrs of use. I was lucky, in that 
a) I have excellent backups
b) before total failure, the file systems would drop into read-only mode first, so I had a few weeks of notification that the SSDs were failing.  I understand that is atypical.  They do fail, without any warning too.

---

### Post by ricardodevpt on 2022-07-14
> **TheFu said:**
> YES!  If any file system is shared/accessed by both OSes.  Disabling both of those is SOP - standard operating procedure and has been since MSFT decided that closing file systems was an unnecessary luxury, incorrectly.

Odd branded SSDs tend to wear out much faster than the reputable brands too.  I had a few no-name SSDs that died after about 2 yrs of use. I was lucky, in that 
a) I have excellent backups
b) before total failure, the file systems would drop into read-only mode first, so I had a few weeks of notification that the SSDs were failing.  I understand that is atypical.  They do fail, without any warning too.
Ok thanks. I did that

---

### Post by ricardodevpt on 2022-07-14
I've resized my windows partition on drive A and created a partition to install ubuntu (it was previously installed in drive B and failing).

Now, with ubuntu in drive A, everything works well (I kept drive B unmounted).

I guess that the most likely cause of failure is some bug on the drivers for the ssd controller for this particular ssd disk. Does anyone know where can I file a bug for this? I guess it should be filed in the kernel repo?

Thank you all for the suggestions.

---

### Post by TheFu on 2022-07-14
I threw the model of SSD into google and if found this: [https://bbs.archlinux.org/viewtopic.php?id=251762](https://bbs.archlinux.org/viewtopic.php?id=251762)
In that thread, it shows some troubleshooting things and a few commands to help determine what the problem might be.  The "vmd" module helped 2 people, so I'd give that a try.

---

### Post by ricardodevpt on 2022-07-14
> **TheFu said:**
> I threw the model of SSD into google and if found this: [https://bbs.archlinux.org/viewtopic.php?id=251762](https://bbs.archlinux.org/viewtopic.php?id=251762)
In that thread, it shows some troubleshooting things and a few commands to help determine what the problem might be.  The "vmd" module helped 2 people, so I'd give that a try.
ok, thanks. I'll take a look

---

