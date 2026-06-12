---
title: "SMART error on disk"
date: 2009-11-20
forum: Hardware
---

### Post by billboule on 2009-11-20
Hi,

On a laptop I had problem for reading/writing on an internal harddrive. I used smartmoontools to get an idea on what was going on. It looks like there is an error, but I do not understand everything. Does anyone can help ?

Thanks !

> 
ubuntu@ubuntu:~$  sudo smartctl -a /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)                        

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160 series
Device Model:     Hitachi HTS541612J9SA00        
Serial Number:    SB2541H6G8MB5E                 
Firmware Version: SBDOC70P                       
User Capacity:    120 034 123 776 bytes          
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7                                              
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1               
Local Time is:    Fri Nov 20 16:28:25 2009 UTC                   
SMART support is: Available - device has SMART capability.       
SMART support is: Enabled                                        

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.             
Self-test execution status:      ( 121) The previous self-test completed having            
                                        the read element of the test failed.               
Total time to complete Offline                                                             
data collection:                 ( 645) seconds.                                           
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
recommended polling time:        (  73) minutes.                                           

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:  
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   085   085   062    Pre-fail  Always       -       12976202 
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       2792     
  3 Spin_Up_Time            0x0007   243   243   033    Pre-fail  Always       -       1        
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1347     
  5 Reallocated_Sector_Ct   0x0033   046   046   005    Pre-fail  Always       -       0        
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0        
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0        
  9 Power_On_Hours          0x0012   094   094   000    Old_age   Always       -       2853     
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0        
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1327     
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0        
192 Power-Off_Retract_Count 0x0032   097   097   000    Old_age   Always       -       649      
193 Load_Cycle_Count        0x0012   097   097   000    Old_age   Always       -       36518    
194 Temperature_Celsius     0x0002   148   148   000    Old_age   Always       -       37 (Lifetime Min/Max 6/50)
196 Reallocated_Event_Count 0x0032   028   028   000    Old_age   Always       -       3683                      
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       217                       
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0                         
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       2                         
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0                         

SMART Error Log Version: 1
ATA Error Count: 7480 (device log contains only the most recent five errors)
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

Error 7480 occurred at disk power-on lifetime: 2851 hours (118 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 3c ab 83 f2 4d  Error: UNC 60 sectors at LBA = 0x0df283ab = 233997227

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 80 67 83 f2 4d 00      03:22:43.500  READ DMA            
  ca ff 08 ef 7f b9 4a 00      03:22:43.500  WRITE DMA           
  ca ff 08 3c 65 58 41 00      03:22:43.500  WRITE DMA           
  ea 00 00 00 00 00 00 00      03:22:43.400  FLUSH CACHE EXIT    
  c8 ff 80 67 83 f2 4d 00      03:22:39.300  READ DMA            

Error 7479 occurred at disk power-on lifetime: 2851 hours (118 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 3c ab 83 f2 4d  Error: UNC 60 sectors at LBA = 0x0df283ab = 233997227

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 80 67 83 f2 4d 00      03:22:39.300  READ DMA            
  ca ff 08 b7 bf d9 47 00      03:22:39.300  WRITE DMA           
  ca ff 19 84 9b bc 46 00      03:22:39.300  WRITE DMA           
  ca ff 10 0c a3 58 41 00      03:22:39.300  WRITE DMA           
  c8 ff 40 16 58 fe 40 00      03:22:39.300  READ DMA            

Error 7478 occurred at disk power-on lifetime: 2851 hours (118 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 3c ab 83 f2 4d  Error: UNC 60 sectors at LBA = 0x0df283ab = 233997227

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 80 67 83 f2 4d 00      03:22:35.000  READ DMA            
  ca ff 08 bf d3 f3 48 00      03:22:35.000  WRITE DMA           
  c8 ff 08 dc 66 35 42 00      03:22:35.000  READ DMA            
  ca ff 10 fc a2 58 41 00      03:22:35.000  WRITE DMA           
  c8 ff 80 67 83 f2 4d 00      03:22:30.800  READ DMA            

Error 7477 occurred at disk power-on lifetime: 2851 hours (118 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH                              
  -- -- -- -- -- -- --                              
  40 51 3c ab 83 f2 4d  Error: UNC 60 sectors at LBA = 0x0df283ab = 233997227

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 80 67 83 f2 4d 00      03:22:30.800  READ DMA            
  ca ff 20 87 50 da 47 00      03:22:30.800  WRITE DMA           
  ca ff 08 af bf d7 47 00      03:22:30.800  WRITE DMA           
  ca ff 08 04 5a 5a 41 00      03:22:30.800  WRITE DMA
  ca ff 08 f4 a2 58 41 00      03:22:30.800  WRITE DMA

Error 7476 occurred at disk power-on lifetime: 2851 hours (118 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3c ab 83 f2 4d  Error: UNC 60 sectors at LBA = 0x0df283ab = 233997227

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 80 67 83 f2 4d 00      03:22:26.600  READ DMA
  ca ff 08 6f 21 c3 48 00      03:22:26.600  WRITE DMA
  ca ff 08 bf bf d7 47 00      03:22:26.600  WRITE DMA
  c8 ff 08 34 04 6d 47 00      03:22:26.500  READ DMA
  ca ff 08 9c 27 fa 40 00      03:22:26.500  WRITE DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      2853         234008184

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


---

### Post by movieman on 2009-11-20
I believe 'UNC' means an uncorrectable data error, so it would appear that you've lost at least some data on that disk. 

I'm not entirely sure what Reallocated_Event_Count means, but if it's the number of sectors reallocated due to errors then you should think about getting a new disk :).

---

### Post by billboule on 2009-11-21
Hi Movieman,

Thanks for the help... i will definitely replace it, let see if the warranty will work.
Any idea on the way I can save the data ? I tried with a live CD but every time there is a reading error, the system freeze.

Thanks

---

