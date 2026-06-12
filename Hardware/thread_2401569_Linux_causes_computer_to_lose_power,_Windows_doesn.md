---
title: "Linux causes computer to lose power, Windows doesn't"
date: 2018-09-19
forum: Hardware
---

### Post by jweed262 on 2018-09-19
Hi,
I'm currently running Ubuntu 18.04 on my desktop, which I've been dual booting Linux/Windows on for the past couple of years.  Recently, my computer has completely powered off (fans stop, everything loses power) and then immediately powered back on while I'm using it, usually between 5-30 minutes after I turn it on.  Nothing has changed in the applications I've been running (usually just Chrome + Emacs).  I originally thought it was my power supply, but just to test, I booted Windows to see if it would happen.  Weirdly enough, I was able to keep Windows running for over 12 hours, and I was even able to stress test it for an hour (100% CPU + GPU) with nothing happening.  
My hardware is:
i5 4670
MSI Z87-G41
MSI GTX 770

Is there anything I can do to figure out what is going on here?

```
$ last reboot
reboot    system boot     4.15.0-34-generi Wed Sep 19 13:36    still running
...

```

---

