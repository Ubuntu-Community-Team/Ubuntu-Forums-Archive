---
title: "What implies when gnome-disk-utility showing SMART &quot;SELF-TEST FAILED&quot; ?"
date: 2019-01-11
forum: Hardware
---

### Post by bijaydeyp on 2019-01-11
Hi,
I wanted to check my hdd health status. N.B. one of my partitions is encrypted.
  
at first, I ran gnome-disk-utility. after 10% progress, self-test turned off showing "SELF-TEST FAILED".

next, I ran smartmontools commands ```
$ sudo smartctl -l selftest /dev/sda
```. the test result shows these...

                        [TABLE]
[TR]
[TD]             === START OF READ SMART DATA SECTION ===[/TD]
[/TR]
[TR]
[TD]             SMART Self-test log structure revision number 1[/TD]
[/TR]
[TR]
[TD]             Num  Test_Description     Status                                               Remaining     LifeTime(hours)     LBA_of_first_error[/TD]
[/TR]
[TR]
[TD]             # 1 Extended offline       Completed: read failure           90%                  8571                            62019076[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 2  Extended offline       Completed: read failure           90%                  8563                            65358817[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 3  Short offline            Completed: read failure     90%                  8563                           241861949[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 4  Extended offline       Completed: read failure           90%                  8563                           60593796[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 5  Extended offline       Completed: read failure           90%                  8562                          60593796[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 6  Short offline            Interrupted (host reset)          30%                  8295                          -[/TD]
[/TR]
[TR]
[TD="width: 100%"]             # 7  Short offline            Completed without error          00%                  3680                           -[/TD]
[/TR]
[TR]
[TD="width: 100%"][/TD]
[/TR]
[/TABLE]
  

the Command ```
$ sudo smartctl -t long /dev/sda
``` and ```
$ sudo smartctl -H /dev/sda
``` show these...

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

the Command ```
sudo smartctl -i /dev/sda
``` shows these...

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint M7
Device Model:     SAMSUNG HM250HI
Serial Number:    S20TJ9AZ537614
LU WWN Device Id: 5 0024e9 2029037a2
Firmware Version: 2AC101C4
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Fri Jan 11 10:08:56 2019 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


Bottomline: I am overall confused! plz help!

---

### Post by TheFu on 2019-01-11
We need to see the 20+ parameters that **sudo smartctl -a /dev/sda** produces.  However, the usefulness of this output isn't much for SSD/flash storage.

Also, running a long test weekly is a good idea on spinning disks, then you can check the results later.  It takes time for the tests to complete, so you can't request a test and immediately ask for the results.  Short tests take 1-3 minutes. Long tests can take an hour.

I've never used gnome-disks. Read that people I respect avoid it.

---

