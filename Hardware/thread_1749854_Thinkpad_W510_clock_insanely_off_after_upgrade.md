---
title: "Thinkpad W510 clock insanely off after upgrade"
date: 2011-05-04
forum: Hardware
---

### Post by Peepsalot on 2011-05-04
I upgraded from 10.10 to 11.04 a few days ago and my clock has been completely messed up since then.  I never had any problem with it before, but it seems to drift 2-3 hours in a single day now.  It's not a time zone issue, I checked that it is set to my correct time zone (CST), and the amount that it is off is not an exact interval of an hour.   

I have always had the time settings already set to automatically get from internet and this is still happening.  Someone on another forum suggested I install ntpd, which I did, but it made no difference.  On a reboot it seems to set the clock correctly, then I come back after a day and it's off by 2 hours or so.  This is driving me crazy.  Does anyone have an idea what is going on? 

One other thing, I noticed during the upgrade process, there was a part where it said something like "calibrating clock, this will take 70 seconds" and it waited that long before continuing the installation.  I'm not sure if this is something new in 11.04, because I've never noticed that in any other install or upgrade.  I'm wondering if there is some bug in whatever that application was that tried to figure out my clock rate.  Is it possibly overcorrecting for some massive clock drift that was simply computed incorrectly in the first place?

Is there some way to clear any sort of clock drift compensation that i happening?  Someone also suggested I try deleting /etc/adjtime, saying that it would be re-created automatically.  I did delete it, but it was never re-created.  The clock is still as inaccurate as it was before I deleted it though.

---

