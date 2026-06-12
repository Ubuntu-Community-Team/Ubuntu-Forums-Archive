---
title: "Promise RAID stuff and Ubuntu"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by ARhere on 2007-11-05
This is a [repost]("http://ubuntuforums.org/showthread.php?t=253839") but I thought the topic would be best served here to get more experienced input.

I am in the process of moving my file/print server from windows to Linux and I use an [SX4000]("http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=94") for RAID5 (*The OS is maintained on a separate disk*).  I booted using a Live CD just to see how much work would be involved in the switch.  An "lspci" does list the SX4000 card but no drivers were found during the Live boot.

I am speaking out of ignorance here, but I see no reason why the [Red Hat driver]("http://www.promise.com/support/download/download2_eng.asp?productId=111&category=driver&os=3&go=GO") would not work on Ubuntu as the differences should just be file location.  I hope a more experienced Linux guy will set me straight.

I have no idea why the drivers have to be packed in a floppy image but I will unpack it and try to test them on a FC6 first, then mimic the install on my Ubuntu machine.  Wish me luck or give me advice!

Also, I saw a link either here or on ./ that was stating there were too few driver projects to keep the many Linux developers busy, maybe this is a good candidate!

---

### Post by ARhere on 2007-11-06
Well...

I extracted the Red Hat driver and tried to install it on FC6.  Immediately I noticed that the driver was compiled against kernel 2.4 and I am not sure I have all the resources to recompile the driver for 2.6 kernel.

I have searched a bit online but have not found answers, just other people with the same problem.  It is sad but this driver problem is actually keeping Windows as my file/print server OSr.  (*I don't have the money to ditch the 40 & 80gig mirrors for a nice pair of 250g drives.*)

My next step is to simply, and nicley, ask promise to possibly recompile a driver for Linux 2.6.  If anyone has more info or suggestions please speak up.

-Andrew:confused:

EDIT:  I found [this resource here]("http://majestic.lugh.de/promise/").  Through all of the documentation, there is only a short link advertising a kernel 2.6 update with an RPM and source code and it appears the last update was in 2005.  I am at my wits end at this point except to just convert the rpm for Debian/Ubuntu, install, and cross fingers.  I would appreciate anyone else with a SX400 (*or similar*) to test out the RPM or look at the source.

-AR

---

### Post by psusi on 2007-11-08
Indeed, the proprietary driver is for the 2.4 kernel.  Read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by Badmaster on 2007-12-21
hi all, I am having trouble compiling the driver from the one and only resource on Sx4000 IDE Raid Controller drivers for linux out there...

$make yields tons of errors and I don't really get anywhere googling for them.

I'm using 2.6.22-14-server does any1 have compiled drivers for that kernel?

Thanks in advance!

---

