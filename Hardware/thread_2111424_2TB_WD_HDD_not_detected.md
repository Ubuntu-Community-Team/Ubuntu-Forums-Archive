---
title: "2TB WD HDD not detected"
date: 2013-02-01
forum: Hardware
---

### Post by TyBlood13 on 2013-02-01
My mother's 2TB Western Digital HDD somehow unmounted itself in Windows, so I put it in my Ubuntu machine to see if I could save it as she tried some partion remounter and it failed but stated the data was still there.
My BIOS for my Ubuntu 12.10 machine detects it, but the OS doesn't
Tried finding it with "sudo blkid" no luck.
Please help me, as my mother's entire photo collection is on it, and if I can't save that she'll kill me.

---

### Post by ahallubuntu on 2013-02-01
Hard drives fail and get corrupted all the time and people lose their precious data.  Why should she blame you if she didn't make backups?

In Ubuntu, you might check the S.M.A.R.T. status of the drive.  You can install GSmartControl.  Then check the Attributes tab and look for any Attributes highlighted in pink.  If none are highlighted, the drive probably hasn't experienced a catastrophic failure, perhaps just a filesystem corruption.

Next, try this in a terminal:

```
sudo fdisk -l
```

Does the 2TB show in there?  It will probably show up as /dev/sdb if Ubuntu is seeing it at all.

If /dev/sdb is recognized but no partitions are found, you could try testdisk (program) to see what might be found on it and recovered.  Running a chkdsk in Windows might be wise, too (perhaps by booting a Windows CD).

---

### Post by TyBlood13 on 2013-02-01
> **ahallubuntu said:**
> Hard drives fail and get corrupted all the time and people lose their precious data.  Why should she blame you if she didn't make backups?

In Ubuntu, you might check the S.M.A.R.T. status of the drive.  You can install GSmartControl.  Then check the Attributes tab and look for any Attributes highlighted in pink.  If none are highlighted, the drive probably hasn't experienced a catastrophic failure, perhaps just a filesystem corruption.

Next, try this in a terminal:

```
sudo fdisk -l
```Does the 2TB show in there?  It will probably show up as /dev/sdb if Ubuntu is seeing it at all.

If /dev/sdb is recognized but no partitions are found, you could try testdisk (program) to see what might be found on it and recovered.  Running a chkdsk in Windows might be wise, too (perhaps by booting a Windows CD).
I've now run GSmart Control and in Attributes IDs #s 5, 196, & 197 are pink, which are Reallocated Sector Count, Reallocation Event Count, & Current Pending Sector Count, respectively.  Now what?

---

### Post by ahallubuntu on 2013-02-01
> **TyBlood13 said:**
> I've now run GSmart Control and in Attributes IDs #s 5, 196, & 197 are pink, which are Reallocated Sector Count, Reallocation Event Count, & Current Pending Sector Count, respectively.  Now what?

Now you tell your mom the hard drive is failing (not a corruption) and that it may not be possible to get any data off of it - not without paying a lot to a data recovery service.  Explain to her that hard drives are mechanical devices that fail all the time, sometimes without warning, which is why people who have themselves lost data this way (like me) tell people to MAKE BACKUPS to anyone who will listen.

Still, I'd probably run chkdsk in Windows.  It might fix the file system enough to get some data off.  There are also other tricks.  There is some tool out there that will try re-reading the same sector over and over again perhaps for days and apparently this tool can recover some data.  Sorry, you'll have to do some research on that - I haven't tried such tools myself, might have years ago had I known about them.

Read up on chkdsk.  chkdsk /r will attempt surface recovery of these sectors and could take a VERY long time (overnight or longer, so be prepared for that).  Without /r will take less time but may not work.

(If you don't have a Windows disc to boot you can download a Windows 7 disc from Softpedia - google for it - it will work for any version of Windows older than Windows 7 for this sort of thing.  You want to drop into a "command prompt" after you boot it.)

The point is, you may be beyond the typical "data recovery" you can do simply by plugging the drive into another computer and copying the data off.  Corruptions can be recovered from to some extent by an average user (using testdisk, etc.) but hardware failures make things much more difficult.  That's why services exist that charge hundreds or thousands of dollars to recover data from failed drives.

How many Pending Sectors are we talking about?  What's the RAW value? If you have one or two, there's some hope chkdsk can recover stuff.  If you have hundreds of Pending Sectors...well, good luck with that.   (Reallocated Sector are different - they are the number of failed sectors ALREADY replaced with working spares by the drive's firmware, until the drive runs out of spares.  Pending means those sectors STILL can't be read, so any file that has that sector it it can't be read.)

Please forgive the somewhat snide tone above - I have been telling people for years, over and over and over and over again, how important it is to make backups because these things happen to hard drives and some people STILL don't get it.  I know it's your mom's drive not yours and you're just trying to help, but I still get frustrated hearing stories like this.  I hope you get lucky and get some stuff back!

---

### Post by TyBlood13 on 2013-02-02
> **ahallubuntu said:**
> Now you tell your mom the hard drive is failing (not a corruption) and that it may not be possible to get any data off of it - not without paying a lot to a data recovery service.  Explain to her that hard drives are mechanical devices that fail all the time, sometimes without warning, which is why people who have themselves lost data this way (like me) tell people to MAKE BACKUPS to anyone who will listen.

Still, I'd probably run chkdsk in Windows.  It might fix the file system enough to get some data off.  There are also other tricks.  There is some tool out there that will try re-reading the same sector over and over again perhaps for days and apparently this tool can recover some data.  Sorry, you'll have to do some research on that - I haven't tried such tools myself, might have years ago had I known about them.

Read up on chkdsk.  chkdsk /r will attempt surface recovery of these sectors and could take a VERY long time (overnight or longer, so be prepared for that).  Without /r will take less time but may not work.

(If you don't have a Windows disc to boot you can download a Windows 7 disc from Softpedia - google for it - it will work for any version of Windows older than Windows 7 for this sort of thing.  You want to drop into a "command prompt" after you boot it.)

The point is, you may be beyond the typical "data recovery" you can do simply by plugging the drive into another computer and copying the data off.  Corruptions can be recovered from to some extent by an average user (using testdisk, etc.) but hardware failures make things much more difficult.  That's why services exist that charge hundreds or thousands of dollars to recover data from failed drives.

How many Pending Sectors are we talking about?  What's the RAW value? If you have one or two, there's some hope chkdsk can recover stuff.  If you have hundreds of Pending Sectors...well, good luck with that.   (Reallocated Sector are different - they are the number of failed sectors ALREADY replaced with working spares by the drive's firmware, until the drive runs out of spares.  Pending means those sectors STILL can't be read, so any file that has that sector it it can't be read.)

Please forgive the somewhat snide tone above - I have been telling people for years, over and over and over and over again, how important it is to make backups because these things happen to hard drives and some people STILL don't get it.  I know it's your mom's drive not yours and you're just trying to help, but I still get frustrated hearing stories like this.  I hope you get lucky and get some stuff back!
Sigh... Well, thank you for your help. I'll run chkdsk /r in the morning and report back whenever it finishes.

---

### Post by Mark Phelps on 2013-02-03
Sigh ... you do NOT have to pay a fortune to a data recovery service unless you FIRST use a premier Windows-based data recovery app and find that does NOT work.

You should read through the following before you give up on recovery:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

