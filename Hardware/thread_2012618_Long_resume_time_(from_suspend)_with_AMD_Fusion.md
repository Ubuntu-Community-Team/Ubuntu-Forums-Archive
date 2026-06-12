---
title: "Long resume time (from suspend) with AMD Fusion"
date: 2012-06-29
forum: Hardware
---

### Post by DavidBanner on 2012-06-29
If I make a brand new install of Ubuntu 12.04 64-bit, update it fully, and run the command pm-suspend, then the time for it to resume from sleep is 4 seconds with an Atom/Ion platform and 17 secs with AMD Fusion E-350. But systems report in syslog that resume took 2.5 secs.

I have looked through logs syslog, Xorg.0.log, pm-powersave.log, pm-suspend.log, kern.log, dmesg, boot and boot.log and compared them for the 2 systems. I can't spot any exciting differences (apart from in pm-powersave.log seeing one occurrance of "Setting Host Bridge 0000:00:00.0 to on" for Atom and 8 such lines for E-350, for addresses 0000:00:18.0 to 0000:00:18.7). 

A peculiar thing in syslog is that all events for suspend and subsequent resume are logged during the same second, i e all suspend and resume events have the same time stamp, which if it was true would mean that all of the suspend process, all of my coffe break in between, and all of the resume process took place during < 1 second. Either that or the clock is standing still.

One thing I REALLY would have use for is a log with proper time stamps for each event during resume, so that I could see what is going on: Is it "locked" for several seconds, or in a loop, or waiting for something, etc. But the logs I found don't have that.

With fglrx it is even slower, but I haven's tested that in great detail. I understand graphics driver has an influence on ACPI somehow even though ACPI has its own drivers.

---

### Post by DavidBanner on 2012-07-09
Nobody in the world has installed Ubuntu on a Fusion board? :-/

---

### Post by Redblade20XX on 2012-07-09
Is your BIOS completely up to date? 

ACPI looks into your BIOS for a table to make references to power management events.

Also does both systems you've tested have the exact same hardware?

Did you have the same programs running when putting the system into suspend?

- Red

---

### Post by DavidBanner on 2012-07-10
Hi. Yep the BIOS is updated. And the hardware is completely different as you can see: Atom/ION or AMD E-350. But the software is identical.

I'm wondering: Is there really no way to make a log reveal what is taking the extra 13 seconds?

And can no one tell me what resume time they get on a Fusion board?

---

