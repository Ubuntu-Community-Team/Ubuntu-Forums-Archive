---
title: "Getting a hard drive to spin down"
date: 2023-02-16
forum: Hardware
---

### Post by michael351 on 2023-02-16
I tried to set the time out on a new hard drive using hdparm to shut down the spindle after 15 minutes of no activity, but it doesn't seem to be working.
Overnight, the hard drive is still spinning away and at operating temperature.

$ sudo hdparm -I /dev/sdb | grep level
        Advanced power management level: disabled

Any ideas on what I can do to set the idle time and put the drive to sleep?

** problem solved ** I had a bad USB enclosure. Changing enclosures solved the problem and APM works now.

---

