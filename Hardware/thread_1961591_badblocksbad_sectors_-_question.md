---
title: "badblocks/bad sectors - question"
date: 2012-04-19
forum: Hardware
---

### Post by RememberWhenItRained on 2012-04-19
So, here's the skinny: Have a friends laptop that had a continues BIOS beep when attempting to load Vista (obligatory shudder) on a 'Windows is loading files' screen. Bad HDD, i thought.

Running BIOS run-in scan yielded #10008 - Replace Hard Disk 1 and 303 error. So it seems correct. Ran Windows Recovery, and chkdsk. Then seemed to boot fine. Tried it multiple times.

Gave it back to the friend, and when she shut down and reboot that night, the BIOS beep occurred again.

Ran Oneiric ubuntu from USB drive and ran Disk Utility. SMART status read: Disk has a few bad sectors. Ran diagnostic from Disk Utility and it resulted in a "FAILED: (Read)" output.

Ran badblocks (and output results to txt file) which showed 5 bad blocks. 

Ghosted/Cloned the drive onto an external with Clonezilla. Now i have a few questions:

1. Are bad blocks the same as bad sectors?
2. Bad sectors are physical imperfections on the disk, correct, and thus cannot be fixed?
3. While bad sectors don't necessarily mean a drive's shot, it's best to replace the drive, correct?
4. Data from bad sectors are automatically moved to different, healthy areas of the HDD, correct? If not, how can you pull the data off of the bad sectors?
5. Is there a way to tell the system (maybe using badblocks or e2fsck -c) to not read the bad areas of the HDD?
6. Will wiping the drive, writing over 0s, and then re-cloning from external HDD help? No, because they are physical imperfections, right?
7. Any solution other than getting a new drive?
8. My own HDD also has a few bad sectors and 8 bad blocks. I have never had a problem with my disk though. Should i be concerned/what should i do? Also, mine (unlike my friends') is still under warranty. Would they replace the HDD?

Sorry for the length. Thanks in advance for your replies.

---

### Post by RememberWhenItRained on 2012-04-19
tried running fsck -v /dev/sdb (local HDD) and it resulted in Superblock invalid, trying backup blocks.
Bad magic number in super-block while trying to open /dev/sdb

blah blah

This is probably because the superblock is corrupt or, more likely, it's an NTFS trying to read as an ext2, right? How do i run fsck for NTFS?

---

### Post by ahallubuntu on 2012-04-19
You're right, you can't run fsck on an NTFS partition.  The Windows equivalent is chkdsk, which you've already run.

Badblocks already showed 5 bad sectors.  I use SmartMonTools (GSmartControl) in Linux to check the S.M.A.R.T. status; Badblocks may be doing the same thing, I'm not familiar with it.  In any case, you can use a Parted Magic CD (google for it) which is a handy Linux distro with many disk utilities on it, including GSmartControl.  Boot that CD on her laptop and click on SmartControl and look for Attributes highlighted in red.  I'll guess you see 5 Pending Sectors. (1 pending sector is enough to make a drive unbootable - depends where the sector is on the drive.)

Yes, "blocks" and "sectors" are often used interchangeably. 

In any case - you may have to replace the hard drive.  Instead of cloning her drive, IMAGE it - which is similar to cloning, except it writes the contents of her drive to a big image file instead of taking up the entire drive.  (You can then restore the image to another drive, if need be.)  In Linux, you can use PartImage (included on the Parted Magic CD) or just ddrescue to make an image.

SOMETIMES you can zero out the whole hard drive to clear any bad sectors and then restore the image backup and all will be good - but if there are real surface failures on the drive, you need to replace it.  I use DBAN ([www.dban.org](www.dban.org)) to zero out a drive, then check S.M.A.R.T. again and if all the bad sectors have been cleared I may use it again.  If not, replace the drive.

I would caution you to BACKUP  important files from her drive in addition to making an image backup before you DBAN the drive, since you've never done them before.  Better safe than sorry if you didn't make the image correctly.

As for your own drive: check S.M.A.R.T. on it as well; you can also try DBAN on it as above, but if it's still under warranty, personally I'd copy my data off, DBAN it anyway (don't send a drive with your data back to anyone!), and get a replacement.

---

### Post by RememberWhenItRained on 2012-04-19
> **ahallubuntu said:**
> You're right, you can't run fsck on an NTFS partition.  The Windows equivalent is chkdsk, which you've already run.

Badblocks already showed 5 bad sectors.  I use SmartMonTools (GSmartControl) in Linux to check the S.M.A.R.T. status; Badblocks may be doing the same thing, I'm not familiar with it.  In any case, you can use a Parted Magic CD (google for it) which is a handy Linux distro with many disk utilities on it, including GSmartControl.  Boot that CD on her laptop and click on SmartControl and look for Attributes highlighted in red.  I'll guess you see 5 Pending Sectors. (1 pending sector is enough to make a drive unbootable - depends where the sector is on the drive.)

Yes, "blocks" and "sectors" are often used interchangeably. 

In any case - you may have to replace the hard drive.  Instead of cloning her drive, IMAGE it - which is similar to cloning, except it writes the contents of her drive to a big image file instead of taking up the entire drive.  (You can then restore the image to another drive, if need be.)  In Linux, you can use PartImage (included on the Parted Magic CD) or just ddrescue to make an image.

SOMETIMES you can zero out the whole hard drive to clear any bad sectors and then restore the image backup and all will be good - but if there are real surface failures on the drive, you need to replace it.  I use DBAN ([www.dban.org](www.dban.org)) to zero out a drive, then check S.M.A.R.T. again and if all the bad sectors have been cleared I may use it again.  If not, replace the drive.

I would caution you to BACKUP  important files from her drive in addition to making an image backup before you DBAN the drive, since you've never done them before.  Better safe than sorry if you didn't make the image correctly.

As for your own drive: check S.M.A.R.T. on it as well; you can also try DBAN on it as above, but if it's still under warranty, personally I'd copy my data off, DBAN it anyway (don't send a drive with your data back to anyone!), and get a replacement.

many thanks for your prompt reply. I will try, and if it works, will marked solved.

---

### Post by efflandt on 2012-04-20
Hard drives reserve space to automatically transparently replace bad sectors with good sectors.  If you start actually seeing bad sectors, that is a bad sign that all of the error sites are used up, and if something is destroying sectors, it should not be trusted (can only get worse).

I was trying to image a defective laptop drive (in a USB enclosure) to put on a warranty replacement, and with bad sectors I could not get clonezilla to work, because it does a sector by sector image, and that would fail (halt) when it got to sectors it could not read at all in repeated attempts.  If that did work for sectors that the filesystem had locked out as bad, those would still be locked out from future use if you did a sector by sector clone to another drive.

So I used Western Digital's version of Acronis to create a file by file image file on a USB drive, instead of sector by sector.  That worked to then put that image on the replacement drive and the laptop booted fine.  Seagate also has their version of Acronis for Seagate and Maxtor drives.

---

### Post by RememberWhenItRained on 2012-04-20
> **efflandt said:**
> Hard drives reserve space to automatically transparently replace bad sectors with good sectors.  If you start actually seeing bad sectors, that is a bad sign that all of the error sites are used up, and if something is destroying sectors, it should not be trusted (can only get worse).

I was trying to image a defective laptop drive (in a USB enclosure) to put on a warranty replacement, and with bad sectors I could not get clonezilla to work, because it does a sector by sector image, and that would fail (halt) when it got to sectors it could not read at all in repeated attempts.  If that did work for sectors that the filesystem had locked out as bad, those would still be locked out from future use if you did a sector by sector clone to another drive.

So I used Western Digital's version of Acronis to create a file by file image file on a USB drive, instead of sector by sector.  That worked to then put that image on the replacement drive and the laptop booted fine.  Seagate also has their version of Acronis for Seagate and Maxtor drives.

appreciate your response. Well, I used CloneZilla's -rescue option, which ignores or bypasses bad sectors (instead of halting - it took me three runs to figure that out :/ ) shouldn't this do what Acronis (or comparable utils) do (or do i need to run it yet again, this time with Acronis instead? also, would i need to use ddrescue, as this thread suggests? [http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3536957](http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3536957)

thanks.

---

### Post by RememberWhenItRained on 2012-04-20
0'ed disk and reloaded image on, and ran GSmart again - test said completed without error, however, there looks like a few possible errors upon reading the Smartctl output; namely Airflow Temp_cel reads as 'FAILING NOW'

---

### Post by ahallubuntu on 2012-04-20
So are there any S.M.A.R.T. attributes highlighted in red in GSmartControl?  Any pending sector errors?  How many reallocated sectors?  If there are zero pending or reallocated sectors - and no reallocation events - you might be safe using the disk again in my opinion.  Some people won't ever use a disk again once there are any bad sectors, though.  In my view, as long as you make regular backups and watch the S.M.A.R.T. status, you should be OK.

---

### Post by RememberWhenItRained on 2012-04-20
```
190 Airflow_Temperature_Cel 0x0022   040   031   040    Old_age   Always   FAILING_NOW 60
```

Airflow and temp. (Celsius) were red attributes

under attributes? current pending sector count? says never failed.

As far as reallocated sectors: 0 RAW value but value and worst of 200.
```
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
```

---

### Post by RememberWhenItRained on 2012-04-20
successfully passed GSmartMon Short & Extended Diagnostics, BIOS Run-In test, and chkdsk. I think it's safe...for now... I'll tell her to run semi-regular diagnostics. And backup.

---

### Post by ahallubuntu on 2012-04-20
I don't know what the pending sector count was before (if any) so it's hard to know for sure if anything in S.M.A.R.T. changed.  Ran badblocks again?

The "FAILING NOW" msg for the temperature is odd - suggests the drive might be overheating - or the sensor measure the temp is not working.  Does the drive seem hot?

---

### Post by RememberWhenItRained on 2012-04-20
> **ahallubuntu said:**
> I don't know what the pending sector count was before (if any) so it's hard to know for sure if anything in S.M.A.R.T. changed.  Ran badblocks again?

The "FAILING NOW" msg for the temperature is odd - suggests the drive might be overheating - or the sensor measure the temp is not working.  Does the drive seem hot?

it does, which concerned me. She has a cooling pad, not sure if she uses it for the HP (she uses it for her MacBook) but i will suggest using it on the HP.

will run badblocks again and pull log file from GSmartTools for prelim. HDD test before zeroing to compare values for pending sector count and post back (when the long scans finish.)

---

### Post by RememberWhenItRained on 2012-04-21
> **ahallubuntu said:**
> I don't know what the pending sector count was before (if any) so it's hard to know for sure if anything in S.M.A.R.T. changed.  Ran badblocks again?

The "FAILING NOW" msg for the temperature is odd - suggests the drive might be overheating - or the sensor measure the temp is not working.  Does the drive seem hot?

badblocks yielded 0 errors. Now, to do the same thing with my computer, do i need to do anything special imaging as I am triple booting?

---

### Post by ahallubuntu on 2012-04-21
Glad to hear zeroing out that laptop drive cleared the bad sectors!  I have done that a few times, and I was nervous at first but I've never had a laptop drive that formerly had bad sectors have problems again after clearing them.  Sometimes bad sectors persist after zeroing so you pretty much have to dump the drive (or RMA it if under warranty) at that point.  I have found more than one drive where you can't clear these sectors.  Probably surface failure.

I speculate that laptop drives may be prone to "soft errors" that can cause these pending sector errors that can be cleared.  I've never seen the same on any desktop drive; I've seen plenty of desktop drive pending sector errors but none that could be cleared.  Perhaps it has to do with laptop drives going into standby more often or moving more often whereas your typical desktop drive doesn't  move very often.

If you want to try the same zeroing procedure for your desktop with multiple partitions, all you have to do is make image backups of each partition (except swap).  You can manually re-create the same partition scheme after zeroing out the drive and then copy the partitions back.  (And use the opportunity to resize any partitions you wished you could have sized differently before.)  Note the blkid (UUID) of each partition as it originally was; after you restore you can reset the UUIDs back to original with tune2fs if need be; this will be important for things like /etc/fstab to reference the partitions by UUID plus things like hibernation if you use that now in Linux.  You may need to update grub again afterward anyway with an Ubuntu live CD but that's pretty easy.

A sophisticated imaging tool like True Image may be able to preserve the structure and UUIDs exactly.  You can also use partimage (on the Parted Magic disc if you grabbed that) to save the individual partitions efficiently as files on an external drive.

Just be prepared to RMA this drive if it turns out zeroing did not clear the pending sector errors (double check S.M.A.R.T. before zeroing and check it again after to see what changed).  Some hard drive vendors have a program whereby you can get a replacement drive shipped to you ahead of time by paying a deposit on it (in effect) and then you can ship them the bad drive back after you get the new one - and they'll refund your money assuming you send it back in time as instructed.

---

### Post by RememberWhenItRained on 2012-04-21
> **ahallubuntu said:**
> Glad to hear zeroing out that laptop drive cleared the bad sectors!  I have done that a few times, and I was nervous at first but I've never had a laptop drive that formerly had bad sectors have problems again after clearing them.  Sometimes bad sectors persist after zeroing so you pretty much have to dump the drive (or RMA it if under warranty) at that point.  I have found more than one drive where you can't clear these sectors.  Probably surface failure.

I speculate that laptop drives may be prone to "soft errors" that can cause these pending sector errors that can be cleared.  I've never seen the same on any desktop drive; I've seen plenty of desktop drive pending sector errors but none that could be cleared.  Perhaps it has to do with laptop drives going into standby more often or moving more often whereas your typical desktop drive doesn't  move very often.

If you want to try the same zeroing procedure for your desktop with multiple partitions, all you have to do is make image backups of each partition (except swap).  You can manually re-create the same partition scheme after zeroing out the drive and then copy the partitions back.  (And use the opportunity to resize any partitions you wished you could have sized differently before.)  Note the blkid (UUID) of each partition as it originally was; after you restore you can reset the UUIDs back to original with tune2fs if need be; this will be important for things like /etc/fstab to reference the partitions by UUID plus things like hibernation if you use that now in Linux.  You may need to update grub again afterward anyway with an Ubuntu live CD but that's pretty easy.

A sophisticated imaging tool like True Image may be able to preserve the structure and UUIDs exactly.  You can also use partimage (on the Parted Magic disc if you grabbed that) to save the individual partitions efficiently as files on an external drive.

Just be prepared to RMA this drive if it turns out zeroing did not clear the pending sector errors (double check S.M.A.R.T. before zeroing and check it again after to see what changed).  Some hard drive vendors have a program whereby you can get a replacement drive shipped to you ahead of time by paying a deposit on it (in effect) and then you can ship them the bad drive back after you get the new one - and they'll refund your money assuming you send it back in time as instructed.

thanks so much for your help. I will marked this solved after i finish with my laptop. Prelim. tests (before imaging or zeroing the drive) showed 8 bad blocks and GSmartControl shows Current Pending Sector Count with a raw value of 3 and Offline Uncorrectable with a raw value of 3. Both are highlighted in red.

Also, when trying to image one of the partitions (I chose to save the whole image with Clonezilla rather than individual partitions) there was an error, though i forget what partition it was.
I went ahead and started to reformat the external drive (though i don't think this should be necessary) and will try again. Zeroing 1TB takes forever....:-(

any idea why one particular partition might fail to copy?

---

### Post by ahallubuntu on 2012-04-21
Well, one of the bad sectors is probably in the partition that errored out.  You can try ddrescue to copy it the partition and skip the bad sectors - but it might be best for you first to copy all the FILES you care about with rsync first.  The files that have bad sectors in them will be corrupted and probably unrecoverable.

Partimage might have an option to ignore bad sectors as well - I forget.

Try copying each partition one at a time and figure out which one has errors.  Expect to lose at least one file in that partition if that one has bad sectors.

Also expect that these sectors may not clear after you zero out the drive, so have a plan B ready (RMA and wait for a new drive to arrive and not use your laptop for a while, probably).

---

### Post by RememberWhenItRained on 2012-04-23
[ friend's computer is fixed. on my computer: ]

ran clonezillla again and looked at output. It kept failing at /dev/sda3 (a Win7 partition). It also said fsck was flagged to run on next Windows bootup. I booted in Windows and it autoran fsck which deleted dozens of orphaned files and autorecovered them. Went to fast too tell what they [the files] all were, but there was a lot. Never had that happen before. Thinking (hoping) the problem was fixed, I ran GSmart again and executed a quick test which Failed: Read with only 10% complete. Ran badblocks (post fsck) and output to text file. Yielded 14 bad blocks (which was weird, because i thought i had like 8 the other day.) I output fdisk -l to another txt file and compared them. It yielded some interesting results. I have included a screenshot.

I was trying to see which bad blocks where in which partition. Most were in /dev/sda3, a Win7 partition, but the rest, well - i couldn't seem to find which partition they belong to. It's like there's a gap in blocks with the output of fdisk -l. See if you can make sense of the screenshot. I'm going to reimage my local drive to the external (post fsck) but i'm a little hesitant to DBAN my drive before i figure out what's going on. Ultimately i'll have to do it anyone, and if that doesn't work, as you said, RMA the drive. Most of them are pending sector errors, so as you suggested, I have a feeling DBANing will fix the problem(s).

ETA: added another screencap with values comma 'ed off to make it easier to read. there seems to be a fairly large gap in partition blocks.

---

### Post by RememberWhenItRained on 2012-04-23
It looks like an image is on the external HDD, but i get this message at the end of clonezilla.

```
This program is not started by Clonezilla server, so skip notifying it the job is done.
Finished!
Now syncing - flush filesystem buffers...

Press "Enter" to continue......
```

is it complete or did it hang somewhere?

---

### Post by ahallubuntu on 2012-04-23
I didn't recommend Clonezilla for this - I haven't used it many times so really can't advise you on whether it's a legit copy or not.  Personally, I would not trust it as your *ONLY* copy of your data.

It sounds like you've had more sectors fail.  Each time you run chkdsk (the Windows equivalent of fsck), you put more stress on the disk, reading a bunch of files.  I'd first make absolutely sure you have your FILES backed up - the ones you care about anyway.  Then backup the partitions, if you can.  But you might need to assume you will have to re-install from scratch on a new drive...

---

### Post by RememberWhenItRained on 2012-04-23
> **ahallubuntu said:**
> I didn't recommend Clonezilla for this - I haven't used it many times so really can't advise you on whether it's a legit copy or not.  Personally, I would not trust it as your *ONLY* copy of your data.

It sounds like you've had more sectors fail.  Each time you run chkdsk (the Windows equivalent of fsck), you put more stress on the disk, reading a bunch of files.  I'd first make absolutely sure you have your FILES backed up - the ones you care about anyway.  Then backup the partitions, if you can.  But you might need to assume you will have to re-install from scratch on a new drive...
backing up files now...
yeah, had same thought about more sectors popping up. Seems weird though I can't find locations for some of the bad blocks...

You recommend Acronis instead? (I have a Seagate Momentus)

---

### Post by ahallubuntu on 2012-04-23
Yes, True Image is my first choice - the newer versions can handle ext4 partitions.  I use the "rescue CD" 99% of the time - I just boot it on any system I'm using and use it to save partitions (create images of them).  There is an option to "ignore errors" during an image backup I think so you don't have to hit "Ignore" each time an error is found during a copy.

There may be a version of True Image that's free for you Seagate drive - not sure.

Second choice would be partimage which is open source and included on the Parted Magic CD.  I have used partimage a few times and it has worked for me.  It originally didn't work on ext4 partitions but I think newer versions do.  Not sure.

IF Clonezilla supports saving partitions (as images) to files (does it? Haven't used it in a while), you could continue to use that - but I just can't personally recommend it from recent experience.  I don't recommend cloning an entire disk from your original to a an external disk - if that's what you have already been doing.  Whatever you use, I'd hope the partition backups will work when you eventually restore them, but if not...you've got your files backed up at least, right?  Then just re-install.

I keep image backups before drives start to fail, so if there's a catastrophe I can restore an image that's a month old instead of completely starting over.

---

### Post by RememberWhenItRained on 2012-04-24
> **ahallubuntu said:**
> Yes, True Image is my first choice - the newer versions can handle ext4 partitions.  I use the "rescue CD" 99% of the time - I just boot it on any system I'm using and use it to save partitions (create images of them).  There is an option to "ignore errors" during an image backup I think so you don't have to hit "Ignore" each time an error is found during a copy.

There may be a version of True Image that's free for you Seagate drive - not sure.

Second choice would be partimage which is open source and included on the Parted Magic CD.  I have used partimage a few times and it has worked for me.  It originally didn't work on ext4 partitions but I think newer versions do.  Not sure.

IF Clonezilla supports saving partitions (as images) to files (does it? Haven't used it in a while), you could continue to use that - but I just can't personally recommend it from recent experience.  I don't recommend cloning an entire disk from your original to a an external disk - if that's what you have already been doing.  Whatever you use, I'd hope the partition backups will work when you eventually restore them, but if not...you've got your files backed up at least, right?  Then just re-install.

I keep image backups before drives start to fail, so if there's a catastrophe I can restore an image that's a month old instead of completely starting over.

Yes, clonezilla supports saving partition images to files. It also uses partclone as part of the program. I think True Image might be on PartedMagic, or no?

---

### Post by ahallubuntu on 2012-04-24
No, True Image is not free software and is not on Parted Magic (which is a Linux distro collecting free software). However, Seagate's Seatools (or one of the boot discs) might actually be a branded version of True Image - I'm not quite sure. 

But if you're using Clonezilla and it's working out for you, I'd probably just use it now to save partitions.

---

### Post by RememberWhenItRained on 2012-04-26
badblocks, GSmartControl, and Disk Utility came out clean.

Marked as solved. Thanks for your help.

---

