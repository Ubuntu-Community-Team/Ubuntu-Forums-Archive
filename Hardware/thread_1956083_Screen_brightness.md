---
title: "Screen brightness"
date: 2012-04-10
forum: Hardware
---

### Post by fidelandche on 2012-04-10
Hi all,
My partner is running a Samsung N150 net book, she just upgraded to 11.10 and since then the screen brightness will not stay at the setting she wants (which is to the max) So each time she starts the net book from hibernation she has to go to system settings - screen to set the brightness. This has only happened since the upgrade, not really sure on how to get the screen brightness to stay at the setting required.

Many thanks

---

### Post by 2F4U on 2012-04-10
There is a bug filed on that issue

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/574250](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/574250)

and the dev says it is fixed. However, the bug has been reopened, so at least one person still seems to have a problem with it. The bug description mentions a ppa which can be used to workaround the problem.

---

### Post by fidelandche on 2012-04-10
Did use the ppa for 11.04 and that did solve the problems, I will have to have a look to see if the ppa is still in the repos, if not I will add the ppa and give it a try.

---

### Post by fidelandche on 2012-04-10
Just gone into update manager and checked the settings and noticed that the ppa had been disabled since the update to 11.10, so I made sure that the ppa was ticked and ran the update manager and now the brightness works as it should.

---

