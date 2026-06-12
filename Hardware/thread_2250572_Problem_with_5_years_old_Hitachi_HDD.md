---
title: "Problem with 5 years old Hitachi HDD"
date: 2014-10-29
forum: Hardware
---

### Post by andrew-pyndyk on 2014-10-29
After improper shutdown , ubuntu loaded in initramfs. I booted from live cd ubuntu, tried to mount a hard drive using "disks", using the command line , but nothing helped.

Here's "disks" error output for mounting.

```
Error mounting /dev/sda1 at /media/root/84012a8e-96d6-47d9-b5a4-3342c72bcca2: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/root/84012a8e-96d6-47d9-b5a4-3342c72bcca2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)
```

"dmesg | tail" output

```
root@ubuntu:~# dmesg | tail
[  796.664315] Descriptor sense data with sense descriptors (in hex):
[  796.664323]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  796.664331]         00 00 00 00 
[  796.664335] sd 0:0:0:0: [sda]  
[  796.664337] Add. Sense: Scsi parity error
[  796.664339] sd 0:0:0:0: [sda] CDB: 
[  796.664340] Write(10): 2a 00 35 40 08 20 00 00 08 00
[  796.664356] ata1: EH complete
[  796.664368] JBD2: recovery failed
[  796.664373] EXT4-fs (sda1): error loading journal
```

fsck output:
```
root@ubuntu:~# fsck /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes
fsck.ext4: unable to set superblock flags on /dev/sda1


/dev/sda1: ********** WARNING: Filesystem still has errors **********
```



I tried to recover ext4 superblocks one-by-one, but log said me something like **Drive still have errors**

Trying to reinstall ubuntu causes 

```
Input/output error write on /dev/sda
```

After cancelling install it says 

```
Error fsyncing/closing /dev/sda: Input/output error
```

Any ideas?

---

### Post by weatherman2 on 2014-10-29
Check the drive's S.M.A.R.T. status with GSmartControl.  You will have to install that in a live session.  Look at any Attributes highlighted in red or pink (if something is labeled "pre-failure" but not highlighted, it's probably normal and not an error).  Hard drives do fail - it would not be unusual for a 5-year-old drive to have begun to fail.

---

### Post by andrew-pyndyk on 2014-10-29
I've got this.

"Overall Health Self-Assessment Test UNKNOWN!"

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MJA BH
Device Model:     FUJITSU MJA2500BH G2
Serial Number:    K94STA52EAGN
LU WWN Device Id: 5 00000e 04485b33e
Firmware Version: 8919
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 3f
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Oct 29 21:43:48 2014 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Read SMART Data failed: scsi error aborted command

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: UNKNOWN!
SMART Status, Attributes and Thresholds cannot be read.

SMART Error Log Version: 1
ATA Error Count: 1563 (device log contains only the most recent five errors)
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

Error 1563 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 53 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 00 08 c4 40 08      01:00:15.531  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      01:00:15.530  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      01:00:15.528  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:00:15.528  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      01:00:15.528  SET FEATURES [Enable SATA feature]

Error 1562 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 4b 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 48 00 08 c4 40 08      01:00:10.872  READ FPDMA QUEUED
  60 00 40 00 06 c4 40 08      01:00:10.869  READ FPDMA QUEUED
  60 00 38 00 04 c4 40 08      01:00:10.864  READ FPDMA QUEUED
  60 00 30 00 02 c4 40 08      01:00:10.861  READ FPDMA QUEUED
  60 00 28 00 00 c4 40 08      01:00:10.858  READ FPDMA QUEUED

Error 1561 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 43 10 bb 64 40  Error: UNC at LBA = 0x0064bb10 = 6601488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 40 10 bb 64 40 08      00:53:26.085  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      00:53:26.085  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:53:26.082  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:53:26.082  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:53:26.082  SET FEATURES [Enable SATA feature]

Error 1560 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3b 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 08 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 30 00 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 28 f8 ba 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 20 f0 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED
  60 08 18 e8 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED

Error 1559 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 23 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 20 00 ba 64 40 08      00:53:16.703  READ FPDMA QUEUED
  60 00 18 00 b8 64 40 08      00:53:16.700  READ FPDMA QUEUED
  60 00 10 00 b6 64 40 08      00:53:16.695  READ FPDMA QUEUED
  60 00 08 00 b4 64 40 08      00:53:16.692  READ FPDMA QUEUED
  60 00 00 00 b2 64 40 08      00:53:16.689  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     28565         482797952
# 2  Short offline       Completed: read failure       90%     28565         482797952
# 3  Short offline       Completed: read failure       90%     28564         482797928
# 4  Short offline       Completed: read failure       90%     28564         482797928
# 5  Extended offline    Completed: read failure       50%     28269         482677912
# 6  Short offline       Completed without error       00%     28268         -
# 7  Short offline       Completed without error       00%     28266         -
# 8  Extended offline    Aborted by host               80%     28266         -
# 9  Short offline       Completed without error       00%     28266         -
#10  Short offline       Completed without error       00%     28265         -
#11  Short offline       Completed without error       00%     28265         -
#12  Short offline       Completed without error       00%     28265         -
#13  Short offline       Completed without error       00%     28265         -
#14  Short offline       Completed without error       00%     28265         -
#15  Extended offline    Aborted by host               80%     28265         -
#16  Short offline       Completed without error       00%     28264         -
#17  Short offline       Completed without error       00%     18468         -
#18  Short offline       Completed without error       00%     17806         -
#19  Short offline       Completed without error       00%     17669         -

Selective Self-tests/Logging not supported
```

---

### Post by andrew-pyndyk on 2014-10-29
And also this 

```
Overall Health Self-Assessment Test UNKNOWN!
```

---

### Post by weatherman2 on 2014-10-29
Try running smartctl with the following options:


-T permissive
-d sat
-T permissive -d sat

(try it all three ways)

and see if you get any change in your results.

But the read errors sure don't look good.  The test was unable to read the same LBA several times in a row.  Disk failure looks probable based on that.

---

### Post by andrew-pyndyk on 2014-10-29
-T permissive

```
root@ubuntu:~# smartctl -T permissive /dev/sda1
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

ATA device successfully opened


```

-d sat

```
root@ubuntu:~# smartctl -d sat /dev/sda1
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

ATA device successfully opened


```

-T permissive -d sat

```
root@ubuntu:~# smartctl -T permissive -d sat /dev/sda1
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

ATA device successfully opened


```

Trying to mount disk

```
Error mounting /dev/sda1 at /media/ubuntu/84012a8e-96d6-47d9-b5a4-3342c72bcca2: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/ubuntu/84012a8e-96d6-47d9-b5a4-3342c72bcca2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by weatherman2 on 2014-10-29
You need to add an option like -a at the end to get info - so

```

sudo smartctl -a -T permissive /dev/sda
sudo smartctl -a -d sat /dev/sda
sudo smartctl -a -T permissive -d sat /dev/sda

```

---

### Post by weatherman2 on 2014-10-29
And give /dev/sda as the drive - not /dev/sda1 - to smartctl.  sda1 is the name of the partition.

---

### Post by andrew-pyndyk on 2014-10-29
Ok, i get it.

sudo smartctl -a -T permissive /dev/sda

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MJA BH
Device Model:     FUJITSU MJA2500BH G2
Serial Number:    K94STA52EAGN
LU WWN Device Id: 5 00000e 04485b33e
Firmware Version: 8919
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 3f
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Oct 30 02:28:03 2014 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Read SMART Data failed: scsi error aborted command

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: UNKNOWN!
SMART Status, Attributes and Thresholds cannot be read.

SMART Error Log Version: 1
ATA Error Count: 1563 (device log contains only the most recent five errors)
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

Error 1563 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 53 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 00 08 c4 40 08      01:00:15.531  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      01:00:15.530  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      01:00:15.528  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:00:15.528  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      01:00:15.528  SET FEATURES [Enable SATA feature]

Error 1562 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 4b 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 48 00 08 c4 40 08      01:00:10.872  READ FPDMA QUEUED
  60 00 40 00 06 c4 40 08      01:00:10.869  READ FPDMA QUEUED
  60 00 38 00 04 c4 40 08      01:00:10.864  READ FPDMA QUEUED
  60 00 30 00 02 c4 40 08      01:00:10.861  READ FPDMA QUEUED
  60 00 28 00 00 c4 40 08      01:00:10.858  READ FPDMA QUEUED

Error 1561 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 43 10 bb 64 40  Error: UNC at LBA = 0x0064bb10 = 6601488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 40 10 bb 64 40 08      00:53:26.085  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      00:53:26.085  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:53:26.082  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:53:26.082  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:53:26.082  SET FEATURES [Enable SATA feature]

Error 1560 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3b 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 08 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 30 00 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 28 f8 ba 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 20 f0 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED
  60 08 18 e8 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED

Error 1559 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 23 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 20 00 ba 64 40 08      00:53:16.703  READ FPDMA QUEUED
  60 00 18 00 b8 64 40 08      00:53:16.700  READ FPDMA QUEUED
  60 00 10 00 b6 64 40 08      00:53:16.695  READ FPDMA QUEUED
  60 00 08 00 b4 64 40 08      00:53:16.692  READ FPDMA QUEUED
  60 00 00 00 b2 64 40 08      00:53:16.689  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     28565         482797952
# 2  Short offline       Completed: read failure       90%     28565         482797952
# 3  Short offline       Completed: read failure       90%     28564         482797928
# 4  Short offline       Completed: read failure       90%     28564         482797928
# 5  Extended offline    Completed: read failure       50%     28269         482677912
# 6  Short offline       Completed without error       00%     28268         -
# 7  Short offline       Completed without error       00%     28266         -
# 8  Extended offline    Aborted by host               80%     28266         -
# 9  Short offline       Completed without error       00%     28266         -
#10  Short offline       Completed without error       00%     28265         -
#11  Short offline       Completed without error       00%     28265         -
#12  Short offline       Completed without error       00%     28265         -
#13  Short offline       Completed without error       00%     28265         -
#14  Short offline       Completed without error       00%     28265         -
#15  Extended offline    Aborted by host               80%     28265         -
#16  Short offline       Completed without error       00%     28264         -
#17  Short offline       Completed without error       00%     18468         -
#18  Short offline       Completed without error       00%     17806         -
#19  Short offline       Completed without error       00%     17669         -

Selective Self-tests/Logging not supported


```


sudo smartctl -a -d sat /dev/sda

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MJA BH
Device Model:     FUJITSU MJA2500BH G2
Serial Number:    K94STA52EAGN
LU WWN Device Id: 5 00000e 04485b33e
Firmware Version: 8919
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 3f
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Oct 30 02:29:53 2014 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Read SMART Data failed: scsi error aborted command

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: UNKNOWN!
SMART Status, Attributes and Thresholds cannot be read.

SMART Error Log Version: 1
ATA Error Count: 1563 (device log contains only the most recent five errors)
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

Error 1563 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 53 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 00 08 c4 40 08      01:00:15.531  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      01:00:15.530  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      01:00:15.528  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:00:15.528  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      01:00:15.528  SET FEATURES [Enable SATA feature]

Error 1562 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 4b 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 48 00 08 c4 40 08      01:00:10.872  READ FPDMA QUEUED
  60 00 40 00 06 c4 40 08      01:00:10.869  READ FPDMA QUEUED
  60 00 38 00 04 c4 40 08      01:00:10.864  READ FPDMA QUEUED
  60 00 30 00 02 c4 40 08      01:00:10.861  READ FPDMA QUEUED
  60 00 28 00 00 c4 40 08      01:00:10.858  READ FPDMA QUEUED

Error 1561 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 43 10 bb 64 40  Error: UNC at LBA = 0x0064bb10 = 6601488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 40 10 bb 64 40 08      00:53:26.085  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      00:53:26.085  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:53:26.082  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:53:26.082  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:53:26.082  SET FEATURES [Enable SATA feature]

Error 1560 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3b 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 08 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 30 00 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 28 f8 ba 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 20 f0 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED
  60 08 18 e8 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED

Error 1559 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 23 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 20 00 ba 64 40 08      00:53:16.703  READ FPDMA QUEUED
  60 00 18 00 b8 64 40 08      00:53:16.700  READ FPDMA QUEUED
  60 00 10 00 b6 64 40 08      00:53:16.695  READ FPDMA QUEUED
  60 00 08 00 b4 64 40 08      00:53:16.692  READ FPDMA QUEUED
  60 00 00 00 b2 64 40 08      00:53:16.689  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     28565         482797952
# 2  Short offline       Completed: read failure       90%     28565         482797952
# 3  Short offline       Completed: read failure       90%     28564         482797928
# 4  Short offline       Completed: read failure       90%     28564         482797928
# 5  Extended offline    Completed: read failure       50%     28269         482677912
# 6  Short offline       Completed without error       00%     28268         -
# 7  Short offline       Completed without error       00%     28266         -
# 8  Extended offline    Aborted by host               80%     28266         -
# 9  Short offline       Completed without error       00%     28266         -
#10  Short offline       Completed without error       00%     28265         -
#11  Short offline       Completed without error       00%     28265         -
#12  Short offline       Completed without error       00%     28265         -
#13  Short offline       Completed without error       00%     28265         -
#14  Short offline       Completed without error       00%     28265         -
#15  Extended offline    Aborted by host               80%     28265         -
#16  Short offline       Completed without error       00%     28264         -
#17  Short offline       Completed without error       00%     18468         -
#18  Short offline       Completed without error       00%     17806         -
#19  Short offline       Completed without error       00%     17669         -

Selective Self-tests/Logging not supported


```


sudo smartctl -a -T permissive -d sat /dev/sda

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MJA BH
Device Model:     FUJITSU MJA2500BH G2
Serial Number:    K94STA52EAGN
LU WWN Device Id: 5 00000e 04485b33e
Firmware Version: 8919
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 3f
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Oct 30 02:30:52 2014 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

Read SMART Data failed: scsi error aborted command

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: UNKNOWN!
SMART Status, Attributes and Thresholds cannot be read.

SMART Error Log Version: 1
ATA Error Count: 1563 (device log contains only the most recent five errors)
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

Error 1563 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 53 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 00 08 c4 40 08      01:00:15.531  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      01:00:15.530  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      01:00:15.528  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:00:15.528  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      01:00:15.528  SET FEATURES [Enable SATA feature]

Error 1562 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 4b 00 08 c4 40  Error: UNC at LBA = 0x00c40800 = 12847104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 48 00 08 c4 40 08      01:00:10.872  READ FPDMA QUEUED
  60 00 40 00 06 c4 40 08      01:00:10.869  READ FPDMA QUEUED
  60 00 38 00 04 c4 40 08      01:00:10.864  READ FPDMA QUEUED
  60 00 30 00 02 c4 40 08      01:00:10.861  READ FPDMA QUEUED
  60 00 28 00 00 c4 40 08      01:00:10.858  READ FPDMA QUEUED

Error 1561 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 43 10 bb 64 40  Error: UNC at LBA = 0x0064bb10 = 6601488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 40 10 bb 64 40 08      00:53:26.085  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 08      00:53:26.085  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:53:26.082  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      00:53:26.082  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:53:26.082  SET FEATURES [Enable SATA feature]

Error 1560 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 3b 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 38 08 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 30 00 bb 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 28 f8 ba 64 40 08      00:53:21.320  READ FPDMA QUEUED
  60 08 20 f0 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED
  60 08 18 e8 ba 64 40 08      00:53:21.319  READ FPDMA QUEUED

Error 1559 occurred at disk power-on lifetime: 29789 hours (1241 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 23 08 bb 64 40  Error: UNC at LBA = 0x0064bb08 = 6601480

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 20 00 ba 64 40 08      00:53:16.703  READ FPDMA QUEUED
  60 00 18 00 b8 64 40 08      00:53:16.700  READ FPDMA QUEUED
  60 00 10 00 b6 64 40 08      00:53:16.695  READ FPDMA QUEUED
  60 00 08 00 b4 64 40 08      00:53:16.692  READ FPDMA QUEUED
  60 00 00 00 b2 64 40 08      00:53:16.689  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     28565         482797952
# 2  Short offline       Completed: read failure       90%     28565         482797952
# 3  Short offline       Completed: read failure       90%     28564         482797928
# 4  Short offline       Completed: read failure       90%     28564         482797928
# 5  Extended offline    Completed: read failure       50%     28269         482677912
# 6  Short offline       Completed without error       00%     28268         -
# 7  Short offline       Completed without error       00%     28266         -
# 8  Extended offline    Aborted by host               80%     28266         -
# 9  Short offline       Completed without error       00%     28266         -
#10  Short offline       Completed without error       00%     28265         -
#11  Short offline       Completed without error       00%     28265         -
#12  Short offline       Completed without error       00%     28265         -
#13  Short offline       Completed without error       00%     28265         -
#14  Short offline       Completed without error       00%     28265         -
#15  Extended offline    Aborted by host               80%     28265         -
#16  Short offline       Completed without error       00%     28264         -
#17  Short offline       Completed without error       00%     18468         -
#18  Short offline       Completed without error       00%     17806         -
#19  Short offline       Completed without error       00%     17669         -

Selective Self-tests/Logging not supported


```

---

### Post by weatherman2 on 2014-10-29
It seems that version of smartmontools can't read your hard drive properly.  A newer version might read the Attributes correctly.  Version 6.3 is out, and you might be able to build it - but honestly, it still looks bad for for your drive.  I suspect it is dying.

---

### Post by tgalati4 on 2014-10-30
It looks like your drive had a couple of failures.  At 1,000 hours ago, it started having LBA errors--some blocks were unreadable.  Then the power outage killed the on-board SATA controller, so it is having SATA communication issues.  So, start the data recovery process with *testdisk* and *photorec* and consider this disk toast.  30,000 hours is a lot for a consumer drive.

---

