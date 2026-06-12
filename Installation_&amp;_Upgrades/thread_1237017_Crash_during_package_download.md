---
title: "Crash during package download"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by The_Great_G on 2009-08-10
When I download packages with apt-get (either in Terminal, Update Manager, Synaptic, or Add/Remove) they will sometimes stop downloading and completely freeze the system.  I've tried downloading a number of different packages, and the only thing I found tying it all together was that the longer I spent downloading, the more likely one of my files was going to stop downloading and freeze everything up.  I read somewhere that this may be caused by a bad ethernet driver.  But why must it freeze the whole system?  Does anyone else have the same problem?  More importantly, do you know how to fix it?

---

### Post by raymondh on 2009-08-10
> **The_Great_G said:**
> When I download packages with apt-get (either in Terminal, Update Manager, Synaptic, or Add/Remove) they will sometimes stop downloading and completely freeze the system.  I've tried downloading a number of different packages, and the only thing I found tying it all together was that the longer I spent downloading, the more likely one of my files was going to stop downloading and freeze everything up.  I read somewhere that this may be caused by a bad ethernet driver.  But why must it freeze the whole system?  Does anyone else have the same problem?  More importantly, do you know how to fix it?

Can you post the error message?

---

### Post by The_Great_G on 2009-08-11
It doesn't give an error.  It will be downloading as normal and then the download rate either changes directly to "unknown" or it will briefly display some stupidly slow download rate (like 14 kb/s instead of 840 kb/s) before freezing at "unknown."  Once it has frozen sometimes moving the mouse will work, sometimes it will be the 'wait' cursor and other times it will be frozen or the normal arrow.  The clock also will freeze or not without any pattern.

---

### Post by calebstone on 2009-09-07
I have the same problem to, can't download anything, tried re-installing and everything but still no luck.

---

### Post by barney_alberni on 2009-10-04
I'm also experiencing the same.  It's happened with both wired and wireless drivers and it's very sporadic.  It appears to be most prevalent while adding and removing software (apt-get).  If anyone has any suggestions or fixes, it would be greatly appreciated.

---

### Post by scyntl on 2009-10-29
I have an ugly solution made all the uglier because I don't know why it works:  Do a clean install of Ubuntu Studio 8.10 from the CD, and then upgrade to 9.04.  

I have an HP dv6000, and I've tried various combinations of installs-and-upgrades from 8.04 to 9.10. This happens to be the way I first installed Ubuntu, and it is the only way I've gotten my video drivers (version 1.73), kernel, AND package-downloading to play nicely.

(go figure:rolleyes:)

I hope this can be of help..

---

