---
title: "SATA drive with errors"
date: 2013-06-18
forum: Hardware
---

### Post by sturkel on 2013-06-18
I'm using a seagate ST32000542AS drive connected to the ICH7 controller of my d945gclf2 motherboard.
When accessing the disk i'm getting errors and the drive speed is way to slow.
I tried to disable NCQ, but that seems not to solve the problem.
the drive is formatted as ext 4 and mounted from fstab
```
/dev/sdb1 /sg ext4 rw,noatime   0       0
```
dmesg error:
```
[ 1915.354201] ata4.00: cmd 25/00:88:b7:a7:34/00:00:92:00:00/e0 tag 0 dma 69632 in
[ 1915.354204]          res 51/84:58:e7:a7:34/84:00:92:00:00/e0 Emask 0x30 (host bus error)
[ 1915.354220] ata4.00: status: { DRDY ERR }
[ 1915.354226] ata4.00: error: { ICRC ABRT }
[ 1915.354245] ata4: soft resetting link
[ 1915.532406] ata4.00: configured for UDMA/33
[ 1915.532437] ata4: EH complete
[ 1915.728042] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 1915.728052] ata4.00: BMDMA stat 0x26
[ 1915.728061] ata4.00: failed command: READ DMA EXT
[ 1915.728077] ata4.00: cmd 25/00:00:b7:e8:34/00:02:92:00:00/e0 tag 0 dma 262144 in

```
lcpci
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
```
hdparm -tT /dev/sdb
```

/dev/sdb:
 Timing cached reads:   1080 MB in  2.00 seconds = 539.48 MB/sec
 Timing buffered disk reads:  34 MB in  3.11 seconds =  10.94 MB/sec
```

What can I do to get normal speeds (w/o errors) and the drive in udma 5,6 or7 mode.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by sturkel on 2013-06-18
> **ahallubuntu said:**
> Check the drive's S.M.A.R.T. status and make sure it's not actually failing.  Install GSmartControl in Ubuntu and check the Attributes tab to see if any Attributes are highlighted in pink or red.  If not, the drive itself is probably not failing.
I already tested it with smartclt but all things seems fine, no errors reported.

---

### Post by Cheesemill on 2013-06-18
Check the SATA cable, as a dodgy one can lead to this sort of problem.

---

### Post by Yellow Pasque on 2013-06-18
^In addition to trying a different cable (and different SATA port), I would look at SATA settings in the BIOS. In my experience, some SATA controllers work better by changing that setting (AHCI, IDE, SATA, etc.), especially with multiple SATA devices.

---

### Post by sturkel on 2013-06-18
> **Temüjin said:**
> ^In addition to trying a different cable (and different SATA port), I would look at SATA settings in the BIOS. In my experience, some SATA controllers work better by changing that setting (AHCI, IDE, SATA, etc.), especially with multiple SATA devices.
I tried a different cable w/o succes.
Bios setting are: ATA/IDE : native,
tried with setting 'use sata' without any effort.
now trying to backup and format, mabye it's a corrupt filesystem, or is that not possible?

---

### Post by user_of_gnomes on 2013-06-18
Do you have 32-bit transfer enabled for that hard drive? Not sure if they still have the option of doing 16-bit transfers in modern BIOS but if they do and it's set to that, 32-bit should offer a bit of an improvement in performance.

---

### Post by sturkel on 2013-06-18
> **UbuntuRaptor said:**
> Do you have 32-bit transfer enabled for that hard drive? Not sure if they still have the option of doing 16-bit transfers in modern BIOS but if they do and it's set to that, 32-bit should offer a bit of an improvement in performance.

I don't have an option for 16 bit, so I guess it will be 32 by default (it's an 32 bits os/cpu)
currently copying files, but at a very slow transfer rate, it seems that the drive can't be accessed continuously
```
Jun 18 20:01:16 tweety kernel: [ 2122.952386] ata4.00: configured for UDMA/33
Jun 18 20:01:16 tweety kernel: [ 2122.952417] ata4: EH complete
Jun 18 20:01:17 tweety kernel: [ 2122.985546] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jun 18 20:01:17 tweety kernel: [ 2122.985561] ata4.00: BMDMA stat 0x26
Jun 18 20:01:17 tweety kernel: [ 2122.985574] ata4.00: failed command: READ DMA
Jun 18 20:01:17 tweety kernel: [ 2122.985597] ata4.00: cmd c8/00:00:bf:93:da/00:00:00:00:00/e0 tag 0 dma 131072 in
Jun 18 20:01:17 tweety kernel: [ 2122.985602]          res 51/84:80:3f:94:da/84:01:00:00:00/e0 Emask 0x30 (host bus error)
Jun 18 20:01:17 tweety kernel: [ 2122.985615] ata4.00: status: { DRDY ERR }
Jun 18 20:01:17 tweety kernel: [ 2122.985624] ata4.00: error: { ICRC ABRT }
Jun 18 20:01:17 tweety kernel: [ 2122.985648] ata4: soft resetting link

```
after the soft reset link it holds up for some seconds

---

### Post by user_of_gnomes on 2013-06-18
> I don't have an option for 16 bit, so I guess it will be 32 by default (it's an 32 bits os/cpu)


That's unrelated. 

> configured for UDMA/33


Why UDMA/33? 

Maybe you should set the BIOS back to its default settings and then try again if you haven't already?
Can you link me to the manual for your mainboard?

---

### Post by sturkel on 2013-06-19
> **UbuntuRaptor said:**
> That's unrelated. 

Why UDMA/33? 
Maybe you should set the BIOS back to its default settings and then try again if you haven't already?
Can you link me to the manual for your mainboard?
I think it's the lowest fallback that the drive/controller supports.
In the bios there are no options to set, see this link:
[http://downloadmirror.intel.com/16960/eng/D945GCLF2_TechProdSpec02.pdf]("http://downloadmirror.intel.com/16960/eng/D945GCLF2_TechProdSpec02.pdf")
Copied yesterday 16G of pictures to my external hd wich took more then 3 hours.
I heard the head of the hd spinning and slow down every x seconds which was related to the error log (syslog)

---

### Post by user_of_gnomes on 2013-06-19
There seems to be a firmware update out for the  ST32000542AS hard drive. Did you look into that to see if your issue is described in the fix list? 

> A lot of ST32000542AS drives come with the CC34 firmware. Apparently it has various known problems, one of which is an annoying click (click of death). The first thing you&#8217;ll want to do is upgrade the firmware to CC35. A Link to the instructions is in the references section below.

[http://tech.kulish.com/2011/03/05/seagate-st32000542as-2tb-setup/](http://tech.kulish.com/2011/03/05/seagate-st32000542as-2tb-setup/)

---

### Post by sturkel on 2013-06-19
> **UbuntuRaptor said:**
> There seems to be a firmware update out for the  ST32000542AS hard drive. Did you look into that to see if your issue is described in the fix list? 
[http://tech.kulish.com/2011/03/05/seagate-st32000542as-2tb-setup/](http://tech.kulish.com/2011/03/05/seagate-st32000542as-2tb-setup/)
steps taken:
-replaced the sata cable
-update hd firmware
-update bios flash

all without effort.
drive starts up with ```
configured for UDMA/100
```
after the errors its ```
configured for UDMA/33
```
this is the output of smartctl
```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda LP
Device Model:     ST32000542AS
Serial Number:    xxx
LU WWN Device Id: 5 000c50 0163ddfce
Firmware Version: CC35
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Jun 19 21:00:53 2013 CEST
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
data collection:                (  633) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   100   006    Pre-fail  Always       -       120261317
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       36
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       16
  7 Seek_Error_Rate         0x000f   065   060   030    Pre-fail  Always       -       21495285693
  9 Power_On_Hours          0x0032   065   065   000    Old_age   Always       -       31316
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       30
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   083   000    Old_age   Always       -       4565619967016
189 High_Fly_Writes         0x003a   090   090   000    Old_age   Always       -       10
190 Airflow_Temperature_Cel 0x0022   065   060   045    Old_age   Always       -       35 (Min/Max 30/35)
194 Temperature_Celsius     0x0022   035   040   000    Old_age   Always       -       35 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   036   016   000    Old_age   Always       -       120261317
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       71
198 Offline_Uncorrectable   0x0010   099   099   000    Old_age   Offline      -       71
199 UDMA_CRC_Error_Count    0x003e   193   182   000    Old_age   Always       -       151417
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       227667626450012
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1723730548
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1846665479

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
what else can I try to solve this

---

### Post by user_of_gnomes on 2013-06-19
99 pending sectors and 100 reallocated? Am I reading it right?

---

### Post by sturkel on 2013-06-19
> **UbuntuRaptor said:**
> 99 pending sectors and 100 reallocated? Am I reading it right?

I don't know, if you're reading right, but the strange thing in my opinion is the smart test reported no errors
or am I reading wrong?

---

### Post by user_of_gnomes on 2013-06-19
> **sturkel said:**
> I don't know, if you're reading right, but the strange thing in my opinion is the smart test reported no errors
or am I reading wrong?

S.M.A.R.T triggers are based on manufacturer's standards. Sometimes they set wholly unrealistic tresholds or no tresholds at all. 

Bad sectors Might explain the slowness. Doesn't explain why it sets it to UDMA 33, though. Have you tried testing this hard drive on a system with a different mainboard?

You should probably get some of the manufacturer's diagnostic software on it and do a full scan to see what it comes up with.

---

### Post by sturkel on 2013-06-20
> **UbuntuRaptor said:**
> S.M.A.R.T triggers are based on manufacturer's standards. Sometimes they set wholly unrealistic tresholds or no tresholds at all. 

Bad sectors Might explain the slowness. Doesn't explain why it sets it to UDMA 33, though. Have you tried testing this hard drive on a system with a different mainboard?

You should probably get some of the manufacturer's diagnostic software on it and do a full scan to see what it comes up with.

Yesterday evening tried the hd in my desktop pc.
copied data and run a disk scan.
not very quick, but an acceptable continuous transfer read.

this morning back in my ubuntu server, same problem as before.
the main hd is on the same sata controller, but this hd hasn't those problems

---

