---
title: "Killed hard drive trying to install Jaunty"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by carverj on 2009-07-03
Hi,
   I have an 80 Gb hard drive, sda with Vista on first partition, then Interpid and then swap. I added a 500 Gig drive and tried to install Jaunty to it and make master. The CD error appeared (stating that the hard drive could be to old or wrote CD to fast) whilst installing Jaunty. Now Vista is running differently, the new drive is not readable to Vista and I cannot load Vista or Ubuntu CDs. 
Please help. Thanks.

---

### Post by carverj on 2009-07-03
It seems intrepid is showing the following errors which are similar to the errors that the live CDs show.
[CODE]
ata4.00: status DRDY ERR 
ata4.00: error UNC
ata4.00: exception Emask 0X0 SAct 0X0 SErr 0X0 action 0X0
ata4.00: BMDMA stat 0X24
ata4.00: cmd c8/00:80:00:00:::/:::/e0 tag 0 dma 4096 i
[CODE]

---

### Post by Herman on 2009-07-03
I had that message from the BIOS during boot-up in one of my computers earlier this week. 'booting from CD-ROM . . . ', or something like that. On  black screen.
I had been adding another IDE hard drive at the time.
I think it was because I have a 'buggy BIOS' in the motherboard of that particular PC, and it seems to require the optical drive to be plugged in and jumpered as the _last_ drive in the IDE sequence. 
I looked at the boot sequence in the  BIOS and that was okay, nothing to do there.
It was a fair bit of messing around to get the cable-select IDE cable to reach the right drives with the right plugs. First I had to switch to a different IDE cable with the slave plug further towards the middle of it so it would reach the drive bay I had spare for the extra hard drive. Then I also had to remove the CD/DVD drive from the top slot and fit it to an lower drive bay.
Maybe things would have been easier if I had chosen simply to revert to an old jumper-select IDE cable and set the jumpers as Master and Slave.
I have it booting normally now.

---

### Post by carverj on 2009-07-03
Oh OK, perhaps loose cable when trying to install messed up install. I forgot to mention, I may have messed things up further. I went in to Vista and manually deleted first two partitions that were left over from failed install to try to revert back to the original windows format. I tried to fdisk the drive to stop errors but got error:   Could this be a zero length partition?

---

### Post by Herman on 2009-07-03
Try checking all of your IDE cables and jumper settings, even for the CD/DVD drive.

---

### Post by carverj on 2009-07-03
I have one CD/DVD on IDE set as slave. I have two SATA cable hard drives. I swapped the power and SATA over on them and changed the 80 Gig to master. Same error only as sda instead of sdb as switched on board. Why would a failed install make a drive unreadable?

---

### Post by Herman on 2009-07-03
Oh, you have two sata drives, I thought maybe the new one might have been an IDE one.

A failed install might leave a corrupted partition table on one of your hard drives, but that shouldn't affect the booting or reading of both hard drives, only the one that has a corrupted partition table. That happened to me once from dust on the optical lense of a CD/DVD drive.

In that case, I don't know. I'll keep thinking about it for you . . .

---

### Post by carverj on 2009-07-03
I appreciate that. I remember going into Vista disk management and deleting the first two volumes and I believe after that even Vista loaded slowly. At this point I would just like to wipe the 500 Gig drive and be able to load live CDs for another install attempt to it. Thoughts?

---

### Post by Herman on 2009-07-03
I agree. I would try using GParted to 'set a new disk label' on the 500 GB hard drive first, just to make sure you clear any corruptions and refresh the partition table.

I'd be careful not to touch the MBR in the hard disk that has Vista in it though, since Vista is tied to the MBR's 'disk identifier'. I'm not sure if it's easy to get Vista to boot again after changing that. You can make  backup of it if you want, [MBR backup and restore]("http://members.iinet.net.au/%7Eherman546/p13.html#mbr_dd").

---

### Post by carverj on 2009-07-03
Is there another way to change the label? Its just that Vista and command line with PCLinux live CD are the only options available right now. The GParted live CD wont load with this disk issue.

---

### Post by Herman on 2009-07-03
:-k Hmmm . . .
Maybe it would be a good idea to just remove the newly added hard disk, or at least unplug it temporarily and see if your computer's behavior returns to normal.

If not, maybe we should try some other troubleshooting procedures to try to isolate the problem. It's possible that there's some other hardware problem here that might be co-incidental to your new hard disk and (failed) operating system install.

---

### Post by Herman on 2009-07-03
Try running a few tests on your computer's memory modules with memtest 86+ from your Ubuntu Jaunty CD. You only have to boot the CD to the usplash screen for that. It should boot that far, (I hope). If you have a faulty memory module, you'll see some test results feedback highlighted bright red. If nothing much happens and the screen remains blue through all eight tests, your memory modules and probably okay.
Here's a link about it, [memtest86+]("http://members.iinet.net.au/%7Eherman546/p15.html#Memtest86").

---

### Post by carverj on 2009-07-03
> Maybe it would be a good idea to just remove the newly added hard disk, or at least unplug it temporarily and see if your computer's behavior returns to normal.

The computer is fine with the corrupted drive removed. Yes, the memory test shows a red highlighted entry.
Is this my problem?

---

### Post by carverj on 2009-07-03
> I would try using GParted to 'set a new disk label' on the 500 GB hard drive first, just to make sure you clear any corruptions and refresh the partition table.

Is it possible to do this from command line? GParted live wont boot with the hardware problem.

---

### Post by Herman on 2009-07-03
If memtest 86+ comes up with any red it would generally indicate a faulty RAM module or bad seating of a RAM module in it's slot.
If you're going to do it yourself you need to be aware of ESD (electrostatic discharge) before playing around with RAM modules. It's best to have the right equipment, such as an electrostatic wrist band and a mat to put the computer box on with a ground wire to the mat to equalize any potential 
If your motherboard has more than one module you can take one module out and run the test again on the other module, then switch modules to find out which one is the faulty one.
If it only shows one line of red, that's not good, but usually with bad RAM you'll get a lot of red lines, heaps of them. I'm not sure if the problem in your RAM is your main problem, but it would probably be a good idea to work on that one first. Faulty RAM can cause some strange behavior in your PC.

I'm not sure why the computer works okay without the 500 GB hard drive plugged in.
I'd be trying the suspected faulty hard drive in a different computer if another computer is available.
One of the really cool things about Ubuntu is that we can install Ubuntu in a hard drive in any computer and remove the hard drive and put it in almost any other computer and it'll boot right up and run perfectly. So you can fix your hard drive's MBR (and partition table) in a different computer and run diagnostic software on the hard drive to see if there was an error in the new hard drive.
I think I read somewhere or saw in add/remove programs or somewhere there's a new GUI for smartmontools. I'll have to find out more about that. I just use the command line normally. You can use a live CD if you want. You'll need to install smartmontools first, ```
sudo apt-get install smartmontools
``````
sudo smartctl -a /dev/sda >> harddisk.report
```Where: /dev/sda is the hard disk to be tested, replace with sdb or sdc according to information from 'sudo fdisk -lu' or a partition editor such as GParted.
That smrtctl -a command will print you a plain text file named 'harddisk report', which may help you decide if your hard disk is okay. Often it's pretty confusing to make much sense out of the information you'll be given, but it's worth doing anyway. The hard disk manufacturer's own diagnostic tools would probably be better.
Basically though, either the hard disk will work satisfactorily in a different computer or it won't.

I'm kind of hoping it's a memory problem and your new hard drive is okay, but I might be wrong, more testing and experiments will sort things out.

---

### Post by carverj on 2009-07-04
I have removed the RAM with two red highlighted entries and that has not fixed the problem. I have no spare computer to test faulty drive. 
> It's best to have the right equipment, such as an electrostatic wrist band and a mat to put the computer box on with a ground wire to the mat to equalize any potential
wrist band - check. might be able to find a mat. Don't have a ground wire so will have to keep away from carpet.
I will try to install smartmontools when am in live CD. 
Cheers.

---

### Post by carverj on 2009-07-04
I have not been able to test with smartmontools.
Trying to reinitialize the device in vista. If I were able to format the drive with the Vista disk, would that fix the partition table?

---

### Post by carverj on 2009-07-04
I finally managed to get Gparted live running only for it to say no device detected. This is with the 80 gig drive removed and the jumper set to master. Vista CD would not let me format the device.
Does this confirm that the drive is faulty?

---

### Post by Herman on 2009-07-04
It seems like the new hard disk is the problem so far, but keep an open mind, it could be something else too. Try a different SATA cable if you have one. Try swapping the hard drive power connectors from one hard drive to the other too.

It could be that the new hard drive is too big for your computer's BIOS or it draws too much power from your power supply. I know I have one laptop hard drive that seems to be too stiff for any laptop I own to be able to spin up. It's a 250 GB drive and we have some laptops that came with 40 and 60 GB hard drives. It won't spin up in a USB external hard drive caddy either. I had to fit it with widening channels to make it fit in a desktop sized drive bay and run it in one of my desktop computers. Probably that's not the problem in your case, but what I mean to say is that there can be weird problems we wouldn't normally think of right away.

listen carefully to the sounds your hard drive is making as you boot your computer up.
Does it spin up okay? Can you hear a nice smooth whirring noise or is there some horrible clicking and buzzing?

Things can go wrong even with a brand new hard drive, just as easily as a household or automotive lightbulb can blow at any random time, so can tiny electronic components on the circuit board under a hard drive, or on your motherboard or anywhere. Fortunately, most of the time computer parts are very reliable, they usually amaze me actually. 

You may be able to use Windows to google up your hard drive manufacturer's website and download some diagnostic tools especially designed for your hard drive.

You can try formatting the hard drive with Vista's tools and see if it helps. It won't be likely to do any harm. That will depend on what's actually wrong with your hard drive. I'm still skeptical that a partition table problem can have that much effect on the rest of the computer.

---

### Post by carverj on 2009-07-04
I forgot to mention, I had been using that drive for a month or two with no problems as a secondary NTFS storage. So the device worked fine until either the Ubuntu failed install or when I deleted the partitions in Vista. I have tried swapping power and SATA with the  working drive and the spinning seems fine. Anyway, I will keep trying things to find a solution.
Thanks mate.

---

### Post by Herman on 2009-07-04
The new GUI program for smartmontools is called GSmartControl. It's really cool! :)
I'm trying it out in my Karmic Koala installation.
It has explanatory notes that come up when I hover my mouse over items in the 'attributes' tab.  That's a big help for most people for making some sense out of the output from smartmontools.
I can recommend GSmartControl to anyone who wants to try it out. 
It's installable from 'add/remove programs' in Karmic but I haven't checked if it's available in earlier versions of Ubuntu. 
Ubuntu Karmic Koala is still under development and most users shouldn't be installing Karmic until after it is officially released.

---

### Post by carverj on 2009-07-04
So managed to boot Jaunty live and run smartmontools:
```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD502HI
Serial Number:    S1VZJ9AS300208
Firmware Version: 1AG01113
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Sat Jul  4 10:22:11 2009 UTC

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (6326) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 106) minutes.
Conveyance self-test routine
recommended polling time: 	 (  12) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   097   097   051    Pre-fail  Always       -       10520
  3 Spin_Up_Time            0x0007   093   093   011    Pre-fail  Always       -       3020
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       174
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       572
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       173
 13 Read_Soft_Error_Rate    0x000e   097   097   000    Old_age   Always       -       10369
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       10369
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   073   060   000    Old_age   Always       -       27 (Lifetime Min/Max 27/28)
194 Temperature_Celsius     0x0022   074   059   000    Old_age   Always       -       26 (Lifetime Min/Max 26/28)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       218
196 Reallocated_Event_Count 0x0032   099   099   000    Old_age   Always       -       46
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       44
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       736

SMART Error Log Version: 1
ATA Error Count: 312 (device log contains only the most recent five errors)
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

Error 312 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:20:17.040  READ DMA
  ef 03 46 01 4f c2 a0 00      00:20:17.040  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:20:17.040  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:20:17.040  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:20:17.040  SMART RETURN STATUS

Error 311 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:00:05.700  READ DMA
  ef 03 46 01 4f c2 a0 00      00:00:05.700  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:00:05.700  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:00:05.700  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:00:05.700  SMART RETURN STATUS

Error 310 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:04:27.870  READ DMA
  ef 03 46 01 4f c2 a0 00      00:04:27.870  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:04:27.870  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:04:27.870  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:04:27.870  SMART RETURN STATUS

Error 309 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:00:05.620  READ DMA
  ef 03 46 01 4f c2 a0 00      00:00:05.620  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:00:05.620  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:00:05.620  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:00:05.620  SMART RETURN STATUS

Error 308 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 a0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:01:01.450  READ DMA
  ef 03 46 01 4f c2 a0 00      00:01:01.450  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:01:01.450  SET FEATURES [Set transfer mode]
  c6 00 10 01 4f c2 a0 00      00:01:01.450  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:01:01.450  SMART RETURN STATUS

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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
Does this mean a faulty disk? I cannot decipher it!
Thanks.

---

### Post by Herman on 2009-07-04
I'm not sure either.

You have 312 errors logged already and your new hard drive only has 572 powered-on hours on it so far, in only 174 starts and stops. But I don't know if those errors are very serious or not. Some hard drives give misleading results in smartmontools anyway because they like to keep their proprietary details secret.
It's still worth a look because sometimes you can see something definitely bad in there, but in this case I can't really tell.

For comparison though, I ran smartmontools in my main computer. It has four hard disks with an average of 1069 start-stops and close to 10000 hours average and none of them have had any errors yet.

I've seen hard drives with a lot of errors and they're still okay though. 
There's one brand of hard drive, Seagate, which is reputed to be a very good brand, but which tends to show more errors. They still last as long or longer it's just that the sensitivity of the error monitoring is higher. I think that's what the difference is anyway. I must have read that somewhere. 

```
herman@amd64hh:~$ sudo smartctl -a
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

ERROR: smartctl requires a device name as the final command-line argument.


Use smartctl -h to get a usage summary

herman@amd64hh:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD1600AAJS-00PSA0
Serial Number:    WD-WMAP91608706
Firmware Version: 05.06H05
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jul  4 21:53:32 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (4200) seconds.
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
recommended polling time:      (  56) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   157   152   021    Pre-fail  Always       -       3116
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1021
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       10212
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1014
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1033
194 Temperature_Celsius     0x0022   116   091   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

herman@amd64hh:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD1600AAJS-00PSA0
Serial Number:    WD-WMAP91611744
Firmware Version: 05.06H05
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jul  4 21:53:59 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (4200) seconds.
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
recommended polling time:      (  56) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   157   151   021    Pre-fail  Always       -       3150
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1087
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       8473
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1062
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       182
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1087
194 Temperature_Celsius     0x0022   111   088   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

herman@amd64hh:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE family
Device Model:     WDC WD1600JB-00REA0
Serial Number:    WD-WMANM7217041
Firmware Version: 20.00K20
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jul  4 21:54:44 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (4980) seconds.
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
recommended polling time:      (  60) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   180   176   021    Pre-fail  Always       -       3975
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1084
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10457
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1076
194 Temperature_Celsius     0x0022   126   103   000    Old_age   Always       -       21
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

herman@amd64hh:~$ sudo smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE family
Device Model:     WDC WD1600JB-00REA0
Serial Number:    WD-WMANM7233163
Firmware Version: 20.00K20
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jul  4 21:55:06 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (4980) seconds.
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
recommended polling time:      (  60) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   176   174   021    Pre-fail  Always       -       4166
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1085
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10485
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1076
194 Temperature_Celsius     0x0022   114   089   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

### Post by carverj on 2009-07-04
Mine is Samsung which could have this input/output errors when combined with a certain chipset. Not sure if this is the case here.
I managed to find the faulty drive with the Jaunty live CD installer (GParted)but there was an input/output error when trying to write ext3 to the first partition.

---

### Post by carverj on 2009-07-04
The issue is not affecting my ability to load CD and Jaunty after all. Only, fdisk -l sda, e2label command and GParted all failing to  initialize/recognize device.
Well might get a replacement hdd. 
Thanks Herman, once again very helpful indeed.

---

### Post by carverj on 2009-07-04
I can't understand errors but here is output from /bin/dmesg | less:

```
[ 2460.088557] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2460.088575] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2462.554966] ata1: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[ 2462.554970] ata1: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[ 2462.554971]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
[ 2462.554973] ata1: ATA_REG 0x41 ERR_REG 0x40
[ 2462.554975] ata1: tag : dhfis dmafis sdbfis sacitve
[ 2462.554976] ata1: tag 0x0: 1 1 0 1  
[ 2462.554984] ata1.00: exception Emask 0x1 SAct 0x1 SErr 0x0 action 0x6 frozen
[ 2462.554986] ata1.00: Ata error. fis:0x21
[ 2462.554991] ata1.00: cmd 60/20:00:00:00:00/00:00:00:00:00/40 tag 0 ncq 16384 in
[ 2462.554992]          res 41/40:04:00:00:00/40:00:00:00:00/40 Emask 0x9 (media error)
[ 2462.554994] ata1.00: status: { DRDY ERR }
[ 2462.554996] ata1.00: error: { UNC }
[ 2462.555002] ata1: hard resetting link
[ 2463.432053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2463.456265] ata1.00: configured for UDMA/133
[ 2463.456281] ata1: EH complete
[ 2463.456364] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 2463.456378] sd 0:0:0:0: [sda] Write Protect is off
[ 2463.456380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2463.456398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2465.750982] ata1: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[ 2465.750986] ata1: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[ 2465.750987]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
[ 2465.750990] ata1: ATA_REG 0x41 ERR_REG 0x40
[ 2465.750991] ata1: tag : dhfis dmafis sdbfis sacitve
[ 2465.750993] ata1: tag 0x0: 1 1 0 1  
[ 2465.751000] ata1.00: exception Emask 0x1 SAct 0x1 SErr 0x0 action 0x6 frozen
[ 2465.751002] ata1.00: Ata error. fis:0x21
[ 2465.751007] ata1.00: cmd 60/20:00:00:00:00/00:00:00:00:00/40 tag 0 ncq 16384 in
[ 2465.751008]          res 41/40:04:00:00:00/40:00:00:00:00/40 Emask 0x9 (media error)
[ 2465.751010] ata1.00: status: { DRDY ERR }
[ 2465.751011] ata1.00: error: { UNC }
[ 2465.751017] ata1: hard resetting link
[ 2466.628217] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2466.652244] ata1.00: configured for UDMA/133
[ 2466.652260] ata1: EH complete

```

---

### Post by Herman on 2009-07-04
:-k Okay, I wish I had the experience to tell you for sure, but it looks as if that hard drive might have something wrong with it somewhere in the hard disk controller in the circuit board on the card underneath the drive. 
All I can tell you is to seek advice from someone who might know more than me.

Your smartmontools output mentions something about DMA in those error messages.
I googled 'DMA' and found out a few things about that, mainly it involves the small flash memory block under your hard disk temporarily caching info on it's way to and from the hard disk. (Like between the hard disk and the computer's main memory or maybe the CPU cache). 
That allows the hard disk to plod along and read and write it it's own leisurely but constant pace while other parts of the computer are free to work in fits and starts.
[Ultra DMA (UDMA) Modes]("http://www.pcguide.com/ref/hdd/if/ide/modesUDMA-c.html") - PC Guide, [What is an IDE Hard Disk Drive]("http://www.duxcw.com/digest/guides/hd/hd3.htm") - Dux Computer Digest, [Ultra DMA]("http://www.duxcw.com/digest/guides/hd/hd3.htm") - Storage.com Definitions.

:idea: Hey! That was a good idea you had to look at the dmesg output! :)
Your dmesg output fairly well hints at the same thing, it looks to me as if your Linux kernel is muttering and mumbling away about it too.

I wouldn't write the hard disk off yet completely though, it might only be some problem with the particular Linux kernel you're trying to use at the moment. Maybe a different kernel will be okay. You did say that you used this drive for a while under Windows and it seemed alright then.

Maybe try taking a look at it with Parted Magic Live CD and see what happens. Parted Magic Live CD will have a different Linux kernel and it contains about the most advanced software I know of for dealing with any kind of disks. Try fdisk -l and e2label and some other things from Parted Magic Live CD and see what happens. It's only a small download, and a very nice and useful product, here's the link: [Parted Magic Live CD]("http://partedmagic.com/") - News.
(I might go download the latest one too, a new one just came out a couple of weeks ago.)
If you still have trouble with your hard disk with Parted Magic, I'd say you have a good case for a warranty claim on that hard disk for sure.

---

### Post by carverj on 2009-07-04
Will give it a go thanks very much.
I installed a spare 20 gig drive to IDE master and was unable to install Jaunty to it with the 80 gig SATA slave in. More input/output errors. So I removed the SATA and Jaunty installed. I went into Vista disk management to delete volumes to see if it was my error that caused this mess. It seems to be hardware not my error. So it could be either kernel issue or DMA issue as mentioned previously by Herman, or hardware/BIOS/jumper or the like not supporting IDE and SATA drive.

---

### Post by Herman on 2009-07-05
Parted Magic -4.2 has GSmartControl in it and it's great ! :guitar:

---

### Post by carverj on 2009-07-05
> It's only a small download, and a very nice and useful product, here's the link: Parted Magic Live CD - News.
(I might go download the latest one too, a new one just came out a couple of weeks ago.)
Tried the new one, 4.2. Neither fdisk, GParted, fsck, etc. were able to read the device. Will take the drive back tomorrow.
Oh, and yes, GSmartControl is a nice tool. It said the basic health of the disk is fine but with those DMA errors still.
Thanks so much for helping again Herman.

---

### Post by carverj on 2009-07-05
Well it seems the store cannot give me a replacement hard drive straight away. Even though they said they do not trust the Samsung product they sold me. He recommended using a live CD for linux in the interim. Not a bad idea, although I have run out of room in Vista. The 80 gig drive has 50GB ntfs, 30GB ext3 and some swap. Is it possible for me to extend the ntfs partition to 80GB?

---

### Post by Herman on 2009-07-06
Sure, easy! Assuming you have no data in your ext3 partition, just boot your Parted Magic CD and 'execute' (start) GParted Partition Editor, delete the ext3 and swap partitions and then resize your NTFS partition. It is recommended to run CHKDSK after resizing NTFS, it will probably be done automatically by Windows before it boots up anyway.

If you have data in your ext3 partition and it isn't backed up, you should be able to use either your Ubuntu Live CD or Parted Magic to do that, but you'll need some kind of storage media to copy it to of course. Parted Magic is handy in case you need to write rescued data to a CD because Parted Magic runs in RAM and ejects it's disk after it loads, so you can use the CD drive to copy any rescued data to a blank CD or DVD.

---

