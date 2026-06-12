---
title: "SMART Self-test reports read failure: is my hard disk dying?"
date: 2009-03-04
forum: Hardware
---

### Post by giacof on 2009-03-04
Hello,

I am running Kubuntu Intrepid on a Presario 773EL laptop, equipped with a Western Digital Scorpio HDD.
I recently experienced a I/O error in reading a file, as reported by dmesg:

```
[   35.790523] EXT3 FS on dm-1, internal journal
[   37.099360] kjournald starting.  Commit interval 5 seconds
[   37.099676] EXT3 FS on sda3, internal journal
[   37.099685] EXT3-fs: mounted filesystem with ordered data mode.
[   37.622711] type=1505 audit(1236124579.399:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4181
[   37.622956] type=1505 audit(1236124579.399:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4181
[   37.792320] ip_tables: (C) 2000-2006 Netfilter Core Team
[  321.346417] EXT3 FS on dm-1, internal journal
[  709.786606] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  709.786674] ata1.00: BMDMA stat 0x4
[  709.786736] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  709.786738]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  709.786879] ata1.00: status: { DRDY ERR }
[  709.786931] ata1.00: error: { UNC }
[  709.824355] ata1.00: configured for UDMA/100
[  709.824363] ata1: EH complete
[  712.818633] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  712.818701] ata1.00: BMDMA stat 0x4
[  712.818763] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  712.818765]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  712.818907] ata1.00: status: { DRDY ERR }
[  712.818959] ata1.00: error: { UNC }
[  712.840349] ata1.00: configured for UDMA/100
[  712.840361] ata1: EH complete
[  715.684459] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  715.684520] ata1.00: BMDMA stat 0x4
[  715.684580] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  715.684583]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  715.684724] ata1.00: status: { DRDY ERR }
[  715.684776] ata1.00: error: { UNC }
[  715.708371] ata1.00: configured for UDMA/100
[  715.708378] ata1: EH complete
[  718.551311] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  718.551372] ata1.00: BMDMA stat 0x4
[  718.551434] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  718.551436]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  718.551577] ata1.00: status: { DRDY ERR }
[  718.551629] ata1.00: error: { UNC }
[  718.572349] ata1.00: configured for UDMA/100
[  718.572357] ata1: EH complete
[  721.561274] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  721.561337] ata1.00: BMDMA stat 0x4
[  721.561398] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  721.561400]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  721.561541] ata1.00: status: { DRDY ERR }
[  721.561593] ata1.00: error: { UNC }
[  721.584370] ata1.00: configured for UDMA/100
[  721.584377] ata1: EH complete
[  724.715409] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  724.715470] ata1.00: BMDMA stat 0x4
[  724.715530] ata1.00: cmd 25/00:b8:dd:3d:0f/00:00:12:00:00/e0 tag 0 dma 94208 in
[  724.715533]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  724.715673] ata1.00: status: { DRDY ERR }
[  724.715725] ata1.00: error: { UNC }
[  724.736372] ata1.00: configured for UDMA/100
[  724.736387] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  724.736392] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  724.736399] Descriptor sense data with sense descriptors (in hex):
[  724.736402]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  724.736416]         12 0f 3d e8 
[  724.736422] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  724.736430] end_request: I/O error, dev sda, sector 302988776
[  724.736531] ata1: EH complete
[  724.742585] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  724.742847] sd 0:0:0:0: [sda] Write Protect is off
[  724.742850] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  724.751805] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  724.752421] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  724.752700] sd 0:0:0:0: [sda] Write Protect is off
[  724.752705] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  724.757622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  727.825912] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  727.825979] ata1.00: BMDMA stat 0x4
[  727.826040] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  727.826043]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  727.826183] ata1.00: status: { DRDY ERR }
[  727.826235] ata1.00: error: { UNC }
[  727.848356] ata1.00: configured for UDMA/100
[  727.848364] ata1: EH complete
[  730.992068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  730.992130] ata1.00: BMDMA stat 0x4
[  730.992191] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  730.992193]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  730.992334] ata1.00: status: { DRDY ERR }
[  730.992385] ata1.00: error: { UNC }
[  731.016353] ata1.00: configured for UDMA/100
[  731.016360] ata1: EH complete
[  734.013026] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  734.013088] ata1.00: BMDMA stat 0x4
[  734.013147] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  734.013149]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  734.013291] ata1.00: status: { DRDY ERR }
[  734.013342] ata1.00: error: { UNC }
[  734.036369] ata1.00: configured for UDMA/100
[  734.036375] ata1: EH complete
[  737.046068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  737.046130] ata1.00: BMDMA stat 0x4
[  737.046191] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  737.046193]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  737.046334] ata1.00: status: { DRDY ERR }
[  737.046386] ata1.00: error: { UNC }
[  737.068353] ata1.00: configured for UDMA/100
[  737.068359] ata1: EH complete
[  740.068041] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  740.068103] ata1.00: BMDMA stat 0x4
[  740.068163] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  740.068165]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  740.068306] ata1.00: status: { DRDY ERR }
[  740.068358] ata1.00: error: { UNC }
[  740.092371] ata1.00: configured for UDMA/100
[  740.092378] ata1: EH complete
[  743.100069] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  743.100130] ata1.00: BMDMA stat 0x4
[  743.100191] ata1.00: cmd 25/00:08:e5:3d:0f/00:00:12:00:00/e0 tag 0 dma 4096 in
[  743.100193]          res 51/40:00:e8:3d:0f/40:00:12:00:00/e0 Emask 0x9 (media error)
[  743.100334] ata1.00: status: { DRDY ERR }
[  743.100385] ata1.00: error: { UNC }
[  743.124350] ata1.00: configured for UDMA/100
[  743.124359] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  743.124364] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  743.124370] Descriptor sense data with sense descriptors (in hex):
[  743.124373]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  743.124387]         12 0f 3d e8 
[  743.124393] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  743.124402] end_request: I/O error, dev sda, sector 302988776
[  743.124469] ata1: EH complete
[  743.126679] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  743.126714] sd 0:0:0:0: [sda] Write Protect is off
[  743.126719] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  743.126772] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  743.126823] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  743.126852] sd 0:0:0:0: [sda] Write Protect is off
[  743.126863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  743.126896] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Then I made some SMART tests (both a short and a long one) which resulted in the following report:

```
~$ sudo smartctl --all /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                        

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD1600BEVS-60RST0         
Serial Number:    WD-WXC408K86958               
Firmware Version: 04.01G04                      
User Capacity:    160,041,885,696 bytes         
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7                                              
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Mar  4 14:42:18 2009 CET                       
SMART support is: Available - device has SMART capability.           
SMART support is: Enabled                                            

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.              
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.   
Total time to complete Offline                                                 
data collection:                 (6780) seconds.                               
Offline data collection                                                        
capabilities:                    (0x5b) SMART execute Offline immediate.       
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new         
                                        command.                                    
                                        Offline surface scan supported.             
                                        Self-test supported.                        
                                        No Conveyance Self-test supported.          
                                        Selective Self-test supported.              
SMART capabilities:            (0x0003) Saves SMART data before entering            
                                        power-saving mode.                          
                                        Supports SMART auto save timer.             
Error logging capability:        (0x01) Error logging supported.                    
                                        General Purpose Logging supported.          
Short self-test routine                                                             
recommended polling time:        (   2) minutes.                                    
Extended self-test routine                                                          
recommended polling time:        (  87) minutes.                                    
SCT capabilities:              (0x103f) SCT Status supported.                       
                                        SCT Feature Control supported.              
                                        SCT Data Table supported.                   

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:  
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       1        
  3 Spin_Up_Time            0x0003   187   187   021    Pre-fail  Always       -       1608     
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       437      
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0        
  7 Seek_Error_Rate         0x000f   100   253   051    Pre-fail  Always       -       0        
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1282     
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0        
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0        
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       264      
187 Reported_Uncorrect      0x0032   060   058   000    Old_age   Always       -       79       
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0        
190 Airflow_Temperature_Cel 0x0022   056   048   040    Old_age   Always       -       44       
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       42       
193 Load_Cycle_Count        0x0032   191   191   000    Old_age   Always       -       29500    
194 Temperature_Celsius     0x0022   103   095   000    Old_age   Always       -       44       
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0        
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       1        
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0        
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0        
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0        

SMART Error Log Version: 1
ATA Error Count: 81 (device log contains only the most recent five errors)
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

Error 81 occurred at disk power-on lifetime: 1278 hours (53 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 08 e5 3d 0f e0  Error: UNC 8 sectors at LBA = 0x000f3de5 = 998885

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 e5 3d 0f 12 00      03:32:52.344  READ DMA EXT        
  ec 00 00 00 00 00 00 00      03:32:52.336  IDENTIFY DEVICE     
  ef 03 45 00 00 00 00 00      03:32:52.329  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      03:32:52.320  IDENTIFY DEVICE                 
  25 00 08 e5 3d 0f 12 00      03:32:49.323  READ DMA EXT                    

Error 80 occurred at disk power-on lifetime: 1278 hours (53 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 08 e5 3d 0f e0  Error: UNC 8 sectors at LBA = 0x000f3de5 = 998885

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 e5 3d 0f 12 00      03:32:49.323  READ DMA EXT        
  ec 00 00 00 00 00 00 00      03:32:49.315  IDENTIFY DEVICE     
  ef 03 45 00 00 00 00 00      03:32:49.308  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      03:32:49.301  IDENTIFY DEVICE                 
  25 00 08 e5 3d 0f 12 00      03:32:46.294  READ DMA EXT                    

Error 79 occurred at disk power-on lifetime: 1278 hours (53 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 08 e5 3d 0f e0  Error: UNC 8 sectors at LBA = 0x000f3de5 = 998885

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 e5 3d 0f 12 00      03:32:46.294  READ DMA EXT        
  ec 00 00 00 00 00 00 00      03:32:46.286  IDENTIFY DEVICE     
  ef 03 45 00 00 00 00 00      03:32:46.279  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      03:32:46.271  IDENTIFY DEVICE                 
  25 00 08 e5 3d 0f 12 00      03:32:43.277  READ DMA EXT                    

Error 78 occurred at disk power-on lifetime: 1278 hours (53 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 08 e5 3d 0f e0  Error: UNC 8 sectors at LBA = 0x000f3de5 = 998885

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 e5 3d 0f 12 00      03:32:43.277  READ DMA EXT        
  ec 00 00 00 00 00 00 00      03:32:43.269  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      03:32:43.262  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      03:32:43.253  IDENTIFY DEVICE
  25 00 08 e5 3d 0f 12 00      03:32:40.112  READ DMA EXT

Error 77 occurred at disk power-on lifetime: 1278 hours (53 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 e5 3d 0f e0  Error: UNC 8 sectors at LBA = 0x000f3de5 = 998885

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 e5 3d 0f 12 00      03:32:40.112  READ DMA EXT
  ec 00 00 00 00 00 00 00      03:32:40.104  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      03:32:40.097  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      03:32:40.090  IDENTIFY DEVICE
  25 00 08 e5 3d 0f 12 00      03:32:37.253  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      1282         302988776
# 2  Extended offline    Completed: read failure       90%      1279         302988776

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

How should I interpret such information? Is it just about one isolated damaged sector or may that indicate a total HDD failure is imminent?
Any help would be highly appreciated.

---

### Post by tgalati4 on 2009-03-16
UNC's are uncorrectable errors.  It's possible that you suffered a head crash causing a scratch and bad sectors.  Try running:

>sudo badblocks /dev/sda1

Depending on how many bad blocks are on the disk, you can work around them with this command:

>sudo fsck -cc /dev/sda1

(Be sure to check your partitions, your actual operating system may be located at /dev/sda5 depending how you have the drive set up.)

I have a similar error on one of my WD Raptors that I'm trying to figure out.

---

