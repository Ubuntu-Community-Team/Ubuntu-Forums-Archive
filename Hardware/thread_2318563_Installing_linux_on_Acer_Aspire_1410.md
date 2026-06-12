---
title: "Installing linux on Acer Aspire 1410"
date: 2016-03-27
forum: Hardware
---

### Post by Staale_Nataas on 2016-03-27
Hi. I have an old Acer Inspire 1410 laptop and I've attempted to install linux on it. I've tried Mint, and now lately Ubuntu, both several times. I've used both Windows and Mac to create USB startup disks and they have both managed to start the machine running Linux. Everything seems to work when I run it off the USB-stick. But when I try to install it on the machine, it goes through the whole installation process but then won't boot up.

When booting the machine, I get a command line interface, I've attached a picture of what it looks like. 

Does anyone have any experience with this? All advice is kindly welcome. Thanks.

---

### Post by weatherman2 on 2016-03-27
Are you sure the hard drive is good in this machine? I would check the S.M.A.R.T. Attributes of the hard drive with GSmartControl.  You can install GSmartControl in a Ubuntu USB live session first by enabling the "Universe" repository, then installing GSmartControl through software center.  (Of course, you must be online to download/install things.)  Look at the Attributes tab of GSmartControl and see if any are highlighted in red or pink - this may show issues with your hard drive.

---

