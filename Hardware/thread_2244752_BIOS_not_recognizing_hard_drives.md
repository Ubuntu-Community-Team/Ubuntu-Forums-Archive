---
title: "BIOS not recognizing hard drives"
date: 2014-09-18
forum: Hardware
---

### Post by thisisbasil on 2014-09-18
Cross-posted from here: [http://askubuntu.com/questions/525384/bios-not-recognizing-hard-drives](http://askubuntu.com/questions/525384/bios-not-recognizing-hard-drives)

> 
          For starters, I have this laptop: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3184129](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3184129)

  "ASUS G75VW-DS71 Laptop Computer - 3rd generation Intel Core  i7-3610QM 2.3GHz, 12GB DDR3, 1.5TB HDD, Blu-ray Player/DVDRW, 2GB NVIDIA  GTX 660M, 17.3" Full HD, Windows 7 Home Premium 64-bit, Bag &  Mouse"
  
I installed Ubuntu 14.01 and removed windows. Things were doing ok  for a while until this last weekend, when I started to get errors:
[B][FONT=courier new]
  Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key[/FONT][/B]

  The first time this happened, I booted into BIOS and got rid of the  Windows bootloader and things went ok for a couple days. Now, when I  tried to boot into my machine this afternoon, I got the same message,  but this time I noticed that my hard drives were not being detected by  BIOS. I then opened up my laptop and checked the connection to my drives  (took them out and put them back in). After this, I booted up again and  checked BIOS.  It was going back to the Windows bootloader, but since I  have no Windows partition, it basically just gave a default error  message and then went to grub, wherein I was able to boot into Ubuntu.
  The problem when I did this was that only one of my drives was being  seen by Ubuntu (it gave a message about checking for disc errors as  well, but was unable to fix them). So, I shut down, rechecked the  connections to the drives, then restarted. I got into grub, and selected  the appropriate boot option, only to be presented with the following  error messages:

  [B][FONT=courier new]error: failure writing sector 0x564c0010 to 'hd0'.
error: failure reading sector 0x549c7bc0 to 'hd0'.
unaligned pointer 0xdd06ec68
Aborted. Press any key to exit[/FONT][/B]

  I then created a live USB stick using Unetbootin where I tried to  check the disc for errors and then to just run Ubuntu live. Each time, I  get the error 
  Invalid or corrupt kernel image
  Now, even after resetting BIOS to defaults, my hard drives are not  being detected (the boot options only list CD/DVD and USB) and the above  error "reboot and select proper Boot device" displays.
  Is there any way to fix this? Does this mean my drives are FUBAR?
  
Update:

  Just for kicks, I switched the hard drives (i.e. I connected one to  where the other one was and vice versa). When I rebooted, it is seeing  the hard discs, and the Windows bootloader is back. I was able to boot  into Ubuntu just fine. *How* is this possible? I have not turned it off yet, so I do not know if this is permanent...

  
Update 2:

  As stated below, I restarted last night and everything was fine. This  morning, however, when I booted into Ubuntu, it seems as if only one of  my discs is not being detected by the OS (like previously mentioned).   Am I to assume that the disc is going bad, since I switched connections  for the drives?

      


I am not sure whether it is an issue with one of my discs or a SATA problem, preferably without having to open up my laptop in the process.  Any input would be appreciated.

---

### Post by weatherman2 on 2014-09-18
A failing hard drive is likely.  You can verify by booting a live USB and checking S.M.A.R.T. Attributes and/or running S.M.A.R.T. tests.  Use GSmartControl to do this - or grab a copy of the Parted Magic Linux disc which has it all built in - "GSmartControl" is called "Disk Health" I think.  Free version of Parted Magic still available at MajorGeeks I believe.

---

### Post by thisisbasil on 2014-09-18
Hmm, this won't be able to check the status of the drive that it cannot see...

Perhaps a reboot/reconnect will change have the same effect as earlier and I can try again. I ran the short test on the drive it can see and it gave no errors, I am running an extended test right now.

---

### Post by weatherman2 on 2014-09-18
Then connect the drive to another computer. If the drive is fine there, you know it's the computer.  If the other computer's BIOS can't see the drive either, you know it's the drive.

Or, connect another drive in the same connector as the one that is failing; if that drive is detected and tests OK, then the original has probably failed.  (Completely dead drives may not show in BIOS.)

---

### Post by thisisbasil on 2014-09-18
Results of the extended scan using GSmartControl:

> 
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-35-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.5
Device Model:     ST9750420AS
Serial Number:    5WS4D3PN
LU WWN Device Id: 5 000c50 049121498
Firmware Version: 0002SDM1
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Sep 18 14:44:10 2014 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
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
recommended polling time:      ( 146) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       131829568
  3 Spin_Up_Time            0x0003   098   097   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2634
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   066   060   030    Pre-fail  Always       -       3721015
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7259
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1288
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   093   000    Old_age   Always       -       4295032904
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   051   039   045    Old_age   Always   In_the_past 49 (0 4 51 24 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       5546
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       11601
194 Temperature_Celsius     0x0022   049   061   000    Old_age   Always       -       49 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   117   099   000    Old_age   Always       -       131829568
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       12
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       259269995795305
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3363058909
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3697452517

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7259         -
# 2  Short offline       Completed without error       00%      7256         -

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


It passed (no errors), but the there are 5 attributes where the type is listed "pre-failure": 
1. Raw Read Error Rate
2. Spin-Up Time
3. Reallocated Sector Count
4. Seek Error Rate
5. Spin-Up Retry Count

Do these give hints as to the impending destruction of my hd? I will also try to run the same diagnostic on the other hd, if I can ever get access to it again.

---

### Post by weatherman2 on 2014-09-18
"Pre-failure" is just the type of attribute.  GSmartControl will highlight Attributes in pink or red when it thinks there is some issue with them.

Looks like that hard drive is good.

---

