---
title: "Hard Drive Failure..."
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by PsypherPunk on 2007-12-02
I woke up this morning to find my server had randomly reset itself during the night but had failed to boot up, nor can it be.

Of the five hard drives therein, four are perfectly fine but one, a 400Gb ext3-formatted drive, is having some problems. Mounting it gives the following:

```
psy011:/home/psypherpunk # mount /dev/hdc1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Dmesg returns: 

```
EXT3-fs: #blocks per group too big: 32768
```

Running fsck gives:

```
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Group descriptors look bad... trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext2 /dev/hdc1 failed (status 0x8). Run manually!
```

...and I've tried passing an alternative superblock (at n*8192+1) but the same error is repeated.

Any ideas? Cheers.

---

### Post by mellowd on 2007-12-02
Are you able to see the drive in another PC? 

If it's crashed there isn't a whole lot you can do.

---

### Post by tgalati4 on 2007-12-02
Search the net for "200 things to try to revive a hard drive."

Looks like hardware failure.  How old is the drive?  Remove it from its cage and feel it while it is connected and spinning.  Hold it to your ear.  Does it sound normal or loud and whining?  Try tilting and see if the tilting forces change the tone of the spinning, that would indicate bearing wear.

Did you have SMART enabled and SMART monitor (smartd) running to catch any pre-failure messages?  Check your /var/log files for the errors before reset.  Normally read errors will get logged before lockup.  That would indicate a head crash or bearing failure (likely for a server).

What was the uptime for the machine at the point of failure?

Post the output of:

>sudo hdparm -iI /dev/hdc1

---

### Post by PsypherPunk on 2007-12-02
The drives the newest one I own; I bought it six months or so ago. It's currently sitting in my desktop PC so I should be able to play with it. The hdparm command gives:

```
/dev/hdc1:
 HDIO_GET_IDENTITY failed: Invalid argument

ATA device, with non-removable media
        Model Number:       ST3400832A
        Serial Number:      3NF0288R
        Firmware Revision:  3.03
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   4047
        heads           16      16
        sectors/track   63      255
        --
        CHS current addressable sectors:   16511760
        LBA    user addressable sectors:  268435455
        device size with M = 1024*1024:      131071 MBytes
        device size with M = 1000*1000:      137438 MBytes (137 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by CSEL 
```

Thanks, I'll check out that article.

Edit: I've moved the drive around and it doesn't make any particular noise beyond a standard spinning sound. The uptime of the server was less than 24 hours when it shut down (the /var/log/messages file reports nothing from around 18:00 yesterday until around 09:00 this morning when there's a restart entry, though this shouldn't have happened).

---

### Post by dasunst3r on 2007-12-02
You should install *smartmontools*: *sudo apt-get install smartmontools*.  After that, run *smartctl*: *sudo smartctl -a /dev/hdc*.  Please post the output for that.

---

### Post by PsypherPunk on 2007-12-02
Here's the output:

```
smartctl version 5.37 [i686-suse-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Warning! Drive Identity Structure error: invalid SMART checksum.
=== START OF INFORMATION SECTION ===
Device Model:     T3400832@
Serial Number:    3NF0288R
Firmware Version: 3.00
User Capacity:    137,438,952,960 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Dec  2 17:45:14 2007 GMT
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
                  Checking for SMART support by trying SMART ENABLE command.
                  SMART ENABLE appeared to work!  Continuing.
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
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
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 134) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   047   033   006    Pre-fail  Always       -       134331268
  3 Spin_Up_Time            0x0003   065   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   004   100   020    Old_age   Always   FAILING_NOW 145
  4 Start_Stop_Count        0x0033   004   100   004    Pre-fail  Always   FAILING_NOW 0
  4 Start_Stop_Count        0x000f   064   060   030    Pre-fail  Always       -       171913964325
  4 Start_Stop_Count        <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
  7 Seek_Error_Rate         <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2282
 10 Spin_Retry_Count        0x0013   068   100   097    Pre-fail  Always   FAILING_NOW 0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x0022   037   057   000    Old_age   Always       -       77309411365
193 Load_Cycle_Count        0x001a   047   046   000    Old_age   Always       -       197558579
196 Reallocated_Event_Count 0x0012   068   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0010   004   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x003e   136   196   000    Old_age   Always       -       7
198 Offline_Uncorrectable   <== Data Page      |  WARNING: PREVIOUS ATTRIBUTE HAS TWO
196 Reallocated_Event_Count <== Threshold Page |  INCONSISTENT IDENTITIES IN THE DATA
200 Multi_Zone_Error_Rate   0x0000   004   252   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   036   253   000    Old_age   Always       -       0

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
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

### Post by tgalati4 on 2007-12-02
5 drives in one machine could cause a sag in the 12VDC power rail.  Check the voltage (yellow and black wires) when all 5 drives are running.  

The drive may be OK, though the data may be toast.  You may need to use the Seagate low-level format tool to revive the disk.  It can be found at the website or on the Ultimate Boot CD.

Now that you have installed SMART make sure the daemon (smartd) is always running.  Don't leave home without it.

---

### Post by PsypherPunk on 2007-12-02
The server it was attached to won't boot. There seems to be a flicker of life when you flick the switch (network adapter lights up and the CPU fan twitches) but nothing's coming to life.

I'm going to see if I can recover the data and then I'll figure out if the drive's shot. Cheers, all.

---

### Post by tgalati4 on 2007-12-02
Could be a southbridge chip that went toasty.  Dealing with 5 drives simultaneously will cause the I/O controller to work hard.

---

