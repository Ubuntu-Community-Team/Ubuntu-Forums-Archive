---
title: "Buffer I/O Errors at end of shutdown"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by REDace0 on 2009-10-30
I've got 9.10 running via Wubi on a new HDD. Started as 9.04 and upgraded to 9.10 the night before official release. Whenever I attempt a restart or shutdown, all processes successfully quit and anacron stops, but then immediately after it says it's turning off the swap, I get 1 to 15 lines of error messages referring to buffer I/O on the hard disk. I can't determine if this is a true HDD error or a software problem in Wubi's loop mounting software.

---

### Post by poo706 on 2009-10-30
I and several others are seeing the same issue.  All of us installed an earlier version via Wubi then upgraded to Karmic shortly before the final release.  We were discussing it here: [http://ubuntuforums.org/showthread.php?p=8187647](http://ubuntuforums.org/showthread.php?p=8187647) , until the thread was closed.  Don't be fooled by the title, the issue was not solved.  I've been trying different things for the last week and have not made any progress.

[poo]

---

### Post by ellalan on 2009-10-30
I have the same problem as well, upgraded from 9.04 through wubi.

---

### Post by kaelonlloyd on 2009-10-30
I'm also having this problem, and it's quite worrying because i once corrupted my linux image file by shutting it down via hard shutdown.

So is there any good way to shutdown for now untill this problem is fixed?

---

### Post by usagetta on 2009-10-30
I had the same problem, but don't think there is a solution....
I got rid of the problem through a fresh install to Karmic with Wubi...

---

### Post by kaelonlloyd on 2009-10-31
Bump

---

### Post by ellalan on 2009-10-31
I have uninstalled 9.10 and wait for the wubi installer to get the speed which I desire. ATM, it takes a very nice 910h55m and I am not going to wait that long because I'm not desperate.

---

### Post by REDace0 on 2009-10-31
If a fresh install will fix it, I'll consider doing that. I spend all my time booted into Ubuntu anyways. It might as well have it's own dedicated partition.

---

### Post by poo706 on 2009-11-01
This is getting talked about on all of these other threads:
[http://georgia.ubuntuforums.org/showthread.php?p=8216794](http://georgia.ubuntuforums.org/showthread.php?p=8216794)
[http://swiss.ubuntuforums.org/showthread.php?p=8206421](http://swiss.ubuntuforums.org/showthread.php?p=8206421)
[http://georgia.ubuntuforums.org/show....php?p=8206461](http://georgia.ubuntuforums.org/show....php?p=8206461)
[http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799](http://ubuntu-ky.ubuntuforums.org/sh....php?p=8212799)

The most promising thing I've seen is from the last one, and it's just a workaround at best. The advice from post #6 (from P4man) halfway worked for me. When I get the buffer errors, I can get it to shutdown without holding the power button, but I couldn't get it to reboot via that method. In doing searches for this nearly every day for the last few weeks, it looks like it's a problem that's hit Wubi before. And there's a lot of people talking about it, so I'm sure a fix will be released soon.

[poo]

---

### Post by ramakrln on 2009-11-11
SO what is the final solution for this problem ?
Pls let me know if u have a solution.. its bad to hard shut down my computer every time..

---

### Post by wrgb2 on 2009-11-11
Ramakrin,

It looks like the only "fix" is to do a fresh install.  We all have wubi, and either updated 9.04 or beta 9.10 after release of Karmic.  I have not found a solution in the forums - the one mentioned in the last thread above worked for me for one restart, the problem came back after that.  If a fresh install is not an option for you, hopefully there will be a fix soon.  I'm going to launchpad now to see if this has been reported.

---

### Post by wrgb2 on 2009-11-11
This is bug #468589 in launchpad: [https://bugs.launchpad.net/wubi/+bug/468589/+activity](https://bugs.launchpad.net/wubi/+bug/468589/+activity) .  It's been confirmed and the importance is set to High, so there should be a fix soon.

---

### Post by ppb1701 on 2009-12-05
well the launchpad claims it's fixed, mine worked intermittently with the previous flag change fixes now it always throws buffer i/o errors. :(

---

