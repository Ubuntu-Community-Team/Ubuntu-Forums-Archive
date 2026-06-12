---
title: "Dell Inspiron E1505 Boot Hang"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by optimarcus_prime on 2007-01-20
I'm fairly new to Ubuntu and Linux in general but I have been sucessfully running Edgy for about three months now with no problems on a five-month-old Dell Inspiron E1505.  Today I was doing nothing out of the ordinary and I opened and then closed my CD drive.  Suddenly the computer rebooted itself.

Now, the computer attempts to start up and then has a boot hang during the progress bar phase.  The bar gets to about the third "segment" and then stops:

[IMG]http://sibbles.com/bar.JPG[/IMG]

If I wait long enough, the bar will sometimes progress to four bars, but it still stays in one place.

When I boot the computer in "Ubuntu, kernal 2.6.17-10-generic (recovery mode)," the progress gets to the following:
```
[17179582.004000]  Uniform CR-ROM driver Revision : 3.20
```
[IMG]http://sibbles.com/CDDriver.JPG[/IMG]
and then the boot hangs.  As far as I can tell, when the progress bar in normal boot-up stops at three segments, that is probably where it is.  Then, if I wait long enough, the following comes up:
```
*  Loading manual drivers...
```
[IMG]http://sibbles.com/manualdrivers.JPG[/IMG]

...and then the boot hangs again.  As far as I can tell, it never progresses past this point.

As I said, I'm fairly new to Linux, but I'd really really like to get my system working again without having to reinstall Ubuntu.  Heck, I'd even pay.:) So, any help that someone can offer, I'd be most appreciative.  Thank you in advance.

If I missed any information that you need, let me know and I'll post whatever you need.

---

### Post by danhm on 2007-01-21
Do you happen to know if the drive was mounted at the time? I'm not really sure if that it matters, though.


I also have an e1505 and do that all the time; maybe I should stop.

---

### Post by optimarcus_prime on 2007-01-21
The drive was mounted at the time, and I've tried restarting with the drive plugged in and out.  However, I don't know how to make that count.  Any suggestions?   Thanks.

---

