---
title: "Need to assess hard drive health."
date: 2009-01-17
forum: Hardware
---

### Post by Twilight in Zero on 2009-01-17
Recently, I attemped a partitioning renovation where I would gradually move the contents of an ntfs partition into my /home by gradually resizing and moving the partitions, and gradually moving the data. I succeeded in deleting Windows and moving my Ubuntu partitions to the front of my drive, when I hit an unexpected roadblock: I have bad sectors in my ntfs partition!

Fortunately, I was able to copy most of my stuff to my iPod, as part of backing up before the procedure, and I've been working off of it for the time being, until I know that my drive will be fine. I really need for it to be fine. Read ahead if you wish to know why.

Here's what I've done thus far in a little more detail: I planned on using an Ibex liveCD to do the resizing and moving. GParted on there showed a warning icon next to my ntfs partition, and refused to show how much space was used/unused, which means that I can't do anything with it. *I've actually had this icon for a very long time, since I first installed Hardy, actually*, and I never paid it any mind until now. I just used BootIt NG to do the partition work for that.

When I checked out more info on it in GParted, it told me that it had at least 1024 bad sectors. It told me to chkdsk /f /r and then reboot twice, which I don't think I could do... I'd already deleted Windows. Fortunately, the Vista Install CD still allows recovery console when no Windows install is present. I chkdsk /f /r'd there, and restarted back to the live CD. It still said the same thing.

I installed a tool called GSmartControl. It told me that it had passed the basic health check, but that there were 966 errors in the ATA Error Count. After some more research, I ran badblocks in read-only mode. A lot. After repeatedly running badblocks, my error count jumped to 2591. I picked up on that, and ran it once more, and the error count jumped up to 3101.

I also checked the Attributes tab. While it hasn't failed anything or given any warnings except for a temperature test in the past due to my fan being clogged a long while back, there are some non-zero values for three entries: 8 for Reallocated Sector Count, 14 for Offline Uncorrectable, and 14 for Current Pending Sector Count. I don't know how to interpret these.

Two of the times I ran badblocks, I had the results output to files. The second to last time, the file had 194 lines it, the lines being bad blocks it found. Strangely, this time, it only had 70 lines in it. I don't know what that means. I also found, while researching, that sometimes NTFS bad sector counts are wrong. Maybe I could fix that somehow.

Let me go ahead and get to the point. I know that there are definitely bad blocks on my hard drive, but I need to prolong its life and use; I may not be able to get a new hard drive. I can't stress that enough; it seems as if computer guys (myself included) trump up negativity a lot, not to mention thinking that everybody has money to get new hardware (not me, I know I'm poor).

I need to find out what kind of health my hard drive really has, as well as how **realistically** likely it is that it will deteriorate further, and the realistic probability that it will damage my data. I want to find some way to clear the list of bad sectors in my ntfs partition, and chkdsk again to find out how many are really there (though it seems GParted won't work if there are ANY bad sectors). I also intend on finishing this partitioning renovation. Can I get GParted to operate on the partition even though it's got bad sectors?

Thanks for your help. If you need to ask more questions, please feel free. :)

---

### Post by 73ckn797 on 2009-01-17
In similar situations I have booted the Windows disk and via recovery reformatted the drive then run chkdsk. If bad sectors still show up I would figure I had a bad hard disk. I feel that the Windows format does a thorough job as compared to gparted. After gparted I always find there is a residual/remaining section that remains in the graphical display when running gparted. When I run from Windows partioning it does not show any used drive space. It is usually a colored section at the head/left side of the display in gparted.

Does this make sense?

---

### Post by Twilight in Zero on 2009-01-17
I want to avoid formatting if possible. My dad has a huge hard drive, so I suppose I could use my ipod to temporarily move all my stuff to his computer, but it would be much, much slower than keeping it on my hard drive. I just need to resize and slide, repeatedly until the partition shrinks to nothing. My /home will grow to replace it.

I didn't know Windows had a partitioning tool. I wouldn't trust it, anyway. :P I can use BootIt NG if GParted won't hack it.

---

### Post by 73ckn797 on 2009-01-17
> **Twilight in Zero said:**
> I didn't know Windows had a partitioning tool. I wouldn't trust it, anyway. :P I can use BootIt NG if GParted won't hack it.


It is called "fdisk" and runs from the command line. It does work and quite well.

---

### Post by Twilight in Zero on 2009-01-17
I know that GParted uses a tool called ntfsresize for its ntfs partition work. I could use it with --bad-blocks if my hard drive will be fine after all.

But even so, I have much less of an idea what I'm doing if I use a command line tool. With GParted, I can see it. I don't want to use a command line tool. I suppose I might if I have to, but I'd much prefer not.

And again... I don't trust Windows' partitioning tools. And I've never heard of fdisk being a partitioning tool. Diskpart (which I had temporarily forgot about), yes, but not fdisk.

This is all presently beside the point, at the moment. I need to know if my hard drive is healthy enough to continue using before I worry about that stuff!

---

### Post by Twilight in Zero on 2009-01-17
Bump?

---

### Post by information_entropy on 2009-01-17
If your drive is S.M.A.R.T compatible
(almost anything less than a decade old is)

```
sudo apt-get install smartmontools
```

Installs several hard drive monitoring tools

The following are some common usages 
that produce useful diagnostic output

```
sudo smartctl -H /dev/sda

sudo smartctl -i /dev/sda

sudo smartctl -A /dev/sda
```

---

### Post by Twilight in Zero on 2009-01-17
Fortunately, I already had those as a requirement for GSmartControl.

I combined the command line switches, and did sudo smartctl -HiA /dev/sda. The output is:
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.3
Device Model:     ST9160821A
Serial Number:    5MA1LFTD
Firmware Version: 3.ALC
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sat Jan 17 19:15:19 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   099   006    Pre-fail  Always       -       117572726
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2683
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       8
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       90491702080
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       9901
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2623
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       2880
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   037   045    Old_age   Always   In_the_past 46 (Lifetime Min/Max 12/46)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1281
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       611412
194 Temperature_Celsius     0x0022   046   063   000    Old_age   Always       -       46 (0 7 0 0)
195 Hardware_ECC_Recovered  0x001a   068   051   000    Old_age   Always       -       201617071
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       14
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       14
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0
```

---

