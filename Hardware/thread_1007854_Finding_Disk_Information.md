---
title: "Finding Disk Information"
date: 2008-12-10
forum: Hardware
---

### Post by twodayslate on 2008-12-10
Hey, doing a physics project on hard drives.

I will need to find out information about the hard drives to do this. 

I found the following: [http://www.cyberciti.biz/faq/linux-find-hard-drive-model-rpm-speed/](http://www.cyberciti.biz/faq/linux-find-hard-drive-model-rpm-speed/)
but it does not work. 
It can only find my media reader.
```
sudo sginfo -a /dev/sdd | more
INQUIRY response (cmd: 0x12)
----------------------------
Device Type                        0
Vendor:                    Generic 
Product:                   USB CF Reader   
Revision level:            1.01

No serial number (bad format for supported VPDs)

>>> Unable to read List supported pages mode page (0x3f) [mode_sense_10]
>>>>> device NOT READY, does it need media?

```

cat /proc/scsi/scsi found them though:
```
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 6Y120L0   Rev: YAR4
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: ST3200826A       Rev: 3.03
  Type:   Direct-Access                    ANSI  SCSI revision: 05
```

What other information besides the RPM will help with the physics aspect. I think I am going to do standard disk drives, flash drives and  maybe holographic? What do you think, any suggestions?
Thanks

peace.

---

### Post by koe1974 on 2008-12-11
sudo sginfo -a /dev/sdd | more

What other /dev/sd* devices are in your system?

try

mount | grep /dev/sd

mine shows:

/dev/sda1 on / type ext3 

then remove the "1"

sudo sginfo -a /dev/sda | more
sudo sginfo -a /dev/sdb | more
sudo sginfo -a /dev/sdc | more

good luck!

---

### Post by albinootje on 2008-12-11
You can also use hdparm with the -I parameter to get info about the drives.
For example : sudo hdparm -I /dev/sda
Or : sudo hdparm -I /dev/hda
(Install hdparm with : sudo apt-get install hdparm)

---

### Post by twodayslate on 2008-12-11
```
mount | grep /dev/sd
/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb2 on /boot type ext3 (rw,relatime)
/dev/sdb4 on /home type ext3 (rw,relatime)



mount | grep /dev/sd
/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb2 on /boot type ext3 (rw,relatime)
/dev/sdb4 on /home type ext3 (rw,relatime)


sudo sginfo -a /dev/sda | more
INQUIRY response (cmd: 0x12)
----------------------------
Device Type                        0
Vendor:                    ATA     
Product:                   Maxtor 6Y120L0  
Revision level:            YAR4

Serial Number 'Y416QCKE            '

Read-Write Error Recovery mode page (0x1)
-----------------------------------------
AWRE                               1
ARRE                               0
TB                                 0
RC                                 0
EER                                0
PER                                0
DTE                                0
DCR                                0
Read Retry Count                   0
Correction Span                    0
Head Offset Count                  0
Data Strobe Offset Count           0
Write Retry Count                  0
Recovery Time Limit (ms)           0

Caching mode page (0x8)
-----------------------
Initiator Control                  0
ABPF                               0
CAP                                0
DISC                               0
SIZE                               0
Write Cache Enabled                1
MF                                 0
Read Cache Disabled                0
Demand Read Retention Priority     0
Demand Write Retention Priority    0
Disable Pre-fetch Transfer Length  0
Minimum Pre-fetch                  0
Maximum Pre-fetch                  0
Maximum Pre-fetch Ceiling          0
FSW                                0
LBCSS                              0
DRA                                0
NV_DIS                             0
Number of Cache Segments           0
Cache Segment size                 0
Non-Cache Segment size             0

Control mode page (0xa)
-----------------------
TST                                0
TMF_ONLY                           0
D_SENSE                            0
GLTSD                              1
RLEC                               0
Queue Algorithm Modifier           0
QErr                               0
DQue [obsolete]                    0
TAS                                0
RAC                                0
UA_INTLCK_CTRL                     0
SWP                                0
RAERP [obs.]                       0
UAAERP [obs.]                      0
EAERP [obs.]                       0
ATO                                0
TAS                                0
AUTOLOAD MODE                      0
Ready AER Holdoff Period [obs.]    0
Busy Timeout Period                65535
Extended self-test completion time 30



sudo sginfo -a /dev/sdb | more
INQUIRY response (cmd: 0x12)
----------------------------
Device Type                        0
Vendor:                    ATA     
Product:                   ST3200826A      
Revision level:            3.03

Serial Number '            3ND0R54S'

Read-Write Error Recovery mode page (0x1)
-----------------------------------------
AWRE                               1
ARRE                               0
TB                                 0
RC                                 0
EER                                0
PER                                0
DTE                                0
DCR                                0
Read Retry Count                   0
Correction Span                    0
Head Offset Count                  0
Data Strobe Offset Count           0
Write Retry Count                  0
Recovery Time Limit (ms)           0

Caching mode page (0x8)
-----------------------
Initiator Control                  0
ABPF                               0
CAP                                0
DISC                               0
SIZE                               0
Write Cache Enabled                1
MF                                 0
Read Cache Disabled                0
Demand Read Retention Priority     0
Demand Write Retention Priority    0
Disable Pre-fetch Transfer Length  0
Minimum Pre-fetch                  0
Maximum Pre-fetch                  0
Maximum Pre-fetch Ceiling          0
FSW                                0
LBCSS                              0
DRA                                0
NV_DIS                             0
Number of Cache Segments           0
Cache Segment size                 0
Non-Cache Segment size             0

Control mode page (0xa)
-----------------------
TST                                0
TMF_ONLY                           0
D_SENSE                            0
GLTSD                              1
RLEC                               0
Queue Algorithm Modifier           0
QErr                               0
DQue [obsolete]                    0
TAS                                0
RAC                                0
UA_INTLCK_CTRL                     0
SWP                                0
RAERP [obs.]                       0
UAAERP [obs.]                      0
EAERP [obs.]                       0
ATO                                0
TAS                                0
AUTOLOAD MODE                      0
Ready AER Holdoff Period [obs.]    0
Busy Timeout Period                65535
Extended self-test completion time 30

```

Why is everything 0? I get no useful info from that!

edit://
```
sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       Maxtor 6Y120L0                          
	Serial Number:      Y416QCKE            
	Firmware Revision:  YAR41VW0
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  240121728
	device size with M = 1024*1024:      117246 MBytes
	device size with M = 1000*1000:      122942 MBytes (122 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	Recommended acoustic management value: 192, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by CSEL
Checksum: correct




sudo hdparm -I /dev/sdb
 
/dev/sdb:

ATA device, with non-removable media
	Model Number:       ST3200826A                              
	Serial Number:      3ND0R54S
	Firmware Revision:  3.03    
Standards:
	Supported: 7 6 5 4 
	Likely used: 7
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  390721968
	device size with M = 1024*1024:      190782 MBytes
	device size with M = 1000*1000:      200049 MBytes (200 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 1 determined by CSEL
Checksum: correct


```

---

### Post by twodayslate on 2008-12-15
up

---

### Post by cariboo on 2008-12-15
Have a look at smartmontools, it is in the repositories. Smartctl will give you more info that you may need. In a terminal type:

```
sudo smartctl -a /dev/sda
```

Will give you an output that looks something like this:

```
sudo smartctl -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 9 family
Device Model:     Maxtor 6Y120L0
Serial Number:    Y3PH406E
Firmware Version: YAR41BW0
User Capacity:    122,942,324,736 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Mon Dec 15 19:56:52 2008 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

-----------------cut-----------------
```

There is a lot more output, but it isn't needed here.

Jim

---

### Post by twodayslate on 2008-12-16
> **cariboo907 said:**
> 
```
sudo smartctl -a /dev/sda
```

Will give you an output that looks something like this:

There is a lot more output, but it isn't needed here.

JimI need the rpm
Since this is the physics lab the serial number isn't important. I need speeds and times. 
Thanks!
```
sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 9 family
Device Model:     Maxtor 6Y120L0
Serial Number:    Y416QCKE
Firmware Version: YAR41VW0
User Capacity:    122,942,324,736 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue Dec 16 12:04:46 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 242) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  63) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   203   201   063    Pre-fail  Always       -       19580
  4 Start_Stop_Count        0x0032   252   252   000    Old_age   Always       -       1995
  5 Reallocated_Sector_Ct   0x0033   001   001   063    Pre-fail  Always   FAILING_NOW 2555
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   253   241   187    Pre-fail  Always       -       52617
  9 Power_On_Minutes        0x0032   219   219   000    Old_age   Always       -       1081h+41m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   248   248   000    Old_age   Always       -       1999
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       36
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       4039
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   001   001   000    Old_age   Offline      -       2547
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   158   084   000    Old_age   Offline      -       113
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   238   000    Old_age   Always       -       98
202 TA_Increase_Count       0x000a   253   196   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   251   180    Pre-fail  Always       -       36
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   197   194   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 28586 inconsistent with error log pointer 5

ATA Error Count: 28586 (device log contains only the most recent five errors)
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

Error 28586 occurred at disk power-on lifetime: 9196 hours (383 days + 4 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 5f fe 5b f9  Error: UNC 3 sectors at LBA = 0x095bfe5f = 157023839

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 5f fe 5b f9 00   1d+04:27:17.424  READ DMA
  ca 00 10 5f 5a 2a fa 00   1d+04:27:17.424  WRITE DMA
  c8 00 10 27 88 3e f6 00   1d+04:27:17.424  READ DMA
  ca 00 80 df 59 2a fa 00   1d+04:27:17.424  WRITE DMA
  c8 00 80 a7 87 3e f6 00   1d+04:27:17.408  READ DMA

Error 28585 occurred at disk power-on lifetime: 9163 hours (381 days + 19 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 5f fe 5b f9  Error: UNC 3 sectors at LBA = 0x095bfe5f = 157023839

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 5f fe 5b f9 00      00:58:02.976  READ DMA
  c8 00 08 0f e0 27 f7 00      00:58:02.912  READ DMA
  c8 00 08 f7 3d 05 f0 00      00:58:02.912  READ DMA
  c8 00 08 ef 3d 05 f0 00      00:58:02.912  READ DMA
  c8 00 08 e7 3d 05 f0 00      00:58:02.912  READ DMA

Error 28584 occurred at disk power-on lifetime: 9163 hours (381 days + 19 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 5f fe 5b f9  Error: UNC 3 sectors at LBA = 0x095bfe5f = 157023839

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 5f fe 5b f9 00      00:57:36.192  READ DMA
  ca 00 68 1f a5 20 fa 00      00:57:36.144  WRITE DMA
  c8 00 68 e7 61 53 f0 00      00:57:36.144  READ DMA
  ca 00 70 af a4 20 fa 00      00:57:36.144  WRITE DMA
  c8 00 70 77 61 53 f0 00      00:57:36.144  READ DMA

Error 28583 occurred at disk power-on lifetime: 9108 hours (379 days + 12 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 5f fe 5b f9  Error: UNC 3 sectors at LBA = 0x095bfe5f = 157023839

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 5f fe 5b f9 00      03:39:56.288  READ DMA
  ca 00 68 e7 61 53 f0 00      03:39:56.288  WRITE DMA
  c8 00 68 17 57 09 fa 00      03:39:56.272  READ DMA
  ca 00 70 77 61 53 f0 00      03:39:56.272  WRITE DMA
  c8 00 70 a7 56 09 fa 00      03:39:56.272  READ DMA

Error 28582 occurred at disk power-on lifetime: 9073 hours (378 days + 1 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 5f fe 5b f9  Error: UNC 3 sectors at LBA = 0x095bfe5f = 157023839

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 5f fe 5b f9 00      01:29:13.040  READ DMA
  c8 00 38 5f d1 87 f8 00      01:29:13.024  READ DMA
  ca 00 70 d7 0a 0f fa 00      01:29:13.024  WRITE DMA
  c8 00 38 5f d1 87 f8 00      01:29:13.024  READ DMA
  c8 00 70 77 8f 12 f2 00      01:29:13.008  READ DMA

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

### Post by twodayslate on 2008-12-23
Am I missing something?

---

### Post by twodayslate on 2008-12-25
bump

---

### Post by twodayslate on 2008-12-27
shiznits

---

### Post by twodayslate on 2009-01-01
nothing?

---

### Post by twodayslate on 2009-01-04
alright, how about a stress test? 
Does Hardware Testing do a good job of giving info?

---

### Post by twodayslate on 2009-01-06
:( 
No help?

---

### Post by twodayslate on 2009-01-11
You guys are making me sad :(
Was the answer posted already and I just misssed the obvious?

---

### Post by twodayslate on 2009-01-13
another...

---

### Post by twodayslate on 2009-01-15
I tried the hardware testing app and it wasn't what I thought it was.

Any help?

---

### Post by twodayslate on 2009-01-23
Need temp. read speed, write speed

---

### Post by twodayslate on 2009-01-24
is there seperate commands for each at least?

---

### Post by twodayslate on 2009-01-26
did I bump a whole page yet?

---

### Post by twodayslate on 2009-02-03
Bump

---

