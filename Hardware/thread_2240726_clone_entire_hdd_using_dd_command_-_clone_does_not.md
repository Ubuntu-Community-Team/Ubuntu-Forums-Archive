---
title: "clone entire hdd using dd command - clone does not boot"
date: 2014-08-21
forum: Hardware
---

### Post by Claus7 on 2014-08-21
Hello,

I tried to clone a 1TB seagate hdd (source) to a western digital 1TB one (destination). Both of them are new hdd. The original hdd has an ubuntu trusty default installation. The goal was to clone the **entire** seagate hdd for backup purposes which has a default installation of ubuntu trusty without manual partitioning.

In order to do so I did the following:

1) plugged both sata hdd in my computer
2) turned it on with ubuntu 14.04 cd
3) the computer booted from the cd and I selected the option: try ubuntu
4) the hdd were unmounted
5) when ubuntu opened I run the command:
```
sudo dd bs=4k if=/dev/SOURCE of=/dev/DESTINATION conv=noerror,sync
```
6) the output I got after ~6 hours was:
> 244190646+0 records in
244190646+0 records out
... (1 TB) copied, 21900.1 s, 45.7 MB/s

I shut down the computer removing the ubuntu cd from the tray. I **removed** my original (source) hdd (disconnected it), and left connected the cloned one in order to check if everything went ok.
So, I opened the computer and to my surprise I get in the end the grub rescue prompt.

It seems also that I cannot mount the cloned hdd, since, while connecting it to my ubu box via a usb case, I can see that under the option: system tools->preferences->disks, this hdd has the same volumes as the source hdd, yet it is mentioned that it has unallocated space. 

Is there any idea on what went wrong in the process? The process I followed should not boot the cloned disk without errors, since I'm not using both disks simultaneously? 

Thank you in advance, 
Regards!

---

### Post by weatherman2 on 2014-08-21
Save yourself hours of time and use a Clonezilla boot disk instead.  It will copy only the blocks used on the source drive - so if your 1TB drive is only 50% full, it will only copy the half of the drive that you need and not the empty space.

Plus Clonezilla will clone intelligently.

---

### Post by sudodus on 2014-08-22
> **Claus7 said:**
> Hello,

I tried to clone a 1TB seagate hdd (source) to a western digital 1TB one (destination). Both of them are new hdd. The original hdd has an ubuntu trusty default installation. The goal was to clone the **entire** seagate hdd for backup purposes which has a default installation of ubuntu trusty without manual partitioning.

In order to do so I did the following:

1) plugged both sata hdd in my computer
2) turned it on with ubuntu 14.04 cd
3) the computer booted from the cd and I selected the option: try ubuntu
4) the hdd were unmounted
5) when ubuntu opened I run the command:
```
sudo dd bs=4k if=/dev/SOURCE of=/dev/DESTINATION conv=noerror,sync
```
6) the output I got after ~6 hours was:


I shut down the computer removing the ubuntu cd from the tray. I **removed** my original (source) hdd (disconnected it), and left connected the cloned one in order to check if everything went ok.
So, I opened the computer and to my surprise I get in the end the grub rescue prompt.

It seems also that I cannot mount the cloned hdd, since, while connecting it to my ubu box via a usb case, I can see that under the option: system tools->preferences->disks, this hdd has the same volumes as the source hdd, yet it is mentioned that it has unallocated space. 

Is there any idea on what went wrong in the process? The process I followed should not boot the cloned disk without errors, since I'm not using both disks simultaneously? 

Thank you in advance, 
Regards!

If SOURCE and DESTINATION are mass storage devices like sda and sdb in it should work. I have used

```
sudo dd bs=4k if=/dev/sda of=/dev/sdb
```

I think noerror might not be good, if there are read errors (bad sectors in the source drive), because it means 'continue after read errors'.

In such cases it is probably much better to use ddrescue. The info page ```
info ddrescue
``` is very well written and informative. It is a good way to get as much as possible cloned from a failing drive, and I suggest that you try it also in your case. Use a log file and run it twice, if bad sectors are found. See Example 1 in the info page.

-o-

I'm not sure that the architecture of the two brands of HDDs are the same.

---

### Post by Claus7 on 2014-08-22
Hello,

> **weatherman2 said:**
> Save yourself hours of time and use a Clonezilla boot disk instead.  It will copy only the blocks used on the source drive - so if your 1TB drive is only 50% full, it will only copy the half of the drive that you need and not the empty space.

Plus Clonezilla will clone intelligently.

> **sudodus said:**
> If SOURCE and DESTINATION are mass storage devices like sda and sdb in it should work. I have used

```
sudo dd bs=4k if=/dev/sda of=/dev/sdb
```

I think noerror might not be good, if there are read errors (bad sectors in the source drive), because it means 'continue after read errors'.

In such cases it is probably much better to use ddrescue. The info page ```
info ddrescue
``` is very well written and informative. It is a good way to get as much as possible cloned from a failing drive, and I suggest that you try it also in your case. Use a log file and run it twice, if bad sectors are found. See Example 1 in the info page.

-o-

I'm not sure that the architecture of the two brands of HDDs are the same.

thank you very much for your responses!

So, the process that I followed should have worked. I will try ddrescue, since I won't need -at the time being- a new bootable cd, yet I have to admit that clonezilla should have been an ideal alternative as well.

Some further questions:
1) do you believe that grub somehow might be corrupted in the cloned disk? I saw many posts dealing with this issue, yet most of them, if I understood correctly, had to do with the fact that, in most cases, both disks were used simultaneously and usually some partitions were cloned, not the entire disk.
2) even if there is a bad sector in one of the disks (both were brand new disks), is it normal that I see the info unallocated to the cloned disk?
3) *sudodus* you mention something about different architecture: do you mean that cloning might not work because they are different brands?

I will continue my cloning process and post back again.

Thank you once again,
Regards!

---

### Post by sudodus on 2014-08-22
> **Claus7 said:**
> Hello,

thank you very much for your responses!

So, the process that I followed should have worked. I will try ddrescue, since I won't need -at the time being- a new bootable cd, yet I have to admit that clonezilla should have been an ideal alternative as well.

Some further questions:
1) do you believe that grub somehow might be corrupted in the cloned disk? I saw many posts dealing with this issue, yet most of them, if I understood correctly, had to do with the fact that, in most cases, both disks were used simultaneously and usually some partitions were cloned, not the entire disk.

Cloning (if correctly done) should create a good grub bootloader and boot directory.
> 
2) even if there is a bad sector in one of the disks (both were brand new disks), is it normal that I see the info unallocated to the cloned disk?

It depends where the bad sector is located.
> 
3) *sudodus* you mention something about different architecture: do you mean that cloning might not work because they are different brands?

I will continue my cloning process and post back again.

Thank you once again,
Regards!

Yes, I know that some terabyte-size disks have special architecture. Often it should work with cloning, but I am not sure that it will always work, at least there might be slower speed. You can find detailed information about your particular brands and models of disks, if you browse the internet.

I have successfully cloned a 1 TB disk to another 1 TB disk some month ago. The disk was failing after years of hard usage. I used ddrescue and could clone most failing sectors (during the second run with ddrescue). All important sectors were saved, so the cloned disk worked (and works) well.

The new disk is a WDC_WD1003FBYZ-010FB0, and the old disk was a WDC10EARS (both Western Digital 1 TB).

---

### Post by Claus7 on 2014-08-22
Hello,

*sudodus* thank you for your prompt and comprehensible responses!

Reading about ddrescue, and before I start again, I would like to ask two more questions:

1) Should I type

```
ddrescue -v /dev/SOURCE /dev/DESTINATION logfile
```

in order to do the cloning and get a logfile as well? 

2) I see that some users have used first the:

```
cfdisk -z /dev/DESTINATION
```

do I need to issue the last command first and then the initial one?

Thank you once again,
Regards!

---

### Post by sudodus on 2014-08-22
Read ```
info ddrescue
``` carefully!

Use ***Example 1*** and the following ddrescue commands

```

ddrescue -f -n /dev/hda /dev/hdb logfile
ddrescue -d -f -r3 /dev/hda /dev/hdb logfile

```

where you should have **sda** and **sdb** or whatever corresponds to your disk devices (instead of the old IDE **hda** and **hdb**).

I think you need *not* run cfdisk before the cloning.

---

### Post by sudodus on 2014-08-22
There is one more important thing to check. ***The target disk must be at least as big as the source***. If the target is one single byte smaller, there will be problems with the partition table (and file system, if the last byte is used by a partition).

---

### Post by Claus7 on 2014-08-22
Hello,

*sudodus* thank you for the prompt verification!

so:
1) taking into consideration the 1st example from the info ddrescue (the difference there is that it mentions 2 partitions, yet here I'm interested about the entire disk) is that I have to issue 2 commands instead of 1, meaning I have to do it **twice** as you had mentioned before.

2) as a result the complete usage of the commands should be:
```
ddrescue -f -n /dev/hda /dev/hdb logfile
ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
fdisk /dev/hdb
e2fsck -v -f /dev/hdb
```

the thing is that I cannot find ddrescue, while running the ubuntu cd. Which leads to:
open software center->edit->Software Sources...-> and check the 2nd option that will appear in the new window that will open.

3) checking my original disk I saw the following:
```
sudo fdisk -l
```

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004b421

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945145343   972571648   83  Linux
/dev/sda2      1945147390  1953523711     4188161    5  Extended
**Partition 2 does not start on physical sector boundary.**
/dev/sda5      1945147392  1953523711     4188160   82  Linux swap / Solaris

so this might be a problem.

4) under disks I can see that my original disk has 3 parts. The cloned one, since it was slightly bigger has 4. I do not know if this caused any problems as well.

I will try to use ddrescue and see what I will get.

Regards!

---

### Post by Claus7 on 2014-08-22
Hello,

update: I was not able to download ddrescue, since it needs internet and for some reason, after some time, it complained that it cannot fetch some packages needed.

So I went to this site: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

and followed the steps in order to use clonezilla for cloning. 
From here: [http://clonezilla.org/downloads/download.php?branch=alternative](http://clonezilla.org/downloads/download.php?branch=alternative) I downloaded for trusty 64bit an iso image and I booted from that cd.

Unfortunately, I had errors, since it complained that it cannot copy a specific partition. 
Is it possible that these errors were made due to dd command or the hdd was faulty from the beginning?

Thank you for all the support up to now!
I would like to see if it is possible to repair the disk.

Regards!

---

### Post by sudodus on 2014-08-22
> **Claus7 said:**
> Hello,

*sudodus* thank you for the prompt verification!

so:
1) taking into consideration the 1st example from the info ddrescue (the difference there is that it mentions 2 partitions, yet here I'm interested about the entire disk) is that I have to issue 2 commands instead of 1, meaning I have to do it **twice** as you had mentioned before.

2) as a result the complete usage of the commands should be:
```
ddrescue -f -n /dev/hda /dev/hdb logfile
ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
fdisk /dev/hdb
e2fsck -v -f /dev/hdb[COLOR=#ff0000]1[/COLOR]
```

e2fsck operates on partitions, not drives/disks/devices, so for each partition [COLOR=#ff0000]1[/COLOR], 2, 3 ...
> 
the thing is that I cannot find ddrescue, while running the ubuntu cd. Which leads to:
open software center->edit->Software Sources...-> and check the 2nd option that will appear in the new window that will open.

install it from the repos with

```
sudo apt-get install ddrescue
```


***Edit:*** Maybe you should use
```
sudo apt-get install gddrescue
```
> 

3) checking my original disk I saw the following:
```
sudo fdisk -l
```



so this might be a problem.

4) under disks I can see that my original disk has 3 parts. The cloned one, since it was slightly bigger has 4. I do not know if this caused any problems as well.

I will try to use ddrescue and see what I will get.

Regards!

---

### Post by Claus7 on 2014-08-22
Hello,

sorry for the typo I did previously. Thank you *sudodus* for mentioning it. And thank you in general!

Concerning the ddrescue command for some reason it does not work for the time being. 

So in between, I issued the command:
```
sudo smartctl --all /dev/sdb
```

and similar ones, and in some cases the disk passed the tests, whereas in others it reported errors.

In the end I issued the command:
sudo badblocks -svvn -c 262144 /dev/sdb

and I got xxx/0/0 errors, where xxx was around 3000 errors after 8 hours having completed around 0.02% of the disc or around 200000 blocks. 

So my question is:
1) have I damaged the brand new disk with dd?
2) or was it damaged from the beginning?
3) if it is damaged is it possible for me to get it back?

Just to report that using clonezilla I was able to see exactly the same information for the source and cloned disk using the command fdisk. The problem was that due to errors the cloned disk remained unbootable.

I'm thinking to return it back to the store and see what they will tell me.

Thank you,
Regards!

---

### Post by weatherman2 on 2014-08-22
The command
```

smartctl --all /dev/sdb

```

doesn't *run *any tests - it only reports the current S.M.A.R.T. status of that drive, including the value of current attributes.

What is the output of that smartctl --all command?

You can run tests with smartctl too (google for the man page), but GSmartControl is much easier to use - it lets you run smartctl tests with a mouse and highlights in red bad results.

If I were you, after making sure with GSmartControl that the new disk really has no S.M.A.R.T. errors and passes tests, I'd erase all partitions on the new drive and start over with Clonezilla.  You can do this with Gparted, so you won't get confused with Clonezilla about which drive is the source and which the destination.

If there are real S.M.A.R.T. errors showing up in GSmartControl, I'd return the drive under warranty and get a good one.

---

### Post by sudodus on 2014-08-23
I do not think that dd causes errors, that are displayed by the S.M.A.R.T. system. I suspect that there are hardware defects, so follow the advice of *weatherman2*.

If you cannot use ddrescue, either you have a typo in the command line, or something is really wrong with at least one of the drives (probably the target drive in your cloning attempts).

I use Clonezilla, and it works well for me. But it does not work, if there are bad sectors in a file, that is to be cloned (on the source drive). Then ddrescue is the alternative.

---

### Post by Claus7 on 2014-08-23
Hello,

*weatherman2* and *sudodus* thank you once again for your responses.

I'm trying various tools in order to see what is going on with the hdd. From what I have done up to now, I guess that the cloned hdd had a problem when purchased. This, because, after issuing the dd command, and when I booted from the cloned hdd which was the only disk connected I was able to see, before the grub rescue prompt, a bad block error which, if I recall correctly, coincides with the one (2064) you will see after issuing the command:

```
smartctl --all /dev/sdb
```

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-34-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA 6Gb/s)
Device Model:     WDC WD10EZEX-08M2NA0
Serial Number:    WD-WCC3FALJ2D0L
LU WWN Device Id: 5 0014ee 25fbef6eb
Firmware Version: 01.01A01
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Sat Aug 23 15:57:36 2014 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (11760) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 122) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   001   001   051    Pre-fail  Always   FAILING_NOW 4151
  3 Spin_Up_Time            0x0027   176   176   021    Pre-fail  Always       -       2200
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       15
  5 Reallocated_Sector_Ct   0x0033   177   177   140    Pre-fail  Always       -       974
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       60
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       32
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       15
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       10
194 Temperature_Celsius     0x0022   109   094   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   169   169   000    Old_age   Always       -       31
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 199 (device log contains only the most recent five errors)
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

Error 199 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 08 00 e0  Error: UNC 8 sectors at LBA = 0x00000810 = [COLOR=#FF0000]2064[/COLOR]

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 08 00 e0 08      00:17:15.739  READ DMA
  ec 00 00 00 00 00 a0 08      00:17:15.730  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:17:15.710  SET FEATURES [Set transfer mode]

Error 198 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 08 00 e0  Error: UNC 8 sectors at LBA = 0x00000810 = 2064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 08 00 e0 08      00:17:11.627  READ DMA
  ec 00 00 00 00 00 a0 08      00:17:11.618  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:17:11.598  SET FEATURES [Set transfer mode]

Error 197 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 08 00 e0  Error: UNC 8 sectors at LBA = 0x00000810 = 2064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 08 00 e0 08      00:17:06.100  READ DMA
  ec 00 00 00 00 00 a0 08      00:17:06.092  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:17:06.071  SET FEATURES [Set transfer mode]

Error 196 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 08 00 e0  Error: UNC 8 sectors at LBA = 0x00000810 = 2064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 08 00 e0 08      00:17:00.574  READ DMA
  ec 00 00 00 00 00 a0 08      00:17:00.565  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:17:00.544  SET FEATURES [Set transfer mode]

Error 195 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 08 00 e0  Error: UNC 8 sectors at LBA = 0x00000810 = 2064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 08 00 e0 08      00:16:56.472  READ DMA
  c8 00 08 40 08 00 e0 08      00:16:56.472  READ DMA
  c8 00 08 00 08 00 e0 08      00:16:56.472  READ DMA
  c8 00 08 80 08 00 e0 08      00:16:56.472  READ DMA
  c8 00 08 00 09 00 e0 08      00:16:56.471  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Interrupted (host reset)      70%        11         -

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

Now, about the above quote, the first time I typed the smartctl command I did not get such an output. In between I have issued some other commands including:
```
sudo e2fsck -f /dev/sdb1 -y
```
which seems that it has corrected some errors. At least now, under disks, I cannot see the bad block message.

Now, using gsmartcontrol found in synaptic:

```
sudo gsmartcontrol
```

at the moment it opened the disk was red marked and the Basic health check: FAILED!

and when pointing the mouse cursor there (on top of the word failed) it said:
> ALERT: The drive is reporting that it will fail very soon. Please back up as soon as possible!

Also running either short or long term tests the output was:
> Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.

I think that after these tests the disk should be returned back. I do mention that this is a brand new disk, which was used for the first time for the cloning purpose.

Thank you for pointing me to the right direction,
Regards!

---

### Post by sudodus on 2014-08-23
I think you know enough about the problem now to ask for the new disk to be replaced. Just tell them that the new disk does not work. It fails in the S.M.A.R.T. test.

---

### Post by weatherman2 on 2014-08-23
Bad disk for sure.  Return and replace under warranty.

---

### Post by Claus7 on 2014-08-23
Hello,

I tried also to see, if a windows cd and an attempt with NTFS partitioning will change anything, yet, as was expected, I got the following:
error: attempt to read or write outside of disk 'hd0'.
Entering rescue mode...
and then I saw the grub rescue> prompt, without having the ability to do anything else to the disk.

I should have typed: done, so as to shutdown the computer at that moment, I guess.

Anyway, I returned the faulty hdd back to the store's technical department and it was diagnosed as...dead **in no time**, so I got it replaced with a new one and blessings for successful cloning.

Then, I chose clonezilla to do the cloning thing, choosing also the option to clone the boot record.
It took ~15 minutes for 1TB hdd which has around 70GB occupied. The transfer rate was from 8.5 till 10 GB/min.
It finished with no errors!

I have to say that the previous time that I tried to use clonezilla the transfer rate started from very high values and in the end it was way lower than the 1GB/min value.

I tried to see if the cloned disk was ok and it booted normally.

The only question that I have now is...
If I type:
```
sudo fdisk -l
```

I get:
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004b421

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945145343   972571648   83  Linux
/dev/sda2      1945147390  1953523711     4188161    5  Extended
[COLOR="#FF0000"]Partition 2 does not start on physical sector boundary.[/COLOR]
/dev/sda5      1945147392  1953523711     4188160   82  Linux swap / Solaris

on both disks.

Should I worry about that message? Both hdd are working really well.

Thank you **very much** *sudodus* and *weatherman2* for your valuable info!

Regards!

---

### Post by weatherman2 on 2014-08-23
"[COLOR=#FF0000]*Partition 2 does not start on physical sector boundary.*[/COLOR]"

That's normal.  It's telling you that the extended partition - which is a container partition for logical partitions - doesn't start on a physical sector boundary.  But it's not a real partition - an extended partition is an abstraction (a old kludge to allow MSDOS hard drives to have more than four partitions).  Only logical partitions (which must be inside an extended partition) and primary partitions need to start on the boundary.  fdisk simply isn't smart enough to know the difference or care.

Your original drive may give you the same message.

Now that you've got this figured out - consider this for some future project: if you want to make *live* backups in the future, instead of booting Clonezilla once in a while to clone a backup, the next time you do a clean install of Ubuntu, use LVM (Logical Volume Manager).  With LVM, you can make "snapshots" of your running partitions, then safely backup the snapshot while you keep Ubuntu booted and in use.  No more need to boot Clonezilla.  But I'm sure you're probably tired of messing with all of this for now.

---

### Post by sudodus on 2014-08-23
I need not add anything to *weatherman2*'s explanation. Congratulations :KS

---

### Post by Claus7 on 2014-08-24
Hello,

> **weatherman2 said:**
> "[COLOR=#FF0000]*Partition 2 does not start on physical sector boundary.*[/COLOR]"

That's normal.  It's telling you that the extended partition - which is a container partition for logical partitions - doesn't start on a physical sector boundary.  But it's not a real partition - an extended partition is an abstraction (a old kludge to allow MSDOS hard drives to have more than four partitions).  Only logical partitions (which must be inside an extended partition) and primary partitions need to start on the boundary.  fdisk simply isn't smart enough to know the difference or care.

Your original drive may give you the same message.

Now that you've got this figured out - consider this for some future project: if you want to make *live* backups in the future, instead of booting Clonezilla once in a while to clone a backup, the next time you do a clean install of Ubuntu, use LVM (Logical Volume Manager).  With LVM, you can make "snapshots" of your running partitions, then safely backup the snapshot while you keep Ubuntu booted and in use.  No more need to boot Clonezilla.  But I'm sure you're probably tired of messing with all of this for now.

it is very relieving for me hearing that things now are totally functional, taking into consideration that I had also my old working drive with problems just a couple of weeks ago. This is the reason that I wanted to experiment with cloning, which proved to be a little bit more challenging than expected.
If clonezilla needs ~15 minutes for 80 occupied GB, I **guess** that it will need ~150' for 800 GB. Not such a big deal taking into consideration that I will need a lot of effort to fill this space up so as to reach the 800GB threshold. 
Now, if clonezilla gets stuck, dd(rescue) can do the work as well, since it can avoid some malfunctions in the original disk and taking into consideration that it is independent of how much disk space is occupied, ~6 hours is not something prohibitive.
I will keep in mind LVM in the future, as it seems very powerful as well. At least now I will be able to experiment with this easier, knowing that there is a cloned hdd waiting in the corner.

> **sudodus said:**
> I need not add anything to *weatherman2*'s explanation. Congratulations :KS

Thank you both for valuable contribution for a more stable working environment!

Regards!

---

