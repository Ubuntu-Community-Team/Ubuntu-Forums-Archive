---
title: "Issue with WD External"
date: 2012-08-29
forum: Hardware
---

### Post by VXxed on 2012-08-29
Hey everyone. So I have an issue with an external HD from WD, the WD Elements 2TB External. The issue is that after some amount of time (roll a die, anywhere between 2 days and 6 months) the HD will crap out. In windows, these are my symptoms:

Doesn't show up in My Computer
Device name changed in the Disk Management tool and the Device Manager to "WD Ext HDD 1021" from whatever brand-named thingy it used to be
When you open up Disk Management, the drive is unallocated and says it needs to be initialized. When you try to initialize it with either NTFS or GPT (I can't remember the actual acronym, but it's something like GPT) it just says access denied. At some point it also said that the drive was write protected.

Here's a detailed log of what I've done in another forum..where so far help is scarce.
[http://forums.majorgeeks.com/showthread.php?t=265042](http://forums.majorgeeks.com/showthread.php?t=265042)

So, remembering my experience with modifying HDD's in Ubuntu, I'm trying to remove the write protection on the drive. Booted Ubuntu 12.04 from a flash drive as a live installation, and when I ran gparted from the terminal, I saw this:
```
======================
libparted : 2.3
======================
Input/output error during read on /dev/sdc

```/dev/sda is my laptop's HD, /dev/sdb is the flash drive, and /sdc  is the broken one.

Any ideas? This is new territory I'm stumbling into here.

---

### Post by TheFu on 2012-08-29
What file system(s) are on the drive?  Have you run **fsck** to clear up any dirty journals for Linux partitions?

USB2 or USB3?

What does dmesg say? Could it be a USB hub issue?

If this is windows only, run chkdsk and scandisk. That's the end of my knowledge there for free tools.

---

### Post by ahallubuntu on 2012-08-29
Check S.M.A.R.T. status of the drive with GSmartControl.  You can install this in a live Ubuntu session as long as you are on the internet to download/install the packages you need.  See if any Attributes are highlighted in red.  Sometimes there will be trouble accessing external hard drives with GSmartControl - you may need to add parameters like -d sat or -T permissible to get it to work.

You can also try booting a diagnostic CD from WD and boot that to test the drive.

It could be the drive has simply failed and needs replacement.  Hard drives fail all the time.  Is it under warranty?

---

### Post by VXxed on 2012-08-30
> **TheFu said:**
> What file system(s) are on the drive?  Have you run **fsck** to clear up any dirty journals for Linux partitions?

USB2 or USB3?

What does dmesg say? Could it be a USB hub issue?

If this is windows only, run chkdsk and scandisk. That's the end of my knowledge there for free tools.

In  order: I have no idea what fsck is or does (my knowledge of linux is  limited to vaguely remembering what it takes to install a windows  installer disc onto the internal HD in order to install windows from  boot).  Here's the result of fsck:
```
root@ubuntu:/home/ubuntu# fsck /dev/sdc
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc
Could this be a zero-length partition?

```

USB2. This laptop is a T60 from I think 2005 or earlier, I don't think USB3 was even around yet.

What should I type for dmesg specifically to get the info from the USB?

It's  across all OS's, all computers. chkdsk, as far as I could figure, I  couldn't point to scan the external HD, only the local drive that the OS  is installed on.

[quote=ahallubuntu]Check S.M.A.R.T. status of the drive with GSmartControl.  You can  install this in a live Ubuntu session as long as you are on the internet  to download/install the packages you need.  See if any Attributes are  highlighted in red.  Sometimes there will be trouble accessing external  hard drives with GSmartControl - you may need to add parameters like -d  sat or -T permissible to get it to work.

You can also try booting a diagnostic CD from WD and boot that to test the drive.

It could be the drive has simply failed and needs replacement.  Hard drives fail all the time.  Is it under warranty?[/quote]I'm trying to do it from the Live USB, but it won't install gsmartcontrol. I just finished installing ubuntu 12.04 over my Win8, so I'll see what it can tell me.

I'm not sure if they have a diag CD, but I'll look into it once I'm restarted.

It's absolutely possible, and if anything is likely. But I wanna exhaust every possible option first, because that's a half filled 2 TB drive that I'd like to make functional again. Also, it'd be pretty cool if I could fix an issue that WD hasn't fixed in over two years.

---

### Post by VXxed on 2012-08-30
I'm attaching the log from GSmartControl, I'm not sure what I'm looking at here, hopefully someone can tell me if this is a total failure or still something fixable.

---

### Post by ahallubuntu on 2012-08-30
From your log:

```
197 Current_Pending_Sector  0x0032   196   196   000    Old_age   Always       -       1418
```

1418 bad sectors, which is catastrophic.  Either return the drive under warranty to WD for replacement, or throw it in the trash.  You will never use it again.

---

### Post by VXxed on 2012-08-30
> **ahallubuntu said:**
> From your log: 1418 bad sectors, which is catastrophic.  Either return the drive under warranty to WD for replacement, or throw it in the trash.  You will never use it again.Well that blows all the chunks. Thanks a lot for the help ahallubuntu.

---

### Post by VXxed on 2012-08-30
How do I mark the thread closed?
Edit: Nevermind, found it.

---

