---
title: "Can't boot windows or ubuntu, hardisk issue"
date: 2019-04-06
forum: Hardware
---

### Post by rahulmawari on 2019-04-06
Hi all!,

I have dual boot laptop with windows and ubuntu.

I was using ubuntu but then i needed to use windows for some reason , so i shut down ubuntu and start windows but screen showed "Default Boot Device missing or boot failed"

I had bootable USB with kali linux, so I booted kali through USB and tried to find the issue.
First i tried to repair grub, so after some research i found commands to reapair grub through kali
I typed `mount /dev/sda /mnt`

An error occurred about windows being in hibernation.
So i tried solve this issue and after some google search i got to know that all i have to do is boot windows through USB and do fast shutdown to delete hiberfile.sys.
So I made a bootable USB of windows 10 and tried to boot but it again shows "no bootable device".So basically i can't boot windows from USB.

So I figured out there are some issues with my hardisk.

Then I did self-test using Disks and overall assessment was failed from ubuntu using bootable USB.

and after typing `sudo smartctl -a /dev/sdb` in terminal
I got this
```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-15-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model:     TOSHIBA MQ01ABD100
Serial Number:    85QYTDGET
LU WWN Device Id: 5 000039 672089682
Firmware Version: AX003J
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Apr  7 03:10:22 2019 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 112)    The previous self-test completed having
                    the read element of the test failed.
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
recommended polling time:      ( 242) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1534
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       6586
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       784
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       5263
 10 Spin_Retry_Count        0x0033   231   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5429
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       59682
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       228
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       11787
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       38 (Min/Max 15/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       86
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       24
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   088   088   000    Old_age   Always       -       4808
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       265
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 6000 (device log contains only the most recent five errors)
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

Error 6000 occurred at disk power-on lifetime: 5263 hours (219 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 08 00 08 00 40  Error: UNC at LBA = 0x00000800 = 2048

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 00 08 00 40 00      02:35:03.476  READ FPDMA QUEUED
  e5 00 00 00 00 00 00 00      02:35:01.197  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:34:56.195  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:34:51.195  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:34:46.196  CHECK POWER MODE

Error 5999 occurred at disk power-on lifetime: 5263 hours (219 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 e8 00 08 00 40  Error: UNC at LBA = 0x00000800 = 2048

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 e8 00 08 00 40 00      02:29:57.744  READ FPDMA QUEUED
  b0 d5 01 09 4f c2 00 00      02:28:51.889  SMART READ LOG
  b0 d5 01 06 4f c2 00 00      02:28:51.882  SMART READ LOG
  b0 d5 01 01 4f c2 00 00      02:28:51.838  SMART READ LOG
  b0 d5 01 00 4f c2 00 00      02:28:51.838  SMART READ LOG

Error 5998 occurred at disk power-on lifetime: 5263 hours (219 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 38 00 08 00 40  Error: UNC at LBA = 0x00000800 = 2048

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 00 08 00 40 00      02:23:06.648  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      02:19:03.590  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      02:19:03.589  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      02:19:03.589  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      02:19:03.588  SET FEATURES [Set transfer mode]

Error 5997 occurred at disk power-on lifetime: 5263 hours (219 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 a8 00 08 00 40  Error: UNC at LBA = 0x00000800 = 2048

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 a8 00 08 00 40 00      02:18:59.495  READ FPDMA QUEUED
  e5 00 00 00 00 00 00 00      02:18:57.220  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:18:52.221  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:18:47.225  CHECK POWER MODE
  e5 00 00 00 00 00 00 00      02:18:42.227  CHECK POWER MODE

Error 5996 occurred at disk power-on lifetime: 5263 hours (219 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 20 00 08 00 40  Error: UNC at LBA = 0x00000800 = 2048

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 58 18 08 32 40 00      02:17:19.979  READ FPDMA QUEUED
  60 68 50 88 07 32 40 00      02:17:19.979  READ FPDMA QUEUED
  60 80 48 00 07 32 40 00      02:17:19.979  READ FPDMA QUEUED
  60 f8 40 00 06 32 40 00      02:17:19.979  READ FPDMA QUEUED
  60 08 38 20 bb 60 40 00      02:17:19.979  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       00%      5263         2048

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



Issue is definitely with hard disk but idk what the issue is and how to solve it. I can access all the data of my hard disk through kali live.
Help me , if possible.
Thanks,

---

### Post by Autodave on 2019-04-06
Well, until someone smarter than me can help you, get ALL of your files on that disk backed up!!!!!

---

### Post by oldfred on 2019-04-06
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rahulmawari on 2019-04-07
Hi oldfred thanks for helping.
I got this after running boot-repair for info
[http://paste.ubuntu.com/p/RrmNtfj4tF/](http://paste.ubuntu.com/p/RrmNtfj4tF/)

Thanks,

---

### Post by yancek on 2019-04-07
Your output shows the currently unsupported Ubuntu 17.10 on sda7 with an apparent attempt to install 18.04 on sda9.  This second partition (sda9) does not appear to have Grub properly installed, no grub,cfg file.  Which Ubuntu had you been using, 17.10?  There is a proper grub.cfg file for 17.10 on sda7 which has Ubuntu/windows menuentries.  It shows 2 EFI partitions and there should only be 1 per drive (sda1, sda8).  Neither shows the correct EFI files for windows or Ubuntu?  You might try to manually mount either of those partitions to see if those files exist.  Boot repair also shows your windows is still hibernated which of course cannot be changed except from inside windows due to microsoft.  Have you tried the suggestion at the end of boot repair to activate the EFI partition.  Not sure exactly what option you need in boot repair or which EFI it refers to, probably sda1.

---

### Post by rahulmawari on 2019-04-07
Hi yancek,

I was using windows10 and ubuntu 17.10. I tried to install ubuntu 18 yesterday as i can't work in ubuntu live all the time and that installation failed at the last step.

How can i see EFI files for windows or ubuntu?

Thanks,

---

### Post by oldfred on 2019-04-07
It looks like you have some issue with sda1. The unknown issue on sda2 is normal as it is unformatted as required for Microsofts's reserved partition.
But sda1 should not show issues & should show boot files.
And perhaps because the installer could not correctly see sda1 as ESP - efi system partition, it created another ESP. Report is not showing Ubuntu's boot files/folders in that, but sometimes report does not show them even when there.

I would try to repair sda1 as that should have your Windows UEFI boot files., then see if you can copy Ubuntu's boot files from sda8 to sda1, or remove sda8 and from Boot-Repair do a full reinstall of grub from advanced options. Multiple settings need to be changed to use correct ESP, and installing grub is probably the easiest. 

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Then see if you can see the files in sda1. In some extreme cases, we have to delete sda1 & recreate it. But you also have to restore Windows boot files.

You also have an Acer. You do show ubuntu entries, but also the unknown entries.
With Acer you have to set "trust" of the .efi boot files & name them.
       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
You also have UEFI system & UEFI installs, but old BIOS boot loaders in the gpt protective MBR. Do not try to boot in BIOS boot mode.

---

### Post by rahulmawari on 2019-04-08
Sorry for late reply, I was busy yesterday.

"sudo dosfsck -t -a -w /dev/sda1" gave me 
"Read 512 bytes at 0:Input/output error

"


then i tried this from terminal
sudo mount -t ntfs-3g /dev/sda1 /mnt




I got this:
"
Error reading bootsector: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


"

Thanks

---

### Post by rahulmawari on 2019-04-08
I can see these partitions from ubuntu live:
[IMG]https://drive.google.com/file/d/1G3KT99eaa2KLS9q3NjN5ZpwcHr40EL5l/view?usp=sharing[/IMG]

---

### Post by oldfred on 2019-04-08
If your sda1 is the ESP, then it is FAT32,not NTFS. So it will not mount as NTFS, but needs vfat driver.

Usually mount command is smart enough to know format.
       sudo mount /dev/sda1 /mnt 
    or:
       sudo mount -t vfat /dev/sda1 /mnt

---

### Post by rahulmawari on 2019-04-08
"sudo mount -t vfat /dev/sda1 /mnt"

is giving me:
"mount: /mnt: can't read superblock on /dev/sda1."

---

### Post by rahulmawari on 2019-04-08
sudo mount -t vfat /dev/sda1 /mnt  gave me : mount: /mnt: can't read superblock on /dev/sda1.

sudo fsck -y /dev/sda1 gave me : 

"e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Input/output error while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>"

---

### Post by rahulmawari on 2019-04-08
sudo mount -t vfat /dev/sda1 /mnt gave me :" mount: /mnt: can't read superblock on /dev/sda1."

sudo fsck -y /dev/sda1 gave me:
"
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Input/output error while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

"

---

### Post by oldfred on 2019-04-08
Fsck is only for the ext family of formats, usually now ext4, but some ext2 for boot partitions with LVM.

You want dosfsck as detailed in post #8. And it needs to be unmounted to run dosfsck.

---

### Post by rahulmawari on 2019-04-08
sudo dosfsck -t -a -w /dev/sda1  causing this error "Read 512 bytes at 0:Input/output error"

---

### Post by oldfred on 2019-04-08
Then about all we can do is delete partition and create a new ESP in its place. 
It must be FAT32 with boot flag and/or esp flag if using gparted.

All the files & folders can be recreated with full reinstall of grub using live installer and full set of repairs to Windows using your repair/recovery flash drive or installer with repair console..
You also need to first remove boot flag from second ESP that was created by Ubuntu, or fully delete that partition.

---

### Post by rahulmawari on 2019-04-09
Okay, I don't want to lose any important data.
And I have never done these kinds of things.
So would you please explain what should i do in more details with steps.
Thanks,

---

### Post by oldfred on 2019-04-09
You must always have backups as any modification to partitions/drives  or installs can cause loss of data. Also hard drives do fail, lately they have become more reliable but that just makes the lose worse as then more users are not backing up and have more data.

For Ubuntu and standard desktop I just backup /home, my data (most users have it all in /home, but may have other partitions), and a list of installed apps. I do make only a few changes to system settings like in my grub configuration, but just copy those when I change them into /home so my regular backup includes those. If making a lot of changes to system you want to include /etc. Only if a server or have installed server applications, then you should know all the extra folders in / (root) that need backup.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
      [/URL]
 Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc) 
    
After you have confirmed you have good backups, or your install is brand new and has nothing to save, then you can use gparted to delete & add new partition. You have to use live installer in live mode or a gparted live flash drive, as all partitions must be unmounted.
       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions) 
    [URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

### Post by rahulmawari on 2019-04-10
I can't open gparted.
It's giving me error:
"Input/output error during read on /dev/sda"

---

### Post by Autodave on 2019-04-10
Generally when I see a superblock error, I know that I am not going to be able to save anything on that disk.  Sometimes, wiping the disk completely and reformatting it will save it.  The only thing that I can suggest at this point is to make a linux installation medium and try booting from that and then see if you are able to ead the disk and copy files to an offline source.

---

### Post by oldfred on 2019-04-10
Will gdisk from live installer see drive?

sudo gdisk -l /dev/sda

Or is drive failing, in live installer & Disks and in upper right corner is Smart Status. It can run tests, but pass/fail is all I ever look at.

---

### Post by rahulmawari on 2019-04-10
Hi ,
A quick update:
Actually windows ISO image that i used to make bootable usb was corrupted(though i downloaded that from official site) that's why I could not boot windows from bootable usb. So I have made a new windows bootable USB using correct ISO image. When I boot windows using usb then I had to choose between upgrade windows or install a new window 10 for that i will have to format hard disk.
So, i chose upgrade windows but i got error that i can't upgrade windows , i have to boot from install windows then upgrade that i can't.


Yes, i can see drive:
Output of sudo gdisk -l /dev/sda:
"
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Model: TOSHIBA MQ01ABD1
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): A76D0D8B-AAB4-49D6-A8A9-956B2B40C6DD
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 8244 sectors (4.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          239615   16.0 MiB    0C01  Microsoft reserved ...
   3          239616       489818111   233.4 GiB   0700  Basic data partition
   4       489818112       937159178   213.3 GiB   0700  Basic data partition
   5      1221158912      1952496429   348.7 GiB   0700  Basic data partition
   6      1952499712      1953523711   500.0 MiB   2700  Basic data partition
   7      1036836864      1221158911   87.9 GiB    8300  
   8       937160704       938209279   512.0 MiB   EF00  EFI System Partition
   9       938209280      1036836863   47.0 GiB    8300  
"



Test are failed in disks smart self tests

---

### Post by Autodave on 2019-04-10
Then the drive is failed and you are unlikely to recover anything from it.  Again, you *may*be able to reformat it and make it workable again, but I would not trust it for anything important.

---

### Post by oldfred on 2019-04-10
While Smart disk will sometimes show failed on a good drive, I would never trust a failed drive.

Since gdisk showed partitions can you use it to delete sda1 & sda8 and create new sda1 (may not be called sda1) in place of old sda1 with ef00 tag so seen as ESP. format as FAT32.
       GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by rahulmawari on 2019-04-11
This is what i got after "sudo gdisk /dev/sda1"

"
GPT fdisk (gdisk) version 1.0.3

Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): d
No partitions

Command (? for help): 

"

---

### Post by oldfred on 2019-04-11
Bit strange drive seen one time and not next.
Double check all connectors are tight.

---

### Post by rahulmawari on 2019-04-19
I formatted everything and now I can run windows.  Some connection are loose i guess  that's why i am getting "i/o error dev sector" while trying to install ubuntu

---

