---
title: "I/O errors: is it an IDE controller problem or the hard disk is dying?"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by radiobuzzer on 2008-04-15
Hello, I would like an advice on a hardware issue, on an ACER laptop.

Recently, my laptop started giving I/O Errors regarding various blocks and sectors. The reaction of Ubuntu is to remount the system as read-only, which results in most of the programs being non-functional after a while. 

A sample of the errors is the following. Note that there are different group of errors, sometimes it's just unable to access a file, and then some other times gets a lost page write. Also, it coincides with driveseek errors to the CD rom (hdb) but it believe this might be irrelevant (?)

```
[ 2909.682379] ath0: no IPv6 routers present
[ 4611.453334] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.453342] ide: failed opcode was: unknown
[ 4611.453749] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.453752] ide: failed opcode was: unknown
[ 4611.454173] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.454176] ide: failed opcode was: unknown
[ 4611.454595] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.454598] ide: failed opcode was: unknown
[ 4611.455017] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.455020] ide: failed opcode was: unknown
[ 4611.455422] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.455425] ide: failed opcode was: unknown
[ 4611.455852] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.455855] ide: failed opcode was: unknown
[ 4611.456273] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.456276] ide: failed opcode was: unknown
[ 4611.456695] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.456699] ide: failed opcode was: unknown
[ 4611.457160] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.457164] ide: failed opcode was: unknown
[ 4611.457566] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.457569] ide: failed opcode was: unknown
[ 4611.457990] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.457993] ide: failed opcode was: unknown
[ 4611.458410] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 4611.458413] ide: failed opcode was: unknown
[ 4611.462198] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.462210] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644786625139, high=4210757, low=6912627, sector=90798707
[ 4611.462235] ide: failed opcode was: unknown
[ 4611.462242] end_request: I/O error, dev hda, sector 90798707
[ 4611.462331] EXT3-fs error (device hda5): ext3_find_entry: reading directory #489226 offset 0
[ 4611.527228] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.527239] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794213571, high=4210757, low=14501059, sector=94192835
[ 4611.527261] ide: failed opcode was: unknown
[ 4611.527268] end_request: I/O error, dev hda, sector 94192835
[ 4611.527380] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.527386] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644778529115, high=4210756, low=15593819, sector=82702683
[ 4611.527405] ide: failed opcode was: unknown
[ 4611.527408] end_request: I/O error, dev hda, sector 82702683
[ 4611.527412] Buffer I/O error on device hda5, logical block 0
[ 4611.527417] lost page write due to I/O error on hda5
[ 4611.528806] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.528816] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794213571, high=4210757, low=14501059, sector=94192835
[ 4611.528836] ide: failed opcode was: unknown
[ 4611.528841] end_request: I/O error, dev hda, sector 94192835
[ 4611.530223] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.530236] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794213571, high=4210757, low=14501059, sector=94192835
[ 4611.530261] ide: failed opcode was: unknown
[ 4611.530269] end_request: I/O error, dev hda, sector 94192835
[ 4611.532900] EXT3-fs error (device hda5): ext3_free_branches: Read failure, inode=700939, block=1436269
[ 4611.533061] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.533067] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644778529115, high=4210756, low=15593819, sector=82702683
[ 4611.533088] ide: failed opcode was: unknown
[ 4611.533092] end_request: I/O error, dev hda, sector 82702683
[ 4611.533098] Buffer I/O error on device hda5, logical block 0
[ 4611.533102] lost page write due to I/O error on hda5
[ 4611.538151] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.538161] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644786625139, high=4210757, low=6912627, sector=90798707
[ 4611.538182] ide: failed opcode was: unknown
[ 4611.538186] end_request: I/O error, dev hda, sector 90798707
[ 4611.538198] EXT3-fs error (device hda5): ext3_find_entry: reading directory #489226 offset 0
[ 4611.538294] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4611.538300] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644778529115, high=4210756, low=15593819, sector=82702683
[ 4611.538319] ide: failed opcode was: unknown
[ 4611.538322] end_request: I/O error, dev hda, sector 82702683
[ 4611.538326] Buffer I/O error on device hda5, logical block 0
[ 4611.538330] lost page write due to I/O error on hda5
[ 4612.366417] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.366427] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794712683, high=4210757, low=15000171, sector=94675499
[ 4612.366448] ide: failed opcode was: unknown
[ 4612.366453] end_request: I/O error, dev hda, sector 94675499
[ 4612.366459] Buffer I/O error on device hda5, logical block 1496602
[ 4612.366463] lost page write due to I/O error on hda5
[ 4612.366586] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.366591] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794712651, high=4210757, low=15000139, sector=94675531
[ 4612.366611] ide: failed opcode was: unknown
[ 4612.366615] end_request: I/O error, dev hda, sector 94675531
[ 4612.366618] Buffer I/O error on device hda5, logical block 1496606
[ 4612.366621] lost page write due to I/O error on hda5
[ 4612.366735] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.366740] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794712819, high=4210757, low=15000307, sector=94675635
[ 4612.366760] ide: failed opcode was: unknown
[ 4612.366763] end_request: I/O error, dev hda, sector 94675635
[ 4612.366766] Buffer I/O error on device hda5, logical block 1496619
[ 4612.366769] lost page write due to I/O error on hda5
[ 4612.366884] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.366890] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794713083, high=4210757, low=15000571, sector=94675899
[ 4612.366909] ide: failed opcode was: unknown
[ 4612.366913] end_request: I/O error, dev hda, sector 94675899
[ 4612.366916] Buffer I/O error on device hda5, logical block 1496652
[ 4612.366919] lost page write due to I/O error on hda5
[ 4612.367040] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.367045] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794713027, high=4210757, low=15000515, sector=94675907
[ 4612.367064] ide: failed opcode was: unknown
[ 4612.367067] end_request: I/O error, dev hda, sector 94675907
[ 4612.367070] Buffer I/O error on device hda5, logical block 1496653
[ 4612.367073] lost page write due to I/O error on hda5
[ 4612.367183] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.367189] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794713203, high=4210757, low=15000691, sector=94676019
[ 4612.367209] ide: failed opcode was: unknown
[ 4612.367212] end_request: I/O error, dev hda, sector 94676019
[ 4612.367215] Buffer I/O error on device hda5, logical block 1496667
[ 4612.367218] lost page write due to I/O error on hda5
[ 4612.367333] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4612.367338] hda: dma_intr: error=0x44 { DriveStatusError UncorrectableError }, LBAsect=70644794712659, high=4210757, low=15000147, sector=94675539
[ 4612.367358] ide: failed opcode was: unknown
[ 4612.367360] end_request: I/O error, dev hda, sector 94675539
[ 4612.367364] Buffer I/O error on device hda5, logical block 1496607
[ 4612.367367] lost page write due to I/O error on hda5
[ 4612.367375] Aborting journal on device hda5.
[ 4612.367397] __journal_remove_journal_head: freeing b_committed_data
[ 4612.371425] ext3_abort called.
[ 4612.371428] EXT3-fs error (device hda5): ext3_journal_start_sb: Detected aborted journal
[ 4612.371432] Remounting filesystem read-only
[ 5332.768730] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 5332.768738] ide: failed opcode was: unknown
[ 5332.769148] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 5332.769152] ide: failed opcode was: unknown
[ 5332.769573] hdb: status error: status=0x50 { DriveReady SeekComplete }
[ 5332.769576] ide: failed opcode was: unknown
```

[LIST]
[*]The interesting thing is that after rebooting, (after an fsck) the system will probably have a bad file allocation table, with wrongly timed inodes etc, but will NOT detect bad sectors or any sort of physical damage. 

[*]Then I download the SMARTctl tools, which are said to be able to detect hard disk errors. They didn't detect any sort of damage either.

[*]Very recently, the PC started having a problem while the BIOS is booting, too. In particular, it will give a "Fixed drive 0 error, opcode 002"; some of these times (but not always) the name of the hard disk appears wrongly (containing strange characters) among the BIOS auto-detected devices in the boot screen.

[*]It is not clear which are the circumstances when this problem happens. But I have noticed that the error may not show up if am stuck on my desk for some hours, but it will definitely happen if I move the PC around.
[/LIST]

Of course I would be happy if I can just go and buy a new hard drive, to solve the problem. But the errors above have made me suspicious whether this is a problem of the controller or the cable (which actually doesn't exist, because the hard disk seems to be directly plugged on the mainboard) and therefore I should keep my money for buying a new laptop, actually :-)

---

### Post by radiobuzzer on 2008-04-15
While I had been fully convinced that this is a hardware problem, it seems that a person in Sweden has been having EXACTLY the same problem, on exactly the same computer, and at the same period. This is too much to be a coincidence.

[http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=121&t=24959&p=201593#p201593](http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=121&t=24959&p=201593#p201593)

I am using ACER Aspire 5102 WLMI, AMD Turion 64x2 (1.6 Ghz), with a 100GB 5400rpm PATA HDD.
These information may also be useful:

```
 sudo hdparm -i /dev/hda

/dev/hda:

 Model=ST9100824A, FwRev=3.06, SerialNo=5PL1TX8B
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

```

---

### Post by mrsteveman1 on 2008-04-15
First, backup anything important.

Next, grab UBCD from here: [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

Now run HDAT2 which comes on the CD, its in hard disk tools > diagnostic tools.

It should both tell you if there are any smart errors in the drive log, let you run extended self tests on the drive, and then you absolutely want to run the "find and repair bad sectors" thing, which can't really be done from Linux.

When the kernel log starts giving you specific sector numbers repeatedly its probably the disk surface itself getting old or perhaps damaged.

How old is the drive in the laptop? Do you know?

---

### Post by radiobuzzer on 2008-04-16
> **mrsteveman1 said:**
> First, backup anything important.

Next, grab UBCD from here: [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

Now run HDAT2 which comes on the CD, its in hard disk tools > diagnostic tools.

It should both tell you if there are any smart errors in the drive log, let you run extended self tests on the drive, and then you absolutely want to run the "find and repair bad sectors" thing, which can't really be done from Linux.

When the kernel log starts giving you specific sector numbers repeatedly its probably the disk surface itself getting old or perhaps damaged.


Thanks, I will do so. So far I have run SMARTctl and finally got some error reports from them. I still need to understand what they mean for my hardware.

```
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST9100824A
Serial Number:    5PL1TX8B
Firmware Version: 3.06
User Capacity:    100.030.242.816 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Apr 16 11:44:42 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1734
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   074   060   030    Pre-fail  Always       -       25948718275
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       9493
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1213
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   001   001   000    Old_age   Always       -       322
190 Temperature_Celsius     0x0022   057   036   045    Old_age   Always   In_the_past 740950059
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       521
193 Load_Cycle_Count        0x0032   019   019   000    Old_age   Always       -       162752
194 Temperature_Celsius     0x0022   043   064   000    Old_age   Always       -       43 (Lifetime Min/Max 0/12)
195 Hardware_ECC_Recovered  0x001a   069   045   000    Old_age   Always       -       162484227
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   182   000    Old_age   Always       -       75
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 13 (device log contains only the most recent five errors)
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

Error 13 occurred at disk power-on lifetime: 9461 hours (394 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 5b f1 75 e0  Error: ICRC, ABRT at LBA = 0x0075f15b = 7729499

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 6b f1 f5 e0 00      05:36:55.829  READ DMA EXT
  25 00 08 eb a8 1a e0 00      05:36:55.824  READ DMA EXT
  25 00 08 d3 df 1a e0 00      05:36:55.981  READ DMA EXT
  25 00 08 3b f5 19 e0 00      05:36:55.969  READ DMA EXT
  25 00 10 93 b5 1a e0 00      05:36:55.963  READ DMA EXT

Error 12 occurred at disk power-on lifetime: 9391 hours (391 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 9b 93 1c e0 00      01:03:07.533  READ DMA EXT
  35 00 a8 93 99 39 e0 00      01:03:07.413  WRITE DMA EXT
  35 00 00 93 95 39 e0 00      01:03:07.404  WRITE DMA EXT
  35 00 00 93 91 39 e0 00      01:03:07.398  WRITE DMA EXT
  35 00 60 2b 91 39 e0 00      01:03:07.397  WRITE DMA EXT

Error 11 occurred at disk power-on lifetime: 9382 hours (390 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 10 00 00 e0 00      00:00:17.960  READ DMA EXT
  25 00 08 08 00 00 e0 00      00:00:17.960  READ DMA EXT
  25 00 08 00 00 00 e0 00      00:00:17.960  READ DMA EXT
  25 00 08 20 22 a5 e0 00      00:00:17.361  READ DMA EXT
  25 00 08 80 21 a5 e0 00      00:00:17.361  READ DMA EXT

Error 10 occurred at disk power-on lifetime: 9380 hours (390 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 93 71 f2 e0 00      00:19:47.298  READ DMA EXT
  65 40 48 d3 71 f2 e0 00      00:19:47.298  [RESERVED FOR SERIAL ATA]
  25 00 08 33 3a 30 e0 00      00:19:47.298  READ DMA EXT
  65 40 48 73 7a 70 e0 00      00:19:47.298  [RESERVED FOR SERIAL ATA]
  65 40 48 73 7a 70 e0 00      00:19:47.297  [RESERVED FOR SERIAL ATA]

Error 9 occurred at disk power-on lifetime: 9287 hours (386 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 10 d3 b7 1b e0 00      00:15:30.126  READ DMA EXT
  65 40 50 d3 f7 5b e0 00      00:15:30.126  [RESERVED FOR SERIAL ATA]
  25 00 08 4b 80 35 e0 00      00:15:30.125  READ DMA EXT
  25 00 08 13 80 35 e0 00      00:15:30.125  READ DMA EXT
  25 00 30 db 7f 35 e0 00      00:15:30.125  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      9488         -
# 2  Extended offline    Completed without error       00%      9265         -
# 3  Extended offline    Interrupted (host reset)      10%      9262         -
# 4  Short offline       Completed without error       00%      9262         -
# 5  Short offline       Completed without error       00%      9262         -

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

> **mrsteveman1 said:**
> How old is the drive in the laptop? Do you know?

The drive is one year + 8 months old. Not too old. The problem showed up 
(a) two months after me buying a new battery, 
(b) one month after buying a new power cord
(c) some weeks after started making intensive use of battery and the suspend mode. 
And since ACER suspend/power management has had very bad support, I have started being suspicious about it...

---

### Post by mrsteveman1 on 2008-04-16
If S.M.A.R.T actually has CRC  errors in the drives internal log its likely the disk surface itself, esp with all the references to specific sectors.

HDAT2 should tell you if the surface is OK.

Sometimes failed drives don't show anything in S.M.A.R.T, and sometimes errors show up in smart when the drive is fine, but in this case it looks like Linux itself found errors writing to specific sectors too.

I do notice the temperature on that drive has spiked fairly high in the past, i have a similar drive (might be the same one) that i had to replace because it ended up getting bad blocks too, right around the timeframe you gave.

---

### Post by radiobuzzer on 2008-04-18
HDAT2 gave no error on the surface. As I said I never had bad block or data loss. It's just that the disk occasionally gets inaccessibly for a while

---

### Post by mrsteveman1 on 2008-04-18
hm, so no bad blocks on the disk surface but Linux can't read specific sectors....

I'm stumped, maybe a ram problem?

---

### Post by velocity303 on 2008-04-28
Hey guys I am actually having the exact same problem with the exact same computer. I have an Acer 5102 and I have been getting the same hdd errors. I thought it was just the hard drive so I bought a replacement, but I am still having the same problem. It used to work perfectly, but now I even get hard drive problems in vista and other linux distros as well. Could it be the IDE controller on these laptops has issues? Because I surely hope I dont have two bad hard drives.

I'd love it if anyone knows how to fix this. I dont wanna have to buy a new laptop already, ive only had it for less than a year!!:(

Also as a sidenote, sometimes my hard drive and cd-rom doesnt show up in bios? Has anyone else experienced this?

---

### Post by radiobuzzer on 2008-05-15
Argh! I'm back. I thought the problem was on the hard-disk so I bought a new 2.5" disk to replace the other one. Guess what: it seemed to be working for a while, but problems started showing up as I kept using the pc intensively. 

So: my mind went back to the hypothesis that it is a problem of the mainboard. 

Actually on the new hard-disk I installed Ubuntu 8.04; so since I am getting slightly different errors, I cannot directly compare them with the ones I was getting in the old disk, with Ubuntu 7.10:  Now it is reported clearly in dmesg (or pressing CTRL+F1) than the CD drive or the Hard disk disappear for some time. In this case the operating system doesn't remount read-only, but tries again and again, until the disk is back. Of course in the meantime some programs may halt temporarily or even crash. This is definitely better than in Ubuntu 7.10, but still annoying.

Though, I have found a pretty ugly but effective solution: I got an external 2.5" disk case, which connects with a USB cable. Then I have configured grub to boot my old linux installation (on the first supposingly erroneous disk) from the USB disk case. Guess what! The system is perfectly booting and it doesn't crash at all. SO: I will leave this USB slot occupied, stick the external disk case on the back of my PC and keep working like that until I have the money to replace the motherboard or the entire laptop. Of course as these guys suggest ( [http://www.newertech.com/Static/articles/article_bruin_uda.html](http://www.newertech.com/Static/articles/article_bruin_uda.html) ) this may result to a lower transfer rate and a higher CPU initialization. But this is the best I could do!

velocity303 : If it is still the first year you got your laptop, why not use the warranty? They HAVE to replace the motherboard if this is the problem.

---

### Post by radiobuzzer on 2008-05-15
> **velocity303 said:**
> 
Also as a sidenote, sometimes my hard drive and cd-rom doesnt show up in bios? Has anyone else experienced this?

YES, I have experienced exactly the same thing

---

### Post by glenstewart on 2008-07-15
> **radiobuzzer said:**
> YES, I have experienced exactly the same thing

I also have the Acer Aspire 5102 with the IDE drive, and experienced the same problems. I also switched my (same) drive to USB, and it has been working fine since.

I haven't proven it yet, but suspect that bad stress relief in the laptop design has allowed flexing of the laptop case to get relayed to solder or wire connections and has created an intermittent connection.  I believe this because a). I can induce errors by flexing the laptop diagonally, and b).the problem gets worse as the laptop heats up from a cold start.

I plan to open it up and study the connections and solder joints near the IDE controller very closely.

---

