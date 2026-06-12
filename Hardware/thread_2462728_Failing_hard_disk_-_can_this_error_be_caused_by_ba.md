---
title: "Failing hard disk - can this error be caused by bad sata connection?"
date: 2021-05-26
forum: Hardware
---

### Post by mastablasta on 2021-05-26
the new UEFI found this, previous BIOS never complained. so i ran smartmontools in KDE partition manager-

> 
[TABLE]
[TR]
[TD]SMART status:[/TD]
[TD]BAD[/TD]
[/TR]
[TR]
 [TD]Model:[/TD]
 [TD]WDC WD10EARS-00Y5B1[/TD]
 [/TR]
[TR]
 [TD]Serial number:[/TD]
 [TD]WD-WCAV5E015619[/TD]
 [/TR]
[TR]
 [TD]Firmware revision:[/TD]
 [TD]80.00A80[/TD]
 [/TR]
[TR]
 [TD]Temperature:[/TD]
 [TD]41,000000° C / 105,800000° F[/TD]
 [/TR]
[TR]
 [TD]Bad sectors:[/TD]
 [TD]2.265[/TD]
 [/TR]
[TR]
 [TD]Powered on for:[/TD]
 [TD]199591339:38:33[/TD]
 [/TR]
[TR]
 [TD]Power cycles:[/TD]
 [TD]3.016[/TD]
 [/TR]
[TR]
 [TD]Self tests:[/TD]
 [TD]Success[/TD]
 [/TR]
[TR]
[TD]Overall assessment:[/TD]
[TD]Disk failure is imminent. Backup all data![/TD]
[/TR]
[/TABLE]

[COLOR=#ff0000]***these are just values where the test failed or is suspicious***[/COLOR]

       [TABLE]
[TR]
[TD]**5 Reallocated Sectors Count**
[FONT=Noto Sans]Count  of reallocated sectors. When the hard drive finds a  read/write/verification error, it marks this sector as "reallocated" and  transfers data to a special reserved area (spare area).[/FONT]
[/TD]
[TD]Pre-Failure[/TD]
[TD]Online[/TD]
[TD]48[/TD]
[TD]48[/TD]
[TD]140[/TD]
[TD]0x0000000004bb[/TD]
[TD]failing[/TD]
[TD]1211 sectors[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD]197[/TD]
[TD]**Current Pending Sector Count**
[FONT=Noto Sans]Number of "unstable" sectors (waiting to be remapped, because of read errors).[/FONT]
[/TD]
[TD]Old-Age[/TD]
[TD]Online[/TD]
[TD]194[/TD]
[TD]194[/TD]
[TD]0[/TD]
[TD]0x00000000041e[/TD]
[TD]warning[/TD]
[TD]1054 sectors[/TD]
[/TR]
[/TABLE]


can this error be caused by bad connection or is it really a hard disk?

this is WD Green disk i used for static data. new pictured & videos from phone - i would just move them there and leave it. linux iso images were downloaded on another drive then moved over. it was hard ever mounted since 2019 when i moved to linux. i have all this data backed up, but i made another copy now just to be sure.

what i need to know if disk is really failing. then it means i need to exchange it. but if this can be caused by bad connection, then i need to redo connection (since i just moved the disk to new frame and motherboard.

---

### Post by TheFu on 2021-05-26
> can this error be caused by bad connection or is it really a hard disk?
Those errors above are from the disk. It is dying and you are losing data already based on the pending sector count. There aren't any more reserved sectors available to hold the data from the dead sectors.

Cable errors show up as read errors.

Hope backups exist from a mount ago. It has likely been losing data at least that long. No way to know which files or how long the issues have been happening, unless SMART tests are run on a schedule, say weekly.  Then smartctl has a summary.

---

### Post by mastablasta on 2021-05-27
ah ok. i will unplug it then. thanks.

we have it backed up on server, DVD, another PC and on an external hard disk. and i made another copy now. data is quite static.  i did not see any major delays or issues when reading from it.

---

### Post by TheFu on 2021-05-27
Did you run a **long** test using **smartctl** then look at the results?
Don't trust the GUI to provide all the information.

---

### Post by rsteinmetz70112 on 2021-05-27
I worry that running a long test on an already failing disk will hurry the ultimate failure.
I's get a new disk ASAP. 
If you have good backups great, if not ddrescue may be able to recover some of the failing sectors.

---

### Post by TheFu on 2021-05-27
> **rsteinmetz70112 said:**
> I worry that running a long test on an already failing disk will hurry the ultimate failure.
I's get a new disk ASAP. 
If you have good backups great, if not ddrescue may be able to recover some of the failing sectors.

Good point.  I've been automatically running weekly "short" tests and monthly "long" tests on all the storage devices here for so long, I just go look at the directory with that data whenever needed/wanted and find 6-months worth.

ddrescue isn't likely to restore any failing sectors, but it might get some of the data to another disk. ;)   There is a theory that badblocks can write 0s to a bad block and somehow that might restore it.  I've never seen it myself, but many people claim that works.  In general, I find that before data gets too stale, as seems to happen with that "other OS", I've already wiped my disk and performed a fresh install.  Perhaps exercising the disk, as a good backup/restore would accomplish can be sufficient to keep spinning rust (non-SSD HDDs) working fine?  Every time we attempt a read, we give the disk hardware an opportunity to get the data and notice that something bad has happened.  Every write to the same/new sector provides a refresh for the bits.  The CoW file systems like ZFS should have a data longevity edge due to that method, perhaps?

The more automatic and often we are doing backups, the less likely we are to need them, I believe.  Plus, sleeping well at night, never worried about some massive data updates disappearing that day is priceless.

---

### Post by Raymond Day on 2021-06-01
You could run [spinrite]("https://www.grc.com/sr/spinrite.htm") on it. It fixed a lot of drives for me but cost about $100. It is all in machine language and he is making a new one right now should be done soon. If you buy this one can upgrade for free when the new one comes out.

Then can copy the drive because it could go bad again.

-Raymond Day

---

