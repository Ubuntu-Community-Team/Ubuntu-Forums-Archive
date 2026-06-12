---
title: "ati mobility m4 with DRI and suspend/resume?"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by velovite on 2006-07-30
Hi everyone.

I recently got my hands on a Dell Latitude C800 and installed Dapper on it. The install from the live CD requires to go through safe graphics mode, but then I managed to get the Ati Mobility M4 graphics card working properly with the ati/r128 driver. In spite of it being already an "old" machine (It has a sticker saying "designed for Win Me"), I get very decent overall performance and I am quite happy with this. 

I have a remaining problem that maybe someone out there knows how to solve:
I can have suspend/resume working well if DRI is disabled. But if I enable DRI, suspend/resume is "nearly working". I mean it suspends OK, but on resume the GUI is painfully slow (it requires a minute or so to repaint the screen), the cursor moves every 10s, and the CPU seems to be heavily loaded (by X from what I can see). I can switch to text console and everything is allright there.

It seems pretty close to working, so I guess something is just misconfigured, but after trying differents changes in xorg.conf, acpi-support and boot options, I made no progress. I couldn't find much helpful info on the net either. Does someone knows how to debug this?

I can post my config and log files if needed, but right now I can't figure which would be most helpful.

Thanks in advance.

---

