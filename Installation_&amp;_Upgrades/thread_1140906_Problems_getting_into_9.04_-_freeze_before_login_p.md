---
title: "Problems getting into 9.04 - freeze before login prompt"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by xonev on 2009-04-28
I just upgraded my Toshiba Satellite A15-S1292 (with integrated Intel graphics) from 8.04 to 8.10 and then from 8.10 to 9.04.  The upgrade process _appeared_ to go smoothly, but I have run into a quite serious problem.

When I boot up the computer, I get the Ubuntu splash screen with the new progress bar and then I get a blue xfce background (I was using xfce) and the progress cursor (the round one with the rotating dots).  It sits there and appears to be working, but then the dots on the cursor keep repeating from the 3/4 point to the starting point instead of going around in a circle - I can still move the mouse around, but when I do ctrl-alt-f1 or ctrl-alt-f4 i get a black screen with no prompt.  If I do ctrl-alt-f7 then I get the same screen with the malfunctioning cursor.  I never get a login prompt.

Anyone have any idea where I should look first?

EDIT:
It actually sounds like my problems are similar to the ones found on this thread: [https://answers.launchpad.net/ubuntu/+question/6130](https://answers.launchpad.net/ubuntu/+question/6130), but I still haven't been able to fix it.  Sometimes I am able to use ctrl-alt-f1 to get a prompt (usually when I boot from recovery mode) and sometimes I am not.

EDIT:
OK, now I'm getting somewhere - it appears that gdm is trying to autologon or something.  I took a look at /var/log/syslog and I keep getting messages such as

```
gdm[2927]: WARNING: Couldn't authenticate user
last message repeated 27 times
last message repeated 52 times
last message repeated 52 times
```

So that explains why the "working" cursor doesn't rotate all the way around - it keeps on trying to authenticate and each time it tries i get a new "working" cursor.  I'll try to find out why it's attempting to autologon (or whatever else it's trying to do).

---

### Post by jvijayv on 2009-05-14
Hi,

Were you able to figure this out? I have the same issue on my laptop after upgrading to Ubuntu 9.04.

Here is the link to the issue that I raised -
[http://ubuntuforums.org/showthread.php?t=1155554](http://ubuntuforums.org/showthread.php?t=1155554)

Thanks,
-Vijay

---

