---
title: "External Hard Drive Failing"
date: 2015-12-06
forum: Hardware
---

### Post by ericrcan on 2015-12-06
Hi everyone, I need some serious help! I had all my backups on an external, and somehow when I got back from my deployment, it doesn't work. I work in the IT field, so I've tried several things, but still need some help. In windows it says that the drive needs to be formatted. In Linux (parted magic) it says unallocated. I have about 300 gigs of backups just from pictures. What can I try so I can pull information off? I've tried pretty much every recovery software on Hirens Boot CD. Thanks in advance!

---

### Post by weatherman2 on 2015-12-06
In Parted Magic, open a terminal window and type:

```
parted -l
smartctl -a /dev/sda

```

If that second command seems to fail, try 

```
smartctl -a -T permissive -d sat /dev/sda
```

(This assumes your external drive is at /dev/sda.  If you are using a computer with a hard drive in it already to run Parted Magic, the internal drive may be on /dev/sda and the external on /dev/sdb or even elsewhere - so make sure you run smartctl with the correct drive.)

If the drive is truly alive but only corrupted, you could run file recovery software on it to try to recover files.  You might even try testdisk to see if say a corrupted partition file could be recovered - but first things first, need to see the above info first to know the drive is alive.

---

### Post by matt_symes on 2015-12-06
Hi

What make is the external hard drive and what is its size ?

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=2271320](http://ubuntuforums.org/showthread.php?t=2271320)

Kind regards

---

### Post by ericrcan on 2015-12-06
Here is what that command posted ```
root@PartedMagic:~# parted -l
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   ntfs         Basic data partition          hidden, diag
 2      316MB   420MB   105MB   fat32        EFI system partition          boot
 3      420MB   555MB   134MB                Microsoft reserved partition  msftres
 4      555MB   1000GB  1000GB  ntfs         Basic data partition


Error: Can't have a partition outside the disk!
Model: TOSHIBA MQ01ABF050 (scsi)                                          
Disk /dev/sdb: 500GB
Sector size (logical/physical): 4096B/4096B
Partition Table: unknown
Disk Flags: 

root@PartedMagic:~# smartctl -a /dev/sdb
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.5.6-pmagic] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MQ01ABF050
Serial Number:    25M3CGWPT
LU WWN Device Id: 5 000039 61340939d
Firmware Version: AM001U
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Sun Dec  6 09:49:10 2015 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
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
recommended polling time:      ( 117) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1772
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       72
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       194
 10 Spin_Retry_Count        0x0033   101   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       70
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       28
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       425
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       25 (0 44 255 245 0)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       17
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       250
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

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

root@PartedMagic:~# 


```


As far as the brand goes, its a cheap military "Skillcraft" external. The actual hard drive is a Toshiba. I have taken the hard drive out of the enclosure and it is connected through a SATA-USB connector now.

---

### Post by weatherman2 on 2015-12-06
Are you sure you didn't encrypt this disk?  Truecrypt or something?

Otherwise, you can try testdisk to see if it can recover the partition table.  You can try file recovery tools.

---

### Post by ericrcan on 2015-12-06
Testdisk can see the files! How do i get these off! lol. I tried Testdisk in windows and it didnt show anything. I tried again now and it sees it just fine... Another reason why I would rather use Linux lol

---

### Post by weatherman2 on 2015-12-06
Plug in another external hard drive - or copy the files to the other drive plugged into the computer.

---

### Post by ericrcan on 2015-12-06
Almost at 4% now. I will let you know how it goes. Thank you!

---

### Post by weatherman2 on 2015-12-06
Just remember that "backup" should mean "2nd/3rd/4th" copy not "only copy."  Your hard drive itself didn't fail but that's extremely common.  I use the "at least two copies of imporant files on different devices" rule.

---

### Post by ericrcan on 2015-12-06
It ended up failing. It says it got 148gb, but when I did list, it's only like 50mb... I'll try again soon.

As soon as I pull these files off I won't be using this hard drive again. It was clicking, but I put it in the freezer and that's how i was able to get it to stop clicking temporarily.

---

### Post by weatherman2 on 2015-12-06
The "freezer trick" has never worked for me - if that really helped you, consider yourself lucky.

It's not clear to me that your hard drive is really failing or whether the file system is simply corrupted.  There are no S.M.A.R.T. errors and no bad sectors.  In an external enclosure, sometimes these drives don't get enough power to operate properly and can "click" because they keep re-starting.  Could be the original enclosure it was in was failing or its power supply was failing.  I don't really know the specifics of what you tried when, etc., so I'm guessing at some of these assertions.

If you are having trouble reading files, you could use a tool called ddrescue to clone the whole drive, sector by sector, to an image file or to another entire drive.  It can skip bad sectors or re-try the bad ones over and over again.  If ddrescue is able to copy the entire drive without errors (no sectors) then that should confirm the drive itself isn't really failing.  If you can do that, you would be able to run file recovery tools even on the copy you made and not risk ruining the original if that's your only copy.  But if ddrescue can't copy anything (also try "dd" in Linux) the drive probably is failing.  S.M.A.R.T. has never been wrong for me but I have heard it's not perfect and that probably varies from manufacturer to manufacturer.  I normally don't preach using one particular brand of drive or avoid using other brands (because I have encountered bad drives from every manufacturer and know they can all fail), but I  have had particularly bad luck with Toshiba drives, FYI.  I hope you are still able to get all your files off, though.

---

### Post by ericrcan on 2015-12-06
ddrescue got over 8gb worth of info. I don't have another external to copy to right now, how do i mount the IMG file so I can see what files I was able to recover?

---

### Post by ericrcan on 2015-12-06
I ran ddrescue again with the hard drive wedged in a certain spot so it doesn't click. 93 GB so far and still going.

---

### Post by ericrcan on 2015-12-07
> GNU ddrescue 1.16
Press Ctrl-C to interrupt
rescued:   500107 MB,  errsize:       0 B,  current rate:   17457 kB/s
   ipos:   500107 MB,   errors:       0,    average rate:   15462 kB/s
   opos:   500107 MB,     time since last successful read:       0 s
Finished  



Got it! Its 5 am, so i have to go to work, then when im back ill see if i can mount this img file.

---

### Post by ericrcan on 2015-12-07
I see all my files!!!! Thanks for pointing out ddrescue!! You are a lifesaver! Mods can mark as solved :)

---

### Post by weatherman2 on 2015-12-07
Good to hear!

---

