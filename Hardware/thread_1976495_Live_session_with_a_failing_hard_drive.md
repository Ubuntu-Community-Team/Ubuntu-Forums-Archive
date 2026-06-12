---
title: "Live session with a failing hard drive"
date: 2012-05-08
forum: Hardware
---

### Post by jstead on 2012-05-08
Hi, I've recently been having lockups on my Satellite Pro A200, and I've managed to narrow down the cause to either a bad motherboard or hard drive.

I need to be sure it's the hard drive before buying a replacement, because it seems to be impossible to source a mobo for this particular model as it was only sold in Australia.

Anyway, I've had lockups in Xubuntu and Trisquel live sessions with swap turned off, so could the HDD still have been the cause?

---

### Post by ahallubuntu on 2012-05-08
Sure - check the hard drive's S.M.A.R.T. status (and run tests too).  You can run GSmartControl (graphical) or smartctl (terminal).  If you don't have a Ubuntu distro with smartmontools installed, grab the handy Parted Magic Linux distro that has this tool plus many other pre-packaged - a nice diagnostic CD to have laying around!

Anyway, first look at the Attributes.  If you use the graphic version of Smart Control, look for attributes highlighted in red (like Pending Sectors or Read Error Rate).  Post the results if you want some interpretation. 

After checking the Attributes, you can also run tests like the extended test (may take 1-2 hours).

Can we assume you've cleaned out the CPU heat sink/fan and made sure it's not overheating?

---

### Post by jstead on 2012-05-08
I kind of forgot that SMART existed. If I'm not misinterpreting "pre-failure" on the attributes tab, that seems pretty conclusive right? The extended test is running anyway, so I'll know once that's finished.

And yeah, overheating was my first thought. Freezes are totally independent of temperature, though.

---

### Post by ahallubuntu on 2012-05-08
The Reallocation Event Count could be very bad but not necessarily.  There are no pending sectors at the moment.  Perhaps there were some but they have cleared on their own.  There are no reallocated sectors either which means no bad sectors were replaced with spares.

Personally, given that you are having problems with this drive, I would make an image backup of the drive then zero it out completely (probably with DBAN - [www.dban.org](www.dban.org) ) and then check S.M.A.R.T. attributes again.  If there is no change and it has passed the extended test you are now running, maybe it is not failing and it is something else on the laptop (you could restore the drive from the image backup you made).  Or if the drive is bad, restore the image to a new drive.

---

### Post by ahallubuntu on 2012-05-08
The Error Log tab is red too - so there were some errors on the drive as well?  How many?  What error?

Have you run e2fsck (for Linux partitions) and/or chkdsk for Windows partitions?

---

### Post by jstead on 2012-05-09
> **ahallubuntu said:**
> The Error Log tab is red too - so there were some errors on the drive as well?  How many?  What error?

Have you run e2fsck (for Linux partitions) and/or chkdsk for Windows partitions?

Here's the one error log:
```
SMART Error Log Version: 1
ATA Error Count: 1
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1 occurred at disk power-on lifetime: 8091 hours (337 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 09 47 d9 6a e9  Error: UNC 9 sectors at LBA = 0x096ad947 = 157997383

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 28 28 d9 6a e9 00      04:07:59.100  READ DMA
  e7 00 00 00 00 00 a0 00      04:07:59.100  FLUSH CACHE
  ca 00 20 c0 c5 42 e0 00      04:07:59.100  WRITE DMA
  ca 00 18 88 c2 42 e0 00      04:07:59.100  WRITE DMA
  ca 00 20 40 c4 42 e0 00      04:07:59.100  WRITE DMA
```

Note that the current power-on lifetime is 11055 hours, so that's 3000 hours of uptime ago.

Chkdsk and e2fsck both show some level of corruption. The extended SMART test has also completed "without errors".

EDIT:
I'm not really familiar at all with cloning / restoring a hard drive, so I'll probably just try yanking the hard drive before it gets to that.

---

