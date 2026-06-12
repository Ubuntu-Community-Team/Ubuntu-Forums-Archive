---
title: "What cuases bad sectors to start and spread rapidly?"
date: 2012-03-13
forum: Hardware
---

### Post by NaturistGirl on 2012-03-13
A few days ago (I think it was Thursday or Friday morning). I checked the disk and it said it was healthy, and then notice it said it had some bad sectors on it. So I kept an eye on it, and notice that it gains at least a few hundred a day, since Thursday or Friday, it now has over 22,000 bad sectors.

When I used to boot up, I noticed an error (haven't seen it, since I did updates on Friday). It said something like can't find disk DIUU or something like that. It was 4 letters with UU at the end. My computer would sill boot up fine though, but I would get a pop up (and still do\0 of a system error.

I have not had this happen before. This laptop is less then a year old. The HDD is 1.5TB.

Here is a screenshot:
[http://i41.tinypic.com/34nl2bp.png](http://i41.tinypic.com/34nl2bp.png)

~ Lexi

---

### Post by ahallubuntu on 2012-03-13
Hard drives can and do fail all the time, sometimes after a few days or weeks of operation, sometimes after many long years of service.  The reason they fail at different times is due to imperfections in the manufacturing process: some drives are more "defective" than others coming out the door, even though they've met the manufacturer's tests.

Also, drives are used differently by different users.  Calendar time doesn't mean a lot in terms of hard drive life.  What matters more is how long you use it and how.  If your computer is on 24/7 and being heavily used much, that's much worse for the drive than one that is used once a month for an hour to make a backup.  People can also abuse drives by moving the computer or drive while it is still in use.

Once the surface of the drive experiences a failure, I would not be surprised to see problems spread very rapidly.

I always assume every hard drive I am using could fail without much warning, so I keep backups of everything important on at least two separate devices.  I recently sent a 2TB Western Digital drive that was under a year old because of a few bad sectors (may potentially have been due to a bad power supply but I wasn't taking chances).  

In your case, looks like you have 66 reallocated sectors.  Reallocated sectors are sectors that were replaced by spares on your drive, but the drive has only a certain number of spares.  When enough sectors fail, you'll run out of spares and then the drive is junk.   No drive I'm aware of has 22,000 spare sectors - that's just an anomaly in the report I think.

I'd still plan to replace that drive but first BACKUP EVERYTHING ASAP if you haven't already.  if still under warranty, after you make your backup send it back to the manufacturer for replacement.

---

### Post by winh8r on 2012-03-13
EDIT***** +1 to the above suggestion, mine is applicable as an alternative but DO back up your data to an external device, whatever you decide to do.





You could try booting from a Ubuntu Live CD and running this command from the terminal:

```
sudo e2fsck -C0 -p -f -v /dev/sdb
```

where /dev/sdb is the name of your hard disk (you can find it in the top right hand corner of the Disk Utility application main window)

this will run a thorough check and repair of the filesystem and tell you what it is doing. It might take quite a while to run so it is probably best done overnight with the machine disconnected from the internet and plugged in to an AC Mains supply.

Hope this helps.

---

### Post by Mark Phelps on 2012-03-14
Looks like you're using a Seagate drive -- which I've found to be quite reliable.  So, it surprising that it's failing so soon.  I've had some WD drives fail in only a few months of use, but not Seagate.

You can use Clonezilla to make a "clone" of your drive onto another of the same size.  I would consider doing that as soon as you can, as increasing bad sector count is an indication of a failing drive.

---

### Post by SlugSlug on 2012-03-14
> **Mark Phelps said:**
> Looks like you're using a Seagate drive -- which I've found to be quite reliable.  So, it surprising that it's failing so soon.  I've had some WD drives fail in only a few months of use, but not Seagate.

You can use Clonezilla to make a "clone" of your drive onto another of the same size.  I would consider doing that as soon as you can, as increasing bad sector count is an indication of a failing drive.

Odd really I swear by WD, got some still running in my current sys from years back

---

