---
title: "Chronic hard drive woes."
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Kharnov on 2007-10-19
Hey guys. This is my first post here, so I figure I might as well introduce myself in one sentence: I'm a completely broke college student that just upgraded from Xubuntu Feisty to Gutsy and i'm absolutely loving it.

Anyway, i've been having some hard drive issues on my laptop for quite a while, in fact ever since six or so months ago when I first made the switch from Win XP to Xubuntu. Before anyone says anything about buying a new laptop, though, please remember that i'm trying to live off this antique T23 for as long as I can, because i'm not getting a new laptop till the end of the year.

The problems could be best described as random clicking that comes from my hard drive, everything freezes, and messages like this start to flood the screen if i'm booting up or in the terminal:

> [ 6566.732000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 6566.732000] ata1.00: (BMDMA stat 0x25)
[ 6566.732000] ata1.00: cmd c8/00:08:90:3b:3c/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
[ 6566.732000]          res 51/40:04:94:3b:3c/00:00:00:00:00/e2 Emask 0x9 (media error)


I've found a temporary solution in that i've been able to stop my problems for a day at a time by booting into my GParted live CD and doing this at the terminal every night:

> badblocks -nsv /dev/hda1 ; badblocks -nsv /dev/hda2 ; e2fsck -fvy /dev/hda1

/dev/hda1 is a 18 GB EXT2 partition, and /dev/hda2 is a 580 MB Swap partition.

After doing that, the clicking and the freezing usually goes away for a day, but the problem is that I need to do that every night or else the next time I boot up, it happens again.

Any thoughts? I don't think my hard drive's been showing any signs of failing yet, it's been doing this for a while.

---

### Post by Kharnov on 2007-10-19
Anyone?

---

### Post by Kharnov on 2007-10-21
Could I at least get a post saying "I don't know how to help you" so I can move on?

---

### Post by nick_h on 2007-10-23
It could be that the drive is failing - do the badblocks and e2fsck show any errors?

You could try installing the package *smartmontools* and run:
```
sudo smartctl --device=ata --attributes /dev/sda
```

A quick google found [this](http://ubuntuforums.org/showthread.php?t=555674) thread and [bug #151938](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938) which may be worth reading.

---

### Post by Kharnov on 2007-10-23
Thanks for the response! Disregard my last two posts, it's just that i'm adjusted to seeing problems worse than mine fixed here within a day or two. :-P

Anyway, badblocks shows errors, mostly of the "i/o error" variety, while e2fsck gives me looooong lists of errors that it fixes every time I run it. I'm used to it by now, it's something i've seen every evening when I run those two programs. Nothing gets worse, nothing gets better, it never changes. There's always the same amount of errors.

As for running sudo smartctl --device=ata --attributes /dev/sda, I get this:

```
=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000d   100   100   050    Pre-fail  Offline      -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   100   100   050    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2298
  5 Reallocated_Sector_Ct   0x0033   001   001   010    Pre-fail  Always   FAILING_NOW 2313
  7 Seek_Error_Rate         0x000f   100   100   050    Pre-fail  Always       -       480
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Minutes        0x0032   084   084   000    Old_age   Always       -       8156h+04m
 10 Spin_Retry_Count        0x0013   100   100   050    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1898
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       23
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       197
193 Load_Cycle_Count        0x0032   007   007   000    Old_age   Always       -       560845/560647
194 Temperature_Celsius     0x0022   068   034   000    Old_age   Always       -       56 (Lifetime Min/Max 16/73)
195 Hardware_ECC_Recovered  0x001a   100   001   000    Old_age   Always       -       142219
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       2061
197 Current_Pending_Sector  0x0032   100   082   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0012   100   100   000    Old_age   Always       -       66
230 Head_Amplitude          0x0032   088   088   000    Old_age   Always       -       382796
250 Read_Error_Retry_Rate   0x000a   100   001   000    Old_age   Always       -       813

```

Ouch, they're all either old age or pre-fail. How long do you think my hard drive'll last like this?

---

### Post by Linicks on 2007-10-23
> It's dead Jim, as far as we know it.

It can be minutes or weeks.  You have no choice but to get a new one, unless you have nothing to waste and wait until it dies.

Nick

---

### Post by Kharnov on 2007-10-23
Well, that's bleak. Thanks, though.

I wonder if I should dissect it after it dies and take pictures, so that I could show the world the insides of *yet another* failed Hitachi drive. :(

---

### Post by nick_h on 2007-10-23
It's not the pre-fail and old-age you need to worry about - they are just the counter type (mine are the same).

Your reallocated sector count is very high though and indicates that the drive is about to fail.  Backup any data you need now.

---

