---
title: "ASUS M51S laptop sometimes crashes on boot"
date: 2009-01-16
forum: Hardware
---

### Post by fireoftroy on 2009-01-16
Sometimes (maybe 1 out of 20) when I boot, the laptop will get about 3/4 of the way through the boot process and freeze up while the HDD and scroll lights flash together.  I hold down the power button, turn the machine off, and then start the machine back up and it boots fine.  I haven't ever had this problem while booting Winblows Mista, but then again I only boot that about 1:100 with Ubuntu.

I keep my machine up to date with all updates (critical updates install automatically and I install the others when they become available).  The only thing I can begin to point a finger at as being a possible cause would be the last kernel update since this started after installing that.  Otherwise I can't find a common cause.

While I am comfortable with Ubuntu GUI, I'm still learning the behind the scenes parts of Linux.  Where are the system logs and how can I check them for a possible cause?  What are some other ideas for troubleshooting such an issue?  Any assistance would be appreciated.

---

### Post by RJARRRPCGP on 2009-01-16
Sounds like your PC isn't stable. The cause may be a bad cap.

---

### Post by fireoftroy on 2009-01-16
Correction to my original post, the caps lock and scroll lock lights flash, not the HDD light.  

I'm starting to question the stability of the system myself.  It seems to be occurring more frequently and tonight I noticed the hinge caps for the monitor were loose and the internals could be seen.  It's still under warranty so I think I'll pursue that option.

---

### Post by RJARRRPCGP on 2009-01-17
> **fireoftroy said:**
> Correction to my original post, the caps lock and scroll lock lights flash, not the HDD light.  



I meant a bad capacitor on the motherboard or in the power supply.

->And the keyboard lights are even more likely to be a bad capacitor then the HDD light!<-

For more information, check out this web site:

[http://badcaps.net](http://badcaps.net)

---

### Post by fireoftroy on 2009-01-18
That definitely sounds like a strong possibility.  I checked the ASUS website and there was nothing similar to this on any of their forums, so it doesn't seem to be a common issue.  At this point I think I'm going to dig out the receipt and submit it to warranty.  Thanks for your help.

---

### Post by fireoftroy on 2009-04-29
A while back there was an ACPI fix for 8.10 that put a stop to this.  I've since loaded 9.04 and haven't had this problem.

---

