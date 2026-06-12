---
title: "Acer Aspire 5749-6926 laptop, dual boot (Win 10) misreads internal clock"
date: 2016-02-07
forum: Hardware
---

### Post by Paul Sodtke on 2016-02-07
My laptop (Acer Aspire 5749-6926) has long been set up for dual boot (currently Ubuntu 15.10 and Windows 10). When I switch, the reported time is 6 hours out (which is also my difference from UTC, since I am in the Central Time Zone, but that may be a coincidence). Apparently, the 2 operating systems read the internal clock differently. I have tried switching between manual and auto (from the internet) settings for the time in each operating system, but the problem persists.

I post this to the hardware forum because this appears to be miscommunication with the firmware.

Has anyone else noticed or solved this issue? (A search did not find anything related.)

---

### Post by weatherman2 on 2016-02-07
Doesn't sound like a coincidence.

It's probably going to be easier to let Windows 10 do what it wants and tell Ubuntu to use localtime not UTC.  This is old but probably still relevant: change this one line from yes to no (or vice versa if it is set the other way):

[http://shallowsky.com/blog/linux/ubuntu-system-clock.html](http://shallowsky.com/blog/linux/ubuntu-system-clock.html)

---

### Post by Paul Sodtke on 2016-02-10
There is indeed a line UTC=yes in my rcS file. But this file is owned by root so it cannot be edited just by clicking on it. I suppose I have to use sudo gedit ... from a terminal.

---

### Post by weatherman2 on 2016-02-10
Yep - use sudo!

---

### Post by Paul Sodtke on 2016-02-14
Yes,  it works. Thank you, weatherman2.
Boot up seems to take longer, at least when switching OSs. I suspect some extra error message is generated. I had a look at the log files (by the way, [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) is excellent), but I don't have enough technical knowledge to figure it out.
Oh well, it works, so I don't have to mess with resetting the time each time I use Windows.

---

