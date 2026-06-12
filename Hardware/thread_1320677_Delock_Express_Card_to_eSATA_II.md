---
title: "Delock Express Card to eSATA II"
date: 2009-11-09
forum: Hardware
---

### Post by XeroXer on 2009-11-09
Hi all!

Just got my "Delock Express Card to eSATA II" today and wanted to try it out.
Plugged it into my Ubuntu 9.10 laptop and nothing happened.
No lights blinking and from what I can see in the System Log Viewer nothing is logged.

Looking at the page ([http://www.delock.com/produkte/gruppen/Express-Card/Delock_Express_Card_to_eSATA_II_61382.html?groupname=Express-Card&itemnumber=61382&action=&](http://www.delock.com/produkte/gruppen/Express-Card/Delock_Express_Card_to_eSATA_II_61382.html?groupname=Express-Card&itemnumber=61382&action=&)) it says "for Windows 2000/XP/2003, Vista, MAC and Linux" under specifications.
But when downloading the manual neither MAC or Linux is listed.

Does anyone have any idea on how to get it running or should I just go out and get a new card, again?

---

### Post by the_MKay on 2009-11-28
Try this: ```
sudo modprobe pciehp
```

---

