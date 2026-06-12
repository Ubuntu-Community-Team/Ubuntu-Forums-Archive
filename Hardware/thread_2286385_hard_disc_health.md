---
title: "hard disc health"
date: 2015-07-11
forum: Hardware
---

### Post by alo12 on 2015-07-11
do you know any way i can run xubuntu through livecd and find out if my hard disc is in a good condition or if it need replacement before isntalling xubuntu?

Thank you in advance

---

### Post by weatherman2 on 2015-07-11
Sure - in the live session, install smartmontools.  Then use the smartctl command to check S.M.A.R.T. status and even run S.M.A.R.T. tests.

I've not used xubuntu in ages.  You may have to enable the "universe" repository to pick up smartmontools.

```

sudo vim /etc/apt/sources.list

```

If you see lines like:

```

#deb http://us.archive.ubuntu.com/ubuntu/ precise universe

```

With the "#" in front (commenting out the universe repository), remove the # in front of those lines.  Save the file, then run:

```

sudo apt-get update
sudo apt-get install smartmontools

```

An easier way: download a Linux distro that already has smartmontools installed.  One is called Parted Magic.  It used to be free - not anymore.  But there's still a free one (from 2013) that works fine, available from Major Geeks among other places.  GSmartControl is installed there but the icon is labeled "disk health" I believe.

---

### Post by alo12 on 2015-07-12
i have install smarttools which command i have to give next in order to get a "report" ?

---

### Post by tgalati4 on 2015-07-12
```
sudo smartctl -a /dev/sda
```

Don't post the entire report, just the parts that you think are a problem.

---

### Post by kurt18947 on 2015-07-12
There is also a 'disks' application present by default in ubuntu-gnome and I'm sure other distros, or it can be installed. One of its functions is to display SMART data. The app may be called something similar but different in the repositories - maybe gdisk? I know it can be installed and will work with Xubuntu.

---

### Post by alo12 on 2015-07-12
== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Current Drive Temperature:     48 C
Drive Trip Temperature:        65 C

Manufactured in week 05 of year 2008
Specified cycle count over device lifetime:  50000
Accumulated start-stop cycles:  4935
Elements in grown defect list: 0

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:          0      941       941       941       1090      47812,883           0
write:         0       86        86        86        113       8569,762           0
verify:        0       15        15        15         17        399,322           0

Non-medium error count:      496

SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background long   Completed                   -       1                 - [-   -    -]
# 2  Background short  Completed                   -       0                 - [-   -    -]
Long (extended) Self Test duration: 2964 seconds [49,4 minutes]

xubuntu@xubuntu:~$ 


what does it mean?

---

### Post by oldfred on 2015-07-12
SMART Health Status: OK

When it says failed then it usually is a new drive. Occasionally SMART status gives false readings.
But even if drive was brand new, you should have good backup procedures so you can restore your data without loss.

---

### Post by alo12 on 2015-07-12
thank you for your answer,

but I have not really understand is my disc in good condition or not?

---

### Post by weatherman2 on 2015-07-12
Please post the entire output of "sudo smartctl -a /dev/sda" including the Attributes.

---

### Post by alo12 on 2015-07-12
thank you for your answer,

but I have not really understand is my disc in good condition or not?

---

### Post by alo12 on 2015-07-12
xubuntu@xubuntu:~$ sudo smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

Current Drive Temperature:     48 C
Drive Trip Temperature:        65 C

Manufactured in week 05 of year 2008
Specified cycle count over device lifetime:  50000
Accumulated start-stop cycles:  4935
Elements in grown defect list: 0

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:          0      941       941       941       1090      47812,883           0
write:         0       86        86        86        113       8569,779           0
verify:        0       15        15        15         17        399,322           0

Non-medium error count:      496

SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background long   Completed                   -       1                 - [-   -    -]
# 2  Background short  Completed                   -       0                 - [-   -    -]
Long (extended) Self Test duration: 2964 seconds [49,4 minutes]

xubuntu@xubuntu:~$ 



i gave the commanrd through livecs xubuntu these are the results...

---

### Post by weatherman2 on 2015-07-12
This is a much newer version of smartctl than I am used to using.  I don't see any Attributes listed.  Usually there is a table of Attributes listed like this, from one of my hard drives:

```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       1739
  3 Spin_Up_Time            0x0007   130   130   033    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0012   097   097   000    Old_age   Always       -       6180
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   085   085   000    Old_age   Always       -       6845
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       5937
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       59
193 Load_Cycle_Count        0x0012   095   095   000    Old_age   Always       -       50440
194 Temperature_Celsius     0x0002   183   183   000    Old_age   Always       -       30 (Min/Max 8/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

```

---

### Post by alo12 on 2015-07-12
How i will find out the confition of my disc ?

---

### Post by alo12 on 2015-07-14
i have run the programm hdd sentinel from windows the performance of my hard disc and it's health are shown as 100% the "programm says" that my 8 years old hard disc is in perfect condition. The only number taht is making my upset is the temperature of 51 celcius(steady) should i trust it?

---

### Post by tgalati4 on 2015-07-14
Your disk drive is old, but seems to be OK.  It should be able to handle installing a new OS.  I don't know why the attributes table does not get displayed.  Perhaps the SMART firmware on the disk drive does not support it, or there is some issue between the LiveUSB environment you are running and SMART.  Regardless, try a regular installation of Xubuntu and set it up the way you want.

The temperatures of the drive are high, but use a fan to cool it to see if they come down.  You want to keep them below the trip temperature, obviously, but higher temperatures will shorten the life.  My laptop drive runs 35C to 41C.

---

### Post by alo12 on 2015-07-14
thank you for your answer. So you think that i "should trust" hdd sentinel. it is true that my hard disc is old enough. The good news for the temperature issue is that is steady there. I want to "clean" the disc with dban and then install ubuntu....Do you think i will be ok?

---

### Post by tgalati4 on 2015-07-15
I don't think you need dban.  Just use gparted to create new partitions (Ext4 and swap).  Assign root (/) to the Ext4 partition and check the "format" box so that the new partition will get formatted.  You can also do this within the installer by using the Manual Partitioner or "Do Something Else" when asked how you want to install.

The multiple delete passes of dban will just put more wear and tear on an old drive.  It's not like you are selling the laptop to somebody else or disposing it--I would use dban for those cases.

---

