---
title: "Seagate FreeAgent Pro - 750GB"
date: 2008-08-21
forum: General Help
---

### Post by Bartee on 2008-08-21
Will this work on 8.04 ?

[http://www.buy.com/prod/seagate-freeagent-pro-750gb-usb-2-0-esata-7200-rpm-firewire-external/q/loc/101/204110108.html]("http://www.buy.com/prod/seagate-freeagent-pro-750gb-usb-2-0-esata-7200-rpm-firewire-external/q/loc/101/204110108.html")

It does not list linux or ubuntu, but it is usb 2.0 and firewire 

Tech Specs
	Capacity
	750 GB
	Interface
	FireWire 400
	USB 2.0
	eSATA

	Operating System
	Windows XP Home
	Professional Edition
	Windows 2000 Pro
	Mac OSx 10.3, 10.4 as read only

	Performance
	USB 2.0: 480 MB/sec
	eSATA: 3 GB/sec
	Spindle Speed: 7200 RPM
	FireWire 400: 400 MB/sec

	Physical
	Product: 7.5 tall x 1.4 thin x 6.3 deep
	Base: 1 x 5.2 x 3
	Weight: 2 lbs
	Inside the Box
	FreeAgent Pro data mover drive
	FreeAgent software and electronic documentation pre-loaded on the data mover drive
	USB2.0 + eSATA interfaces
	Select models include dual FireWire 400 interface module and cable
	USB 2.0 cable
	AC power adapter
	Quick start guide
	Other
	Model number: ST307504FPA1E3-RK
	Limited Warranty: 5-year

---

### Post by rampageoberon on 2008-08-21
I'm quite sure it will work just fine. the drive will probably come formatted in FAT32 so will be plug and play without any issues. If you wish you can format it to ext3.

---

### Post by stoneage on 2008-08-21
As long as you are aware of the possible spin down problem and know what you are getting into. There are some fixes and workarounds, but it was a known, and vexing, problem for a while there.

This is one example, a search will turn up more, I don't know if it is still a problem:-
[http://ubuntuforums.org/showthread.php?t=679228](http://ubuntuforums.org/showthread.php?t=679228)

---

### Post by Bartee on 2008-08-21
After reading the Spin Down Thread there does not seem to be any conclusion to the problem.

It looks like the change in settings will fix the "problem" , but still sometimes the extenal usb drive is not available.

I use this for a nightly backup.   I need it to work reliably unattended.

This would seem like a real bug that should have been fixed.  But then again, I do not understand how anything get's fixed, since all of this is FREE!!! Some very great people out there somewhere.

---

### Post by stoneage on 2008-08-22
I know, like the elves and the shoemaker.

One very simple solution is to not leave it idling for long periods. If it goes into sleep mode after 15 mins on idle, an easy way to prevent this is to shut it down before it goes to sleep, or wake it up before it goes to sleep.
I think someone wrote a script(should be on the forum somewhere, there were many posts about it a while back), that gives it a nudge every so often to prevent it idling for too long.

Or if you have access to a Windows machine you can disable the shutdown(I'm sure there was a linux fix for this too - Seagate also published one).

I wouldn't say don't buy it, but research a fix or workaround before you leave it idling.

---

### Post by Bartee on 2008-08-22
If anyone is still reading this, is the just this brand of USB drive or is this a problem with ALL usb drives.  

I just need a USB drive for backup,  not really particular what brand.

---

### Post by stoneage on 2008-08-22
As far as I know it isn't even all Seagate drives, just the Freeagent series.

---

### Post by jimv on 2008-08-22
I recommend that you get this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817198004](http://www.newegg.com/Product/Product.aspx?Item=N82E16817198004)

And put this in it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148298](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148298)

I have this setup and it is THE BEST portable drive I have ever had.

---

