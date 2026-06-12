---
title: "Silicon Image Sil 3112 issue"
date: 2009-03-09
forum: Hardware
---

### Post by th3bigguy on 2009-03-09
I have an legacy (never thought I would be saying that) gigabyte motherboard ga-8penxp.  It has the Silicon Image SIL3x12 onboard raid controller.  I currently have the controller configured for RAID 1.  When I boot into Ubuntu 8.10 after the RAID controller initializes, Ubuntu see two separate disk and not one single disk like Windows is seeing.  Does anyone have a config or info on how to get Ubuntu to work properly with the Sil 3x12 raid device.  I have been checking oround google and the forum but I can not see the correct data I am looking for.  When I load gpart Is see sda and sdb.  There has to be a "driver" to get ubuntu to see one full disk and the partitions from the other operating system.  Any help would be much appreciated.  Thanks again.

---

### Post by cariboo on 2009-03-09
Have a look at the [FakeRaidHowto]("http://help.ubuntu.com/community/FakeRaidHowto").

Jim

---

