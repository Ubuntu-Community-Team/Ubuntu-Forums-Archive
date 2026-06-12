---
title: "files gone missing from mounted ntfs drive"
date: 2013-01-11
forum: Hardware
---

### Post by Haur on 2013-01-11
Hi.

So i was just going to add some files to my external hdd but then something went terribly wrong. Yesterday adding files seemed to go just fine but this time after i started trying to copy to the hdd i first got an error telling my the directory was invalid or there was no such file\directory. Then things just got worse because every file inside the directory i was trying to copy to has gone missing as well.

I really ain't got a clue what could be going on or how i can recover the files that went missing. The only thing i've tried so far so checking for recoverable files using ntfsundelete but it didn't show any of the files that went missing, just some older stuff that i had deleted a long time ago.

If anybody could help me out then that would be great.

Edit:
Disk useage analyser seems to indicate that the space is still filled with data but gives some sort of error. "Error when getting information for file '/media/hugstari/backup/Barnamyndir/Rasmus Klumpur og félagar nr2': Input/output error" is what it tells me. This was one of the new directories i was trying to copy.

---

### Post by ahallubuntu on 2013-01-11
It sounds like one of your drives is having an issue.

Is the external drive really a "portable" drive with only a USB cable for both power and data?  Or does it have its own power supply?  If it's a portable drive, perhaps the USB port doesn't have enough power to power the drive.

Check the S.M.A.R.T. status of each drive - use GSmartControl.  Any Attributes in red?

For NTFS drives, once you are confident they are properly working/powered, try running Windows chkdsk, perhaps by booting a Windows disc.

---

### Post by Haur on 2013-01-13
The drive does have it's own power supply. The drive does not give any SMART status, probably cause it doesn't support it.

The device housing the drive connects to the television and plays media from the drive and when i browse to the "missing" directory everything seems to be fine. Still nothing shows up when i connect the drive to the computer.

---

### Post by oldfred on 2013-01-13
Is drive FAT32 and you tried to copy a movie/file over 4GB? 

FAT32 has a max of 4GB for any one file. And since it does not have a journal like NTFS chkdsk will take a lot longer. But some external devices (like your TV?) may only work with FAT32. But otherwise NTFS is better for compatibility and of course since we are Linux we think our Linux formats are better still. :)

---

### Post by Haur on 2013-01-13
No the drive is formated as NTFS.

---

### Post by ahallubuntu on 2013-01-13
You may need to add options to smartctl to check S.M.A.R.T. on a USB-connected drive .

The most common options are

-T permissive

and

-d sat

(you can add both in GSmartControl too).

This may give further options:

[http://sourceforge.net/apps/trac/smartmontools/wiki/USB](http://sourceforge.net/apps/trac/smartmontools/wiki/USB)

I'd still try to check S.M.A.R.T. just to make sure no major errors or Attribute issues have been recorded.

And again, if no S.M.A.R.T. issues, do a chkdsk with a Windows disc or by connecting to a Windows computer.

---

### Post by Haur on 2013-01-19
```
xxx@xxxx:~$ sudo smartctl -T verypermissive -d scsi -i -H -c /dev/sdb 
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-21-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Vendor:               WDC WD32
Product:              00JB-00KFA0     
Revision:             08.0
User Capacity:        320,072,933,376 bytes [320 GB]
Logical block size:   512 bytes
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page
```Still not getting a smart status from the drive. And getting errors ramdomly if i try to copy more data to it. This is the error i get:
"Error splicing file: Input/output error"

Any ideas for restoring the folders that have gone missing?

This might hold a answer
[http://ubuntuforums.org/showthread.php?t=1500384](http://ubuntuforums.org/showthread.php?t=1500384)

---

### Post by Mark Phelps on 2013-01-20
I used to be a really BIG supporter of WD drives -- until last year, I had three drives fail on me -- and one was only a few months old.

What I suggest, if you can connect this drive to a Windows PC, is to go to the WD website, download and install their drive testing utility -- and run that against this drive.

In the cases of the WD drives that failed me, in all the cases, that utility stopped part way through claiming there were too many failures on the drive.

As you can guess, I don't buy WD drives anymore.

---

