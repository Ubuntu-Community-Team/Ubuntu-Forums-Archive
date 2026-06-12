---
title: "A question about 'bad sectors'"
date: 2012-07-30
forum: Hardware
---

### Post by Musicmaker384 on 2012-07-30
When I use Disk Utility, SMART tells me that my 750gb Hard Disk has 'A Few Bad Sectors.' The light is green and I get no warning that the disk is failing, but there are a few warnings in the 'Attributes' section - two of them - 'Reallocated Sector Count' and 'Current Pending Sector Count.' I'm not worried about that as my computer runs fine on Ubuntu 12.04 and Windows 8 RP. What worries me is that when I try to run a SMART self-test, I get a 'FAILED (Read)' error. From my perspective, my computer runs flawlessly. So my question is simply, is this something I *should* be concerned about, or am I worrying over nothing? Thanks for the help.

Kyle

---

### Post by ahallubuntu on 2012-07-30
You should be extremely worried about pending sectors.  If any of those sectors happens to be in a file anywhere on your disk, that file is now CORRUPT.  Most people don't like having files corrupted.  Have you checked every file on your hard drive to make sure it isn't corrupt?  Try running e2fsck on EXT partitions; try running chkdsk (in Windows) on Windows partitions.  Pay careful attention to the results - pipe them to log files to see what files might have been corrupted.

A "pending sector" means that a that sector could not be read.  Yes, it could be a very serious problem.  The sector may not yet be in a file (if you are lucky) - but even if the sector is in some unused area of the drive, an operating system could try to use it...and that's when you experience freezes and slowness issues.

"Reallocated sectors" are less severe.  They mean that sectors have ALREADY been marked "bad" by the drive's firmware and been replaced with spares.  Every modern drive has some spare sectors (maybe a few hundred, give or take).  It's not a good thing if you start seeing sectors marked bad and reallocated into spares, but it's not necessarily catastrophic, because you haven't necessarily lost any data as you might with pending sectors (that haven't yet been marked "bad" by the drive firmware - just "can't access").  It's not that uncommon to have a few reallocated sectors on an old drive - and if that number doesn't increase, don't worry about it as long as you are making regular backups and are more cautious about using this drive.

The fact that you have both types of bad sectors is potentially bad news - it means some sectors have failed and others are on the way.  It should go without saying that you should backup any important data off this drive immediately if you hadn't already.  At that point, it's probably best just to replace the drive unless you don't much care about what happens on this computer (some people have spare computers that are used like terminals with no real data on them, so a disk failure is inconvenient, not a catastrophe).  It's POSSIBLE you could then write zeros to the current/failing drive and try to clear those pending sectors - I have done that a few times.  Sometimes it works, sometimes it doesn't.  If it works, you have a spare drive you could use for testing or emergencies.  If it doesn't work, recycle the drive.

---

### Post by Musicmaker384 on 2012-07-30
Wow, I was kind of hoping for a reply that would make me sweat a little less.

But I understand. I don't know how this happened; I know bad sectors are caused by physical damage to the drive and I've never done anything to cause that, but I'll start looking for a new drive. Nothing on this computer is important as I've already reinstalled both Ubuntu and Windows numerous times. A backup won't be necessary. I will try running chkdsk and e2fsck, though. It's odd, because the last time I ran chkdsk, it said the drive checked out okay. But thanks for your advice, I'll get a new hard drive if necessary.

---

### Post by ahallubuntu on 2012-07-31
Hard drives fail all the time even if they have not been externally damaged.  They have moving parts and get hot; they fail, sooner or later.  Some drives become obsolete before they fail, others fail early and take your data with them.  I've replaced lots of failed hard drives, most of them presumably that had not been mistreated by their owners.  Sometimes you have to lose some data to take this really seriously.  Then you get paranoid and have a pragmatic backup strategy that ASSUMES hard drive failure - and when it happens, you are prepared to replace them without much disruption.

Backups are crucial, but regular S.M.A.R.T. monitoring can give early warning of creeping problems, as it has for you.

---

