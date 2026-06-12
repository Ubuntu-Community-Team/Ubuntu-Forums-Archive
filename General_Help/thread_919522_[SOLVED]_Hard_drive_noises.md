---
title: "[SOLVED] Hard drive noises"
date: 2008-09-14
forum: General Help
---

### Post by civillian on 2008-09-14
Not sure where to post this, so I figured general help would be a good place to start :confused:

Basically, a few days a go I got a new hard drive (seagate barracuda 500GB) and it clicks. I'm not sure if they are just the noise my hard drives makes anyway, or whether or not its a sign of a defective drive. They only make the noise when the hard drive is being accessed (starting up large programs like OopenOffice and F-spot, or when I'm scanning my music library in quod-libet. 

I recorded the sounds to post (since I'm aware 'clicking' is a vague description of the sound) and they are [COLOR="Red"]_*[here](http://www.civint.110mb.com/hdd-clicks-1.ogg)*_[/COLOR] and [COLOR="Red"]*_[here](http://www.civint.110mb.com/hdd-clicks-2.ogg)_*[/COLOR].

The first recording was taken inside the computer casing, and the second from outside (with a mobile phone, so the qualitys not great but they give you an idea of the noise my computers making.

As I said, is this a normal (if not healthy) sound form my hard drive to be making? Or should I back up quickly and get a replacement drive?
Thanks

Civ

---

### Post by bingoUV on 2008-09-14
Check the health and status of your hard drive with smart as follows. Post here the output of the following command. Replace /dev/sda by the device name of your hard drive. 
```

sudo smartctl -Ha /dev/sda

```

---

### Post by civillian on 2008-09-14
```
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3500630AS
Serial Number:    9QG8H47C
Firmware Version: 3.AAD
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep 14 18:43:20 2008 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
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
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 163) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   109   100   006    Pre-fail  Always       -       22962292
  3 Spin_Up_Time            0x0003   093   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       28
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   060   060   030    Pre-fail  Always       -       1083480
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       41
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       29
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   060   058   045    Old_age   Always       -       672399400
194 Temperature_Celsius     0x0022   040   042   000    Old_age   Always       -       40 (Lifetime Min/Max 0/19)
195 Hardware_ECC_Recovered  0x001a   079   067   000    Old_age   Always       -       158475246
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

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

Thats the ouput from > 
sudo smartctl -Ha /dev/sda

I have to be honest here and say it doesnt make much sense to me :s

---

### Post by Sycron on 2008-09-14
I'm so happy that I have SSD, no more moving parts inside...

---

### Post by civillian on 2008-09-14
Can anyone reveal the mysteries of the output I just posted?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **C!V!NT said:**
> I have to be honest here and say it doesnt make much sense to me :s

Well, you have very high Raw_Read_Error_Rate, Seek_Error_Rate and Hardware_ECC_Recovered values.

I think the disk is dead ...

Kudos to bingoUV for immediately asking smartctl -a infos :)
And no kudo to Sycron, for pitying your situation without telling you the awful truth ;)  (just kidding)

---

### Post by civillian on 2008-09-14
well, I'm getting a new HDD (not too much of a big deal, did a system backup yesterday) and as for awful truth? I'd rather pay £30 for 500GB than £72 for 32GB (avg prices for SSDs in UK). Anyway, if HDD is good enough for servers, it's good enough for me, lol.

---

### Post by bingoUV on 2008-09-14
Smart is not explicitly giving a warning, so not necessary to replace the hard disk. Just keep a periodic backup, and smart check the backup hard disk too ;). This is assuming there is no mission critical data on the hard drive.

Seagate drives are famous for very high numbers for these errors. I guess the keywords from the smartctl output for non-critical use are:

1. No errors logged.
2. SMART overall-health self-assessment test result: PASSED

The hard drive could easily last a decade more. Just keep a backup.

---

### Post by Sycron on 2008-09-14
Well if you want that for a server then I recommend a HDD. Personally I'm using a 4.0GB SSD. I just don't need more than that....

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **bingoUV said:**
> Seagate drives are famous for very high numbers for these errors.

Yeah, I guess the OP could ```
sudo dd if=/dev/sda of=/dev/null
``` and check dmesg and "tail -f /var/log/{syslog,messages}" to see if the disk should really be considered unreliable.

---

### Post by bingoUV on 2008-09-14
Smart errors catch errors about factors affecting the drive electronics. Some of the metrics are affected by magnetic surface quality, but in general smart errors/warnings are about drive electronics. As the initial suspicion was because of noise, we don't have prima facie evidence against magnetic surface.

dd'ing it might catch some errors but it will mostly catch issues with magnetic surface. fsck with badblocks option will do this in more detail; it will also add the IDs of blocks that were not behaving properly to the badblocks list of the filesystem so that the filesystem does not use these blocks in future. Only problem is, this cannot be done for the whole hard disk. This needs to be performed for individual ext3 partitions. For this,
```

/sbin/fsck.ext3 -c /dev/sda1

```

Replace /dev/sda1 by an ext3 partition device name. This needs to be done from a live CD, as it is a read-write operation and the partition will need to be unmounted.

I don't foresee much chance of discovery of a big error from this elaborate process. It can be done whenever upgrading the OS, or installing a new OS.

---

