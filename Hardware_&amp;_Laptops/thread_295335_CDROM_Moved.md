---
title: "CDROM Moved"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by SonWon on 2006-11-07
Today I replaced a defective CDROM drive in my laptop.  Now the CDROM is showing as /dev/hdd from the Disks Manager.  Before it was /dev/hdc in the Disks Manager.  Does anyone know what is wrong?  The Disks Manager is showing a hard disk at /dev/hdc but it appears to be a ghost?

Also the new CDROM does not show up in the BIOS but does work with nautilus and burner software?

Thank you for help,
SonWon

---

### Post by SonWon on 2006-11-09
Posting here for the next user with this question.

Okay, I fixed the problem.  Kind of a long story.  First a little history.  Laptop drives are a mess.  Some laptops only have one IDE channel.  This is done to cut cost, I think.  The BIOS in many laptops will only look for a master device so slave devices are not found.  My laptop will only look for the master.  Okay there are three ways to configure an IDE device (hard drives, DVD drives, CDROM, etc.), they are:

Master
Slave
Cable Select

Most IDE devices have a jumper that you can move to configure the IDE device.    Laptops use slim CD/DVD drives.  The slim drives have no jumpers.  Seems stupid to me but then I am not an engineer, another cost cutter?  Anyway when you purchase a DVD or CD for your laptop you should ask how it is configured or it will likely not work.  It needs to match your old drive.

In my case the slim DVD drive I purchased was set for cable select.  My laptop does not have a cable that supports cable select drives, so the drive was telling the laptop it was a slave.  And the bios could not see the drive.  The fix is to short pins 45 and 47 together, by shorting the pins you are forcing the drive to act as a master IDE device.  Pictures are to be found on the web for different drives on how to short the pins.  Most web sites say to use solder which is what I used.  Originally I was going to use conductive paint but the stuff is hard to find locally.  One saleman suggestted it was pulled from the market because of environmental concerns.  Another website suggestted using fine wire.  I did not see anyway to make this work without risk of shorting other pins, not a good thing.  I did the solder route since I am experienced with soldering.  However, my eyes are not what they use to be and those pins are awful close together.  Think of two pieces of thread with one thread width between and you get the picture.  I dabbed just enough solder on the iron's tip so when I touched it to the two tabs from the connector a short was formed.  It works great the drive is now /dev/hdc when before it was /dev/hdd.  And the bios sees the drive.

SonWon

---

