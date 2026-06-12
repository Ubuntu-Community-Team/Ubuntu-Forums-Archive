---
title: "Please tell me what this smartctl report means:"
date: 2012-04-30
forum: Hardware
---

### Post by Mark Uhde on 2012-04-30
I hate to bump such an ancient thread, but it's short and hopefully this will help both me and possibly the OP. One, to the OP, I'd love to know the status of that drive now, years down the road.

For myself, I have one of these drives I pulled out of a Dell Mini 10 brand new nearly two years ago (I wanted a bigger drive anyways and I didn't trust it because Ubuntu said it was failing - brand new I will note), and the drive has sat virtually unused. I'm considering using it for a pfSense server for a non-profit (save them ever penny I can, they're friends of mine, and I'm charging just parts - this is my good deed/volunteer work). Here is the SMART status. It is worth noting that the reallocated event count has about doubled in the last 20 hours:

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2000
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1544
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       74
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       79
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       56
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       46
194 Temperature_Celsius     0x0022   151   079   000    Old_age   Always       -       29 (Min/Max 8/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4127
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       179
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       535
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0
```

And here is the drive info:

```
=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint M5
Device Model:     SAMSUNG HM160HI
Serial Number:    S14QJDRSB30151
LU WWN Device Id: 5 0f0000 03141a423
Firmware Version: HH100-15
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Mon Apr 30 15:10:12 2012 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

If the OP manages to see this (a notification or anything), or else - anyone else - do you feel that this drive is trustworthy and displaying nonsense SMART data? Or should it simply be junked?

Thanks a ton!

Mark

---

### Post by ahallubuntu on 2012-04-30
You probably should have just started a new thread instead of resurrecting an old one.  In any case...

You have a reallocated event count of 4127 - which indicates a serious if not catastrophic drive failure.  Plus 179 pending sectors (which cannot be read).  Most likely the drive surface is failing.  Assuming the drive will be completely dead soon.  It should go without saying that you should have already backed up anything important - if not, better do so NOW before this thing completely dies.

Once you have gotten anything you wanted off of this drive, you can try zeroing it out completely with a program like DBAN ([www.dban.org](www.dban.org)), which is a CD you can download/burn and run to wipe the drive completely.  SOMETIMES a soft error of some sort can cause a few pending sector errors, and zeroing the drive can clear them - but you have a lot of errors, so that seems unlikely.  Still, once you have nothing to lose you might as well try it.  Check S.M.A.R.T. again after running DBAN.  If after that you still have any pending sector errors, toss the drive.  Or try to submit an RMA for replacement if it's still under warranty.

Brand new drives can fail the first week after you start using them.  Electronics are not perfect.  Sometimes they last for years or decades.

---

### Post by Mark Uhde on 2012-04-30
> **ahallubuntu said:**
> You probably should have just started a new thread instead of resurrecting an old one.  In any case...

You have a reallocated event count of 4127 - which indicates a serious if not catastrophic drive failure.  Plus 179 pending sectors (which cannot be read).  Most likely the drive surface is failing.  Assuming the drive will be completely dead soon.  It should go without saying that you should have already backed up anything important - if not, better do so NOW before this thing completely dies.

Once you have gotten anything you wanted off of this drive, you can try zeroing it out completely with a program like DBAN ([www.dban.org](www.dban.org)), which is a CD you can download/burn and run to wipe the drive completely.  SOMETIMES a soft error of some sort can cause a few pending sector errors, and zeroing the drive can clear them - but you have a lot of errors, so that seems unlikely.  Still, once you have nothing to lose you might as well try it.  Check S.M.A.R.T. again after running DBAN.  If after that you still have any pending sector errors, toss the drive.  Or try to submit an RMA for replacement if it's still under warranty.

Brand new drives can fail the first week after you start using them.  Electronics are not perfect.  Sometimes they last for years or decades.

The reason I resurrected such an ancient thread is that he had the same exact drive and symptoms, a Google search reveals similar results from many of these drives from the day they're new. I can't find any long-term followup or anyone who has said they've actually had a problem, long-term. It appears that it could be a bug in the SMART logic of the drive model.

---

### Post by ahallubuntu on 2012-04-30
Is there some sort of S.M.A.R.T. controller problem with this Samsung drive so it reports false errors?  If so, I would either look for a firmware upgrade or not use the drive myself.  I would never rely on a drive that reports false S.M.A.R.T. errors.  How am I supposed to know when there are REAL errors?  I use S.M.A.R.T. all the time.

Now, I understand you are trying to salvage a drive on the cheap to save money for a non-profit - I donate my time (and spare computer parts) to non-profits myself.  I can relate.  If you want to confirm your suspicion that this drive is in fact fine and reporting false errors, then I would find some other way (besides S.M.A.R.T.) to test the drive the drive to verify its integrity.  There are drive testing tools.  Does Seagate (new owner of Samsung's hard drive business) offer a diagnostic tool you can use?  Not sure.  You can also try the Ultimate Boot CD (google for it) and run a few tests on it.  

In any case, I have found so many real S.M.A.R.T. errors over the years that turned out to be real drive problems that I would be extremely nervous about this drive.  Even one real pending sector error on a drive can render it unbootable and is enough for me to discard it.  If you are going to use such a drive for a non-profit's computer (supposing you are successful at say installing Ubuntu on it), at best I would use it for a drive that can afford to crash: a workstation that has no real data on it, just a terminal people can use on a network or something.  You would be doing that non-profit a big disservice giving them a failing hard drive that could cause them to lose data and/or time if it ultimately fails completely.

---

### Post by Mark Uhde on 2012-05-01
> **ahallubuntu said:**
> Is there some sort of S.M.A.R.T. controller problem with this Samsung drive so it reports false errors?  If so, I would either look for a firmware upgrade or not use the drive myself.  I would never rely on a drive that reports false S.M.A.R.T. errors.  How am I supposed to know when there are REAL errors?  I use S.M.A.R.T. all the time.

Now, I understand you are trying to salvage a drive on the cheap to save money for a non-profit - I donate my time (and spare computer parts) to non-profits myself.  I can relate.  If you want to confirm your suspicion that this drive is in fact fine and reporting false errors, then I would find some other way (besides S.M.A.R.T.) to test the drive the drive to verify its integrity.  There are drive testing tools.  Does Seagate (new owner of Samsung's hard drive business) offer a diagnostic tool you can use?  Not sure.  You can also try the Ultimate Boot CD (google for it) and run a few tests on it.  

In any case, I have found so many real S.M.A.R.T. errors over the years that turned out to be real drive problems that I would be extremely nervous about this drive.  Even one real pending sector error on a drive can render it unbootable and is enough for me to discard it.  If you are going to use such a drive for a non-profit's computer (supposing you are successful at say installing Ubuntu on it), at best I would use it for a drive that can afford to crash: a workstation that has no real data on it, just a terminal people can use on a network or something.  You would be doing that non-profit a big disservice giving them a failing hard drive that could cause them to lose data and/or time if it ultimately fails completely.

Well, it's just going to be used for a pfSense (FreeBSD-based firewall box) install, so no HUGE deal if it dies dies... they're USED to having no internet days at a time with the cheap consumer-grade routers they've been using. It's going to be a huge step up for them in reliability even IF the drive dies in a few months or something. With that said, I decided to not use the drive....

Because, thanks for the idea - Samsung DOES have a utility (ES-Tool) that's on that CD. I'm running it now, doing a low-level format for curiosity's sake. The drive failed that utility, on it's full scan. For a bad sector. Oddly, the drive's SMART still shows as passed, in that utility and in it's short test again from smartctl. Something's just downright weird with this drive. It didn't fail in the full surface scan, it failed in the final verification step... the full surface scan passed????

Further confirming the idea this drive model is stupid somehow, the reallocation events divided by the drive's power-on hours for the OP's drive works out to 57.8 events/hr. For mine, from the latest data update (more accurate since time's only to the nearest hour), it's 56.19 events/hr. From the data I posted it was 55.77 events/hr. These are all extremely close, though to be fair, rounding of the time alone can't account for the difference. Something's not right here.

Honestly, I think this model drive is just stupid, given the "errors" are so numerous and it's still "passing" it's self-help - the data just doesn't make any sense. But I'm probably not going to trust it at all, even for such a low-risk application.

---

### Post by overdrank on 2012-05-01
> **Mark Uhde said:**
> I hate to bump such an ancient thread, but it's short and hopefully this will help both me and possibly the OP. One, to the OP, I'd love to know the status of that drive now, years down the road.


Mark

Moved to new thread. :)

---

### Post by Mark Uhde on 2012-05-01
> **overdrank said:**
> Moved to new thread. :)

Okay, sorry, I wasn't sure what would be better in this case :) Thanks and in the future I'll make new threads on here when they're ancient!

Anyways, like I said, Ubuntu's dire warning that the drive was failing (plus a desire for more than 160GB anyways) is why the drive was never used. Thanks to ahallubuntu, I found the boot CD with Samsung's ES-Tool. To recap:

1st ran it's self test, it completed the full surface scan and everything all passing and the last step reported a bad sector and told me to erase the drive and try again

2nd did a low-level format, and it told me the drive had no error

3rd re-did the test in step 1 and it told me the drive had no error

here's the smartctl report following step 3 and a reinstall for pfSense 2.1-SNAPSHOT (FreeBSD 8.3):

```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2437
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1735
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       92
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       84
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       56
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       51
194 Temperature_Celsius     0x0022   163   079   000    Old_age   Always       -       25 (Min/Max 8/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4827
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       329
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       843
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0
```

I know some of you now that it's been separated are gonna be like "WTH are you posting this to the Ubuntu forum when you're using FreeBSD on the drive" - well, two reasons. 1. Ubuntu was the OS that warned me the drive was in danger of imminent failure (it's also one of two OSes I use daily - I have a Mac and an Acer with Ubuntu). 2. The OP of the ancient thread I found had a very similar smartctl report from the same model drive, as do a few other people on Google. 

I think I'm going to trust the drive as an experiment but if it ever shows a reallocated sector in the smartctl report, swap it immediately for them.

---

### Post by ahallubuntu on 2012-05-01
You may be confused about the meaning of some of these S.M.A.R.T. status/error columns:

A "Reallocated Sector" is not catastrophic; it means that the drive firmware detected a bad sector and disabled it and replaced it with a "spare."  It's not unusual for older drives to have a couple of these.  It's worrisome you start seeing a lot of them or if the number of reallocated sectors keeps growing - that means the surface is probably failing.  And eventually, your drive will run out of spares.

A "Pending Sector" means that the sector can't be read.  That's really bad if it is a real error.  I will not use a drive with pending sectors except when I really don't care about it - as a junk or experimental drive or something.  Pending sectors bother me much more than reallocated sectors do.

And you still have a pending sector count of 329 sectors?  Wow!

If that 329 number is bogus because there is something wrong with the drive's S.M.A.R.T. monitoring, then you might as well ignore S.M.A.R.T. altogether.  No point in worrying about reallocated sectors since a small number of them aren't fatal anyway - and how would you even know they are real or not?

Besides a low-level format, I highly suggest running DBAN on this drive, to write zeros to every sector.  Then check S.M.A.R.T. again and compare the number of pending sectors to what you had before.  Any change?

Are you running the latest version of smartmontools?  How are you connecting the drive to your system?  Via a USB adapter?  Have you tried connecting it directly to a SATA port on the motherboard instead?

Is there a firmware update available from Samsung/Seagate for this drive?  I know some Samsung drives had had issues in the past that were fixed with firmware updates.  Many drives never have a firmware update released, however.

---

