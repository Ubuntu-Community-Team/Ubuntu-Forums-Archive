---
title: "usb hdd slow transfer"
date: 2012-11-16
forum: Hardware
---

### Post by Facundo_Ruiz on 2012-11-16
Hi!

I'm running Ubuntu 12.04 LTS, and using an usb hdd(Western Digital My Passport, 500gb, ext3).
The problem I have it's that when i'm making any transfer the disks starts to go slower after a few MB. At a speed of 1 MB/s.

At firts i thought that it could be a problem of incompatibilities between USB SS and USB 2.0 or something like that.

I saw that [someone else had a similar problem]("http://ubuntuforums.org/showthread.php?t=2017540") in the forum. 
GSmartControl prints the attached log.

thank you in advance!
Facundo.

---

### Post by ahallubuntu on 2012-11-16
[COLOR="Red"]197 Current_Pending_Sector  0x0032   200   193   000    Old_age   Always       -       **53**[/COLOR]

53 pending sectors (can't be read) is very bad news.  The drive has probably had it.  If you haven't already backed up anything important on this drive, do so ASAP if you still can.  If those 53 sectors are in files, those files will have been corrupted, probably no recoverable.

If you have important files on this that you MUST have, you can try a few tools like ddrescue to try to access them.  There are some tools that will try for days to read the same sector to try to recover unreadable files...

Once you have copied off everything you cared about, you can try zeroing out the whole drive and hope that clears the pending sectors.  I have seen it happen with laptop drives more than once (a portable USB drive is a laptop drive).  Some would say to junk such a drive even if you clear those sectors, but I have had good luck using drives that were cleared up that way without future issues.  I've always assumed they were a kind of "soft" error.

I use the DBAN tool to zero out drives.  It will take some time, perhaps a few hours.  Formatting the drive isn't the same thing.

If after zeroing out the whole drive those pending sectors are still there, time to recycle the drive and get a new one.  Hard drives fail all the time.  It happens.

---

