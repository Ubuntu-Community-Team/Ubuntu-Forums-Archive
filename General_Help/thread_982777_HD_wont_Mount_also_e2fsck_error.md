---
title: "HD wont Mount also e2fsck error"
date: 2008-11-15
forum: General Help
---

### Post by killaray on 2008-11-15
haven't needed help in quiet some time and have been happy with Ubuntu 8.04 but decided to try out kubuntu 8.10... well one day one of my HDs suddenly wouldn't mount, I researched it a bit and saw that maybe I should run fsck or e2fsck to see if it could fix the problem... well it can't and gives me the wonderful error

```
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda1
```


then I've tried testdisk to try and repair the drive, and can see that the files are all still intact which I'm happy about... now all i kindly ask you guys is if you could help me completely fix this issue... I've tried rebuilding the partition structure, which did nothing for me

heres the testdisk log
```


Wed Nov 12 00:24:30 2008
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAJS-0
Disk /dev/sdb - 60 GB / 55 GiB - CHS 7299 255 63, sector size=512 - ATA MAXTOR 4K060H3
Disk /dev/sdc - 203 GB / 189 GiB - CHS 24792 255 63, sector size=512 - ATA Maxtor 6B200P0

Disk /dev/sda - 500 GB / 465 GiB - ATA WDC WD5000AAJS-0
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * Linux                    0   1  1 60800 254 63  976768002
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/3726, s_mnt_count=130/27, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 122096000
recover_EXT2: part_size 976768000
   D Linux                    0   1  1 60800 254 61  976768000
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1 60800 254 63  976768002
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB

interface_write()
 1 P Linux                    0   1  1 60800 254 63  976768002

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/3726, s_mnt_count=130/27, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 122096000
recover_EXT2: part_size 976768000
   D Linux                    0   1  1 60800 254 61  976768000
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/3726, s_mnt_count=0/27, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 122096000
recover_EXT2: part_size 976768000
   D Linux                    0   1  1 60800 254 61  976768000
     EXT3 Large file Sparse superblock Backup superblock, 500 GB / 465 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1 60800 254 63  976768002
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB

interface_write()
 1 P Linux                    0   1  1 60800 254 63  976768002
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * Linux                    0   1  1 60800 254 63  976768002
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/3726, s_mnt_count=130/27, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 122096000
recover_EXT2: part_size 976768000
   D Linux                    0   1  1 60800 254 61  976768000
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1 60800 254 63  976768002
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB

interface_write()
 1 * Linux                    0   1  1 60800 254 63  976768002
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * Linux                    0   1  1 60800 254 63  976768002
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

recover_EXT2: s_block_group_nr=0/3726, s_mnt_count=130/27, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 122096000
recover_EXT2: part_size 976768000
   D Linux                    0   1  1 60800 254 61  976768000
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1 60800 254 63  976768002
     EXT3 Large file Sparse superblock, 500 GB / 465 GiB

interface_write()
 1 P Linux                    0   1  1 60800 254 63  976768002
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
You will have to reboot for the change to take effect.

TestDisk exited normally.
```

I ran it multiple times so there might be alot of repeated lines, sorry about that..

is there anyone here that could help me recover this without having to backup to another drive and do all that nonsense.. plz

---

### Post by cariboo on 2008-11-15
Boot from the LiveCD and run fsck with out any options on your hard drive. Be prepared to press the **Y** quite a few times.

Jim

---

### Post by killaray on 2008-11-15
I've run fsck a couple times from parted magic live cd and it gives the same error

---

### Post by killaray on 2008-11-15
anyone have any suggestions?

---

### Post by killaray on 2008-11-16
any hard drive recovery gurus? i know there are... please help

---

### Post by ellgor on 2008-11-16
Hi,

I had similar problems with one of my hdd's not being mounted/recognised, none of the window managers - disk-checkers  whatever would mount or read it and then quite by chance I was using Abiword at the time and when I went to save, it showed the hdd as an option to save to, which I promptly did.
After that the hdd was available to the system, however, upon rebooting the same thing happened and again Abiword opened it, whilst not a fix, it does enable your files to be accessed, hope this of some use (you could try a different app instead of Abiword, who knows).

Regards, Ellgor.

---

### Post by killaray on 2008-11-17
Ellgor, ive tried that and it didnt work cause the drive wont mount...

to Cariboo, i've also attempted fsck and it results in the same error message...

```
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda1
```

can anyone help please

---

### Post by cariboo on 2008-11-17
If you are getting an error after running fsck, I would suggest that you go to your hard drives manufacturers web site and download the diagnostic tools for your hard drive and run them. If you have an unrecoverable error, the utilities will tell you if your hard drive needs replacing. If it is new enough, you may be able to get an RMA and have it replaced under warranty.

Jim

---

### Post by psusi on 2008-11-17
Sounds like your disk has developed a bad sector.  Install the smartmontools package and post the output of sudo smartctl -a /dev/sda ( assuming sda is the disk in question ).

---

### Post by killaray on 2008-11-17
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                        

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAJS-00YFA0                                     
Serial Number:    WD-WCAS82048017                                           
Firmware Version: 12.01C02                                                  
User Capacity:    500,107,862,016 bytes                                     
Device is:        In smartctl database [for details use: -P show]           
ATA Version is:   8                                                         
ATA Standard is:  Exact ATA specification draft version not indicated       
Local Time is:    Mon Nov 17 23:30:55 2008 EST                              
SMART support is: Available - device has SMART capability.                  
SMART support is: Enabled                                                   

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.    
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever  
                                        been run.                               
Total time to complete Offline                                                  
data collection:                 (13200) seconds.                               
Offline data collection                                                         
capabilities:                    (0x7b) SMART execute Offline immediate.        
                                        Auto Offline data collection on/off support.                                                                            
                                        Suspend Offline collection upon new     
                                        command.                                
                                        Offline surface scan supported.         
                                        Self-test supported.                    
                                        Conveyance Self-test supported.         
                                        Selective Self-test supported.          
SMART capabilities:            (0x0003) Saves SMART data before entering        
                                        power-saving mode.                      
                                        Supports SMART auto save timer.         
Error logging capability:        (0x01) Error logging supported.                
                                        General Purpose Logging supported.      
Short self-test routine                                                         
recommended polling time:        (   2) minutes.                                
Extended self-test routine                                                      
recommended polling time:        ( 154) minutes.                                
Conveyance self-test routine                                                    
recommended polling time:        (   5) minutes.                                
SCT capabilities:              (0x303f) SCT Status supported.                   
                                        SCT Feature Control supported.          
                                        SCT Data Table supported.               

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:  
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE                                                                
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0                                                                        
  3 Spin_Up_Time            0x0003   236   166   021    Pre-fail  Always       -       3191                                                                     
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       286                                                                      
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0                                                                        
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0                                                                        
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       7871                                                                     
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0                                                                        
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0                                                                        
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       186                                                                      
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       550                                                                      
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       661                                                                      
194 Temperature_Celsius     0x0022   111   098   000    Old_age   Always       -       39                                                                       
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0                                                                        
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       2                                                                        
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       2                                                                        
199 UDMA_CRC_Error_Count    0x003e   200   192   000    Old_age   Always       -       20                                                                       
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0                                                                        

SMART Error Log Version: 1
ATA Error Count: 624 (device log contains only the most recent five errors)
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

Error 624 occurred at disk power-on lifetime: 7861 hours (327 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 02 5b 20 00 00 08   2d+11:29:54.606  READ DMA            
  27 00 00 00 00 00 00 08   2d+11:29:54.606  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   2d+11:29:54.597  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08   2d+11:29:54.590  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   2d+11:29:54.590  READ NATIVE MAX ADDRESS EXT     

Error 623 occurred at disk power-on lifetime: 7861 hours (327 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 02 5b 20 00 00 08   2d+11:29:51.313  READ DMA            
  27 00 00 00 00 00 00 08   2d+11:29:51.313  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   2d+11:29:51.304  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08   2d+11:29:51.297  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   2d+11:29:51.297  READ NATIVE MAX ADDRESS EXT     

Error 622 occurred at disk power-on lifetime: 7861 hours (327 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 02 5b 20 00 00 08   2d+11:29:48.020  READ DMA            
  27 00 00 00 00 00 00 08   2d+11:29:48.020  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   2d+11:29:48.011  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08   2d+11:29:48.004  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   2d+11:29:48.004  READ NATIVE MAX ADDRESS EXT     

Error 621 occurred at disk power-on lifetime: 7861 hours (327 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 02 5b 20 00 00 08   2d+11:29:44.731  READ DMA            
  27 00 00 00 00 00 00 08   2d+11:29:44.731  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   2d+11:29:44.722  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08   2d+11:29:44.715  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   2d+11:29:44.715  READ NATIVE MAX ADDRESS EXT

Error 620 occurred at disk power-on lifetime: 7861 hours (327 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 02 5b 20 00 00 08   2d+11:29:41.439  READ DMA
  27 00 00 00 00 00 00 08   2d+11:29:41.439  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   2d+11:29:41.430  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   2d+11:29:41.423  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   2d+11:29:41.423  READ NATIVE MAX ADDRESS EXT

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

### Post by psusi on 2008-11-17
Yep, you got two bad sectors so far.  Start a self test and see where it finds the first error, then you can try to force the drive to remap the sector:

```
sudo smartctl -t long /dev/sda
sudo smartctl -l selftest /dev/sda
```

The first starts the test, which can take quite a while.  The second will check on the status.  Once it hits the bad sector it should show that it found it when you run the second command.  Take note of the number and then:

```
sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct count=1 skip=NNNN
```

Where NNNN is the sector number from the selftest log.  That should come back with an IO error if you got it right, confirming that you are trying to read the bad sector.  If it does, then zero the sector, which will force the drive to remap the sector to a fresh one if it can't correctly write to the media:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 oflag=direct count=1 seek=NNNN
```

Then try the read again and it should work this time.  Repeat this until the selftest doesn't find any more bad sectors, then fsck the filesystem and hope it can recover.

---

### Post by killaray on 2008-11-18
Thank god for copy/paste lol, anywho I left my house for the night so ill give this a shot tomorrow... thanx for the help and I'll let u know how it went

---

### Post by killaray on 2008-11-19
> **psusi said:**
> Yep, you got two bad sectors so far.  Start a self test and see where it finds the first error, then you can try to force the drive to remap the sector:

```
sudo smartctl -t long /dev/sda
sudo smartctl -l selftest /dev/sda
```

The first starts the test, which can take quite a while.  The second will check on the status.  Once it hits the bad sector it should show that it found it when you run the second command.  Take note of the number and then:

```
sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct count=1 skip=NNNN
```

Where NNNN is the sector number from the selftest log.  That should come back with an IO error if you got it right, confirming that you are trying to read the bad sector.  If it does, then zero the sector, which will force the drive to remap the sector to a fresh one if it can't correctly write to the media:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 oflag=direct count=1 seek=NNNN
```

Then try the read again and it should work this time.  Repeat this until the selftest doesn't find any more bad sectors, then fsck the filesystem and hope it can recover.

first and second command gimme this...
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                        

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".                                                                       
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.                                                               
Testing has begun.                                                              
Please wait 154 minutes for test to complete.                                   
Test will complete after Tue Nov 18 17:17:31 2008                               

Use smartctl -X to abort test.

```

then

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      7871         8284
# 2  Extended offline    Completed: read failure       90%      7871         8284

```

wuts it mean.. or if u dont wanna explain just wut do i do next? are the LBA the numbers i substitute in for NNNN?

---

### Post by psusi on 2008-11-19
It is pretty self explanatory.  The test failed to read sector 8284, so that's what you use for NNNN.

---

### Post by killaray on 2008-11-19
ur such a beautiful person psusi... thank you that worked... lol

---

### Post by psusi on 2008-11-19
Now you might want to check the output of smartctl -a again and look at the relocated sector count.  If the sector just got corrupted and the drive was able to rewrite it without a problem, the relocated count should still be 0.  If the media is physically damaged and can not be written to, then the drive will have relocated it.  If this is the case, you might want to think about getting a new drive because once media defects start, they tend to spread.

---

### Post by killaray on 2008-11-19
Once I get home ill give that a go... thanx again for all ur help

---

### Post by killaray on 2008-11-20
where do u find the number of relocated sectors?

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAJS-00YFA0                                     
Serial Number:    WD-WCAS82048017                                           
Firmware Version: 12.01C02                                                  
User Capacity:    500,107,862,016 bytes                                     
Device is:        In smartctl database [for details use: -P show]           
ATA Version is:   8                                                         
ATA Standard is:  Exact ATA specification draft version not indicated       
Local Time is:    Thu Nov 20 01:24:17 2008 EST                              
SMART support is: Available - device has SMART capability.                  
SMART support is: Enabled                                                   

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.    
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.   
Total time to complete Offline                                                 
data collection:                 (13200) seconds.                              
Offline data collection                                                        
capabilities:                    (0x7b) SMART execute Offline immediate.       
                                        Auto Offline data collection on/off support.                                                                            
                                        Suspend Offline collection upon new     
                                        command.                                
                                        Offline surface scan supported.         
                                        Self-test supported.                    
                                        Conveyance Self-test supported.         
                                        Selective Self-test supported.          
SMART capabilities:            (0x0003) Saves SMART data before entering        
                                        power-saving mode.                      
                                        Supports SMART auto save timer.         
Error logging capability:        (0x01) Error logging supported.                
                                        General Purpose Logging supported.      
Short self-test routine                                                         
recommended polling time:        (   2) minutes.                                
Extended self-test routine                                                      
recommended polling time:        ( 154) minutes.                                
Conveyance self-test routine                                                    
recommended polling time:        (   5) minutes.                                
SCT capabilities:              (0x303f) SCT Status supported.                   
                                        SCT Feature Control supported.          
                                        SCT Data Table supported.               

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:  
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE                                                                
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0                                                                        
  3 Spin_Up_Time            0x0003   176   166   021    Pre-fail  Always       -       6191                                                                     
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       290                                                                      
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0                                                                        
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0                                                                        
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       7906                                                                     
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0                                                                        
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0                                                                        
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       190                                                                      
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       554                                                                      
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       667                                                                      
194 Temperature_Celsius     0x0022   108   098   000    Old_age   Always       -       42                                                                       
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0                                                                        
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0                                                                        
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0                                                                        
199 UDMA_CRC_Error_Count    0x003e   200   192   000    Old_age   Always       -       20                                                                       
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0                                                                        

SMART Error Log Version: 1
ATA Error Count: 630 (device log contains only the most recent five errors)
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

Error 630 occurred at disk power-on lifetime: 7892 hours (328 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 5c 20 00 00 08      20:38:09.043  READ DMA            
  27 00 00 00 00 00 00 08      20:38:09.043  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      20:38:09.033  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08      20:38:09.026  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      20:38:09.026  READ NATIVE MAX ADDRESS EXT     

Error 629 occurred at disk power-on lifetime: 7892 hours (328 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 5c 20 00 00 08      20:38:05.757  READ DMA            
  27 00 00 00 00 00 00 08      20:38:05.757  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      20:38:05.748  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08      20:38:05.741  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      20:38:05.741  READ NATIVE MAX ADDRESS EXT     

Error 628 occurred at disk power-on lifetime: 7892 hours (328 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 5c 20 00 00 08      20:38:02.285  READ DMA            
  27 00 00 00 00 00 00 08      20:38:02.285  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      20:38:02.276  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08      20:38:02.269  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      20:38:02.269  READ NATIVE MAX ADDRESS EXT     

Error 627 occurred at disk power-on lifetime: 7892 hours (328 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.                                                                               

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 5c 20 00 00 08      20:37:58.820  READ DMA            
  27 00 00 00 00 00 00 08      20:37:58.820  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      20:37:58.811  IDENTIFY DEVICE            
  ef 03 46 00 00 00 00 08      20:37:58.804  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      20:37:58.804  READ NATIVE MAX ADDRESS EXT     

Error 626 occurred at disk power-on lifetime: 7892 hours (328 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 5c 20 00 e0  Error: UNC at LBA = 0x0000205c = 8284

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 5c 20 00 00 08      20:37:55.879  READ DMA
  27 00 00 00 00 00 00 08      20:37:55.879  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      20:37:55.870  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      20:37:55.870  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      20:37:55.859  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      7871         8284
# 2  Extended offline    Completed: read failure       90%      7871         8284

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

is it this one?
```
5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0 
```

---

### Post by psusi on 2008-11-20
Yep, looks like the sector just got corrupted somehow and the media is ok.  But it looks like you never ran another test after fixing the first one to make sure there aren't any more.

---

### Post by killaray on 2008-11-21
> **psusi said:**
> Yep, looks like the sector just got corrupted somehow and the media is ok.  But it looks like you never ran another test after fixing the first one to make sure there aren't any more.

it gave me this after running the test again

```
== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7922         -
# 2  Extended offline    Completed: read failure       90%      7871         8284
# 3  Extended offline    Completed: read failure       90%      7871         8284

```

it says read failure is that bad??

---

### Post by psusi on 2008-11-21
> **killaray said:**
> 
it says read failure is that bad??

That's from the two times you ran it before.  The most recent run completed without error, so it looks to be all good.

---

### Post by killaray on 2008-11-21
> **psusi said:**
> That's from the two times you ran it before.  The most recent run completed without error, so it looks to be all good.

nice.. ok thanx alot for your help again..

---

