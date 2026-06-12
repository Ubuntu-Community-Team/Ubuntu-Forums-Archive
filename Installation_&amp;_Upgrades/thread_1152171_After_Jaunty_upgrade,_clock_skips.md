---
title: "After Jaunty upgrade, clock skips"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by sakuramboo on 2009-05-07
So far, all of the bugs I cam across after upgrading to Jaunty have been very minor and fixed, except for one.

After upgrading to Jaunty, I notice my clock sometimes skips a second. It will count 3, 4, 5, 6, 8, for example. It seems to skip 1 second every 10-15 seconds. The time is always right, but, it just seems that the clock runs slower now and skips 1 second to keep it right.

I monitored htop and I kill some misc. processes to see if it helps. It did, but it's still happening.

EDIT: It seems that it is system wide, not just with my clock. For example, as I am typing this, every few seconds, I keep on typing, but the text does not display for a fraction of a second. This also happens in abiword. When I am browsing a website, scrolling up and down will sometimes pause for a split second and then catch up to where it's supposed to be.

I was thinking that it might be something wrong with Xorg, so I looked in the log and noticed two warnings. One was for a missing font, which I fixed and the other was for v4l. I also browsed the xorg.conf file and noticed that glx and GLcore were being used. So I disabled GLcore, but that didn't fix it either.

This annoyance has been seen since I upgraded to 8.10 from 8.04. And it still persists in 9.04. I did the upgrades via apt.

EDIT: I upgraded to 9.10 and the problem still exists. I took a video of it to show everyone what I'm talking about.

[http://www.sakuramboo.com/videos/clock_skip.mpeg](http://www.sakuramboo.com/videos/clock_skip.mpeg)

---

