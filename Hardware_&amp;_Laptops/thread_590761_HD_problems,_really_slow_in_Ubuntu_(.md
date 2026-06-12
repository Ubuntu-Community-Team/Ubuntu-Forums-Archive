---
title: "HD problems, really slow in Ubuntu :("
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by DARKGuy on 2007-10-25
Hey guys :)

Since Feisty I've been having some problems with my hard disk, overall when I'm doing "heavy" stuff on it... I say "heavy" because the time it takes to do anything else is ridiculously SLOW compared to Windows (which I've installed on the same HD before). I upgraded to Gutsy in hopes that HD access was faster but it was a no-go...

For example, I login on my system and have to wait about 5-15 seconds until my full desktop appears  (it doesn't matter if I have compiz enabled or not). That's ok. I have some panel buttons with Swiftweasel, Swiftdove, Mercury Messenger and Rythmbox. I click them all one by one... and then the HD slowness begins, until after **2-5 minutes** that's when my system is responsive again with all my apps loaded. It's **ridiculous!!** - I've been able to start up WMP, Firefox, Dev-C++, Diablo II and Thunderbird in Windows in less time :/ and while all those apps are running, my system is still responsive to load other stuff, such as MSN Live Messenger.

I really want to have Ubuntu as my main OS but this is driving me crazy... I can't believe this >.<...

My system specs are the following ones:

3.2Ghz Pentium 4 EM64T/HT Processor.
512Mb DDR2 533Mhz Corsair (or Markvision, can't remember).
Biostar P4M800-Pro motherboard.
GeForce4 Ti 4200 AGP8X 128Mb.
Ubuntu Gutsy 64-bit.

**My HD config is as follow:**

**Primary master: **Seagate 40Gb IDE (Ubuntu).
**Primary slave:** Maxtor 40Gb IDE (Windows).
**Secondary Master:** Samsung CDRW/DVDRW combo 52x.

I have DMA enabled on the disk as hdparm shows:
```
~$ sudo hdparm /dev/hdd
/dev/hdd:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 16383/255/63, sectors = 78156288, start = 0
```
My fstab is this one:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=3e96f8c3-b18b-45e2-b5d9-4893ebd5f50e /               ext3    defaults,noatime,errors=remount-ro 0       1
# /dev/hdd5
UUID=448efe2b-b09d-4ab6-a089-d2a9e7d83fbc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```
/dev/hdd1 being my Ubuntu HD.

By following this guide suggested to me by an IRC channel user -> [http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips](http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips) I managed to set my ext3 journaling mode to the "journal" data mode, tho I didn't change its size. I also enabled directory indexing. In the fstab, I added "noatime" as a suggestion by one of the forum users when I did a google & forum search a few days ago about my problem.

I've been thinking in using LILO instead so I can partition my HD with xfs which is said is 10x faster than ext3, but that can also cause loss of data - as much as an ext3 without journaling will? what could happen if I disable journaling and somehow shut down my PC by pressing the case's button? will I lose data I already have, or the last written/accessed/read data before the shutdown?.

Also, are there any suggestions to improve my HD/overall OS speed? Ubuntu can't be this slow... can it? :/... also, I have no plans to buy new harddrives soon (nor I'm willing to spend money) so getting a SATA/SATAII drive/memory/processor/etc. isn't an option.

Any help is greatly appreciated!!! :D

---

### Post by tommcd on 2007-10-25
It seems there was a bug in fiesty about hdparm on IDE drives:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636) 
 I have read that recent kernels do not perform well on some IDE drives. An 80GB sata drive would replace your 2 drives without costing much money at all, as long as your motherboard has sata ports.
Only other thing I could suggest would be to make sure the jumpers on your drives are set to master and slave. Do not use cable select.

---

### Post by PointyWombat on 2007-10-25
With only 512MB of memory, i would check that you're not swaping. In a terminal, run:

# sar -r 1 100

and see if you have values in the "kbswpused" and "%swpused" columns which generally indicate a memory shortage.

---

### Post by DARKGuy on 2007-10-25
> **tommcd said:**
> It seems there was a bug in fiesty about hdparm on IDE drives:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636) 
 I have read that recent kernels do not perform well on some IDE drives. An 80GB sata drive would replace your 2 drives without costing much money at all, as long as your motherboard has sata ports.
Only other thing I could suggest would be to make sure the jumpers on your drives are set to master and slave. Do not use cable select.

Hm o.O... figured as much, that's why I upgraded to Gutsy as I said in my first post (fresh install, too) but I haven't noticed much difference at all. Yes I know SATA could be better than my two IDE drives, but I don't have the enough money to get one right now (I'm Venezuelan and the dollar exchange is REAL high here :/, thus making imported stuff expensive) though I have in mind to get one someday, maybe a 160Gb one, gotta check.

What puzzles me is that HD work becomes more intensive and makes my system more unresponsive (to the point that it freezes totally) that in Windows :/. Only way I could reproduce that would be to try to run two WoWs, WinAmp and then try to open anything else - and yet that's faster! :confused:

I know about the jumpers thing, they're on their right setting according to their role, in fact I don't use cable select unless I have problems with IDEs and HDD detection on some machines, but as general rule I always put the jumpers where they should be ^_^.

> **PointyWombat said:**
> With only 512MB of memory, i would check that you're not swaping. In a terminal, run:

# sar -r 1 100

and see if you have values in the "kbswpused" and "%swpused" columns which generally indicate a memory shortage.
Alright, I'll try that when I'm back home since I'm at work right now :)

---

### Post by DARKGuy on 2007-10-26
Alright, I tried the command and I got some commands from the forum to get more HD info, I hope it's useful!

```
:~$ sudo hdparm -i /dev/hdd

/dev/hdd:

 Model=ST340014A, FwRev=3.10, SerialNo=5JXB94PW
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78156288
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode
```

```
~$ sudo smartctl -a /dev/hdd
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST340014A
Serial Number:    5JXB94PW
Firmware Version: 3.10
User Capacity:    40,016,019,456 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Fri Oct 26 14:15:08 2007 VET
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
data collection:                 ( 430) seconds.
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
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   058   051   006    Pre-fail  Always       -       90406847
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       56
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   085   060   030    Pre-fail  Always       -       377860411
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       8911
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1620
194 Temperature_Celsius     0x0022   037   048   000    Old_age   Always       -       37
195 Hardware_ECC_Recovered  0x001a   058   051   000    Old_age   Always       -       90406847
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   123   000    Old_age   Always       -       1229
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 817 (device log contains only the most recent five errors)
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

Error 817 occurred at disk power-on lifetime: 7093 hours (295 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 07 00 00 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000007 = 7

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  10 00 3f 00 00 00 e0 00      06:53:32.746  RECALIBRATE [OBS-4]
  25 00 08 00 00 00 e0 00      06:53:32.745  READ DMA EXT
  25 00 08 00 00 00 e0 00      06:53:32.745  READ DMA EXT

Error 816 occurred at disk power-on lifetime: 7093 hours (295 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 07 00 00 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000007 = 7

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  10 00 3f 00 00 00 e0 00      06:53:32.746  RECALIBRATE [OBS-4]
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  25 00 08 00 00 00 e0 00      06:53:32.745  READ DMA EXT
  ef 02 00 00 00 00 e0 00      06:53:32.745  SET FEATURES [Enable write cache]

Error 815 occurred at disk power-on lifetime: 7093 hours (295 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 07 00 00 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000007 = 7

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  ef 02 00 00 00 00 e0 00      06:53:32.746  SET FEATURES [Enable write cache]
  27 00 00 00 00 00 e0 00      06:53:32.745  READ NATIVE MAX ADDRESS EXT
  ec 00 01 00 00 00 a0 00      06:53:32.745  IDENTIFY DEVICE

Error 814 occurred at disk power-on lifetime: 7093 hours (295 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 07 00 00 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000007 = 7

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 00 00 00 e0 00      06:53:32.746  READ DMA EXT
  ef 02 00 00 00 00 e0 00      06:53:32.746  SET FEATURES [Enable write cache]
  27 00 00 00 00 00 e0 00      06:53:32.746  READ NATIVE MAX ADDRESS EXT
  ec 00 01 00 00 00 a0 00      06:53:32.745  IDENTIFY DEVICE
  c6 00 00 00 00 00 a0 00      06:53:32.745  SET MULTIPLE MODE

Error 813 occurred at disk power-on lifetime: 7092 hours (295 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 47 49 54 e0  Error: ICRC, ABRT at LBA = 0x00544947 = 5523783

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 47 49 54 e0 00      06:05:22.429  READ DMA EXT
  25 00 00 47 49 54 e0 00      06:05:21.807  READ DMA EXT
  10 00 3f 00 00 00 e0 00      06:05:21.807  RECALIBRATE [OBS-4]
  25 00 00 47 49 54 e0 00      06:05:21.212  READ DMA EXT
  25 00 00 47 49 54 e0 00      06:05:20.607  READ DMA EXT

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

Here's the output of **sar -r 1 100** with only a gnome session, swiftweasel and xfce4-terminal opened:
```
~$ sar -r 1 100
Linux 2.6.22-14-generic (cave)  26/10/07

14:18:42    kbmemfree kbmemused  %memused kbbuffers  kbcached kbswpfree kbswpused  %swpused  kbswpcad
14:18:43        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:44        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:45        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:46        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:47        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:48        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:49        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:50        37204    475052     92,74      3928    122976   1463596     38440      2,56         0
14:18:51        37212    475044     92,74      3928    122976   1463596     38440      2,56         0
14:18:52        37212    475044     92,74      3932    122972   1463596     38440      2,56         0
14:18:53        37212    475044     92,74      3960    123040   1463596     38440      2,56         0
14:18:54        37212    475044     92,74      3960    123040   1463596     38440      2,56         0
14:18:55        37212    475044     92,74      3960    123040   1463596     38440      2,56         0
14:18:56        37212    475044     92,74      3960    123040   1463596     38440      2,56         0
14:18:57        37212    475044     92,74      3960    123040   1463596     38440      2,56         0
14:18:58        37212    475044     92,74      3968    123040   1463596     38440      2,56         0
14:18:59        37212    475044     92,74      3968    123040   1463596     38440      2,56         0
14:19:00        37212    475044     92,74      3968    123040   1463596     38440      2,56         0
```

Nothing changes on those two columns, so I decided to start X-Chat, Swiftdove, Rythmbox and Pidgin at the same time:

```
~$ sar -r 1 100
Linux 2.6.22-14-generic (cave)  26/10/07

14:19:49    kbmemfree kbmemused  %memused kbbuffers  kbcached kbswpfree kbswpused  %swpused  kbswpcad
14:19:50        32624    479632     93,63      4000    123080   1463596     38440      2,56         0
14:19:51        32624    479632     93,63      4000    123080   1463596     38440      2,56         0
14:19:52        27580    484676     94,62      4196    125392   1463596     38440      2,56         0
14:19:53        21616    490640     95,78      4436    129020   1463596     38440      2,56         0
14:19:54         9480    502776     98,15      4552    137444   1463596     38440      2,56         0
14:19:55         5092    507164     99,01      4440    139112   1463564     38472      2,56        32
14:19:56         4816    507440     99,06      4256    135032   1463564     38472      2,56        32
14:19:57         5004    507252     99,02      3352    133148   1463564     38472      2,56        32
14:19:58         5744    506512     98,88      2992    129852   1463564     38472      2,56        32
14:19:59         5864    506392     98,86      2920    126732   1463564     38472      2,56         0
14:20:00         4864    507392     99,05      2644    123916   1463560     38476      2,56         4
14:20:01         4948    507308     99,03      2624    120472   1463560     38476      2,56         4
14:20:02         4948    507308     99,03      2492    117284   1463560     38476      2,56         4
14:20:03         5356    506900     98,95      2260    112920   1463560     38476      2,56         0
14:20:04         5016    507240     99,02      1616    110784   1463432     38604      2,57       128
14:20:05         5224    507032     98,98      1836    107068   1463196     38840      2,59       236
14:20:06         5944    506312     98,84      1844     99752   1463188     38848      2,59         8
14:20:07         5292    506964     98,97      1832     95088   1463060     38976      2,59       136
14:20:08         5160    507096     98,99      1840     92760   1462932     39104      2,60         8
14:20:09         5224    507032     98,98      1512     91068   1462480     39556      2,63       192
14:20:10         4916    507340     99,04      1568     88864   1460376     41660      2,77      1656
14:20:11         5568    506688     98,91      1788     88704   1460332     41704      2,78       248
14:20:12         6116    506140     98,81      1852     87408   1459316     42720      2,84       732
14:20:13         6396    505860     98,75      1856     87408   1457788     44248      2,95       416
14:20:14         6148    506108     98,80      1780     86980   1457692     44344      2,95       460
14:20:15         6552    505704     98,72      1808     85604   1457004     45032      3,00       668
14:20:16         7212    505044     98,59      1792     84920   1456572     45464      3,03      1016
14:20:17         7168    505088     98,60      1828     85048   1456572     45464      3,03      1016
14:20:18         6296    505960     98,77      1856     85184   1456572     45464      3,03      1016
14:20:19         5812    506444     98,87      2032     85584   1455140     46896      3,12       552
14:20:20         6024    506232     98,82      2116     86280   1452556     49480      3,29       884
14:20:21         5916    506340     98,85      2216     88108   1449580     52456      3,49       772
14:20:22         6496    505760     98,73      2356     89016   1446616     55420      3,69      1792
14:20:23         6348    505908     98,76      2376     89124   1446616     55420      3,69      1792
14:20:24         6356    505900     98,76      2376     89124   1446616     55420      3,69      1792
14:20:25         6680    505576     98,70      2420     89748   1444708     57328      3,82      1212
14:20:26         6312    505944     98,77      2420     89748   1444708     57328      3,82      1212
14:20:27         6320    505936     98,77      2420     89748   1444708     57328      3,82      1212
14:20:28         6312    505944     98,77      2420     89748   1444708     57328      3,82      1212
14:20:29         6312    505944     98,77      2420     89748   1444708     57328      3,82      1212
14:20:30         6312    505944     98,77      2420     89764   1444708     57328      3,82      1212
14:20:31         6312    505944     98,77      2428     89764   1444708     57328      3,82      1212
14:20:32         6296    505960     98,77      2428     89828   1444708     57328      3,82      1212
14:20:33         6296    505960     98,77      2428     89832   1444708     57328      3,82      1212
14:20:34         6296    505960     98,77      2432     89832   1444708     57328      3,82      1212
14:20:35         6288    505968     98,77      2432     89848   1444708     57328      3,82      1212
14:20:36         6304    505952     98,77      2440     89848   1444708     57328      3,82      1212
14:20:37         6304    505952     98,77      2440     89892   1444708     57328      3,82      1212
14:20:38         6304    505952     98,77      2440     89896   1444708     57328      3,82      1212
14:20:39         6304    505952     98,77      2440     89892   1444712     57324      3,82      1208
```

This is my HD free space info... useful?
```
~$ df
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/hdd1             36985736  21056284  14050652  60% /
varrun                  256128       196    255932   1% /var/run
varlock                 256128         0    256128   0% /var/lock
udev                    256128        88    256040   1% /dev
devshm                  256128         0    256128   0% /dev/shm
lrm                     256128     38324    217804  15% /lib/modules/2.6.22-14-generic/volatile

~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/hdd1              36G   21G   14G  60% /
varrun                251M  196K  250M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   88K  251M   1% /dev
devshm                251M     0  251M   0% /dev/shm
lrm                   251M   38M  213M  15% /lib/modules/2.6.22-14-generic/volatile
```

Please keep replying! I really need my OS to be more responsive :/

---

### Post by DARKGuy on 2007-10-26
Sorry for bumping but... anyone?

---

### Post by tommcd on 2007-10-26
I would try to reinstall with XFS then if nothing else helps.

---

### Post by tommcd on 2007-10-27
Also, you might try working you way through this:
[http://www.gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://www.gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)
It's everything you would ever want to know about hdparm.

---

### Post by DARKGuy on 2007-10-28
Yeah, I've read that guide before back when I used Edgy, but hdparm does not do any much difference now.

I managed to solve my problem though - I reinstalled using XFS for / (root), 100Mb or so for /boot in ext3 (so it didn't complain about having to use LILO and not advancing to the next install step) and 1532Mb for swap.

Problem solved, now I can multitask happily, menus open faster, and I can have VirtualBox running happily in seamless mode without slowing my entire system down, I can open 10-20 apps at the same time and the delay is reduced from dozens of minutes to just seconds or 1-2 minutes maximum. XFS -is- the real Ubuntu speed :).

I'm happy :D - but ext3 should really be optimized...

---

### Post by tommcd on 2007-10-28
> **DARKGuy said:**
> Yeah, I've read that guide before back when I used Edgy, but hdparm does not do any much difference now.

I managed to solve my problem though - I reinstalled using XFS for / (root), 100Mb or so for /boot in ext3 (so it didn't complain about having to use LILO and not advancing to the next install step) .

Glad you got it fixed. So I guess you can still boot with grub since you made a 100mb /boot partition in ext3, is that correct?
Perhaps I'll try XFS the next time I install ubuntu or zenwalk. I've been using ext3 because I was concerned about data corruption also, plus that is what I am used to doing. Lots of people on the zenwalk forums use xfs (it is the default file system chosen on a zenwalk install) and they say it is reliable and fast.

---

