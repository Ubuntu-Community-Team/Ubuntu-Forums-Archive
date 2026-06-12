---
title: "Dell XPS m1730 cannot enable SLI"
date: 2009-11-20
forum: Hardware
---

### Post by mrancier on 2009-11-20
If I try to enable SLI on my m1730 the system hard locks.  Completely frozen, black screen.   I have looked around and some people seem to believe it is related to Xorg and the lack of BusId value in the config.  I tried this, but the system still locks.  I've also tried this on Fedora 12, Mint 8, Arch, and OpenSuse 11.2.  Same problem.  So it seems that Xorg has ****** up somewhere (or just plane old dell garbage).  everything worked and still works on jaunty.  Does anyone have any ideas as to how this problem can be resolved or worked around ?

---

### Post by mrancier on 2009-11-24
Not one reply.  Jesus Christ guys, really ? Not one person can help with this ?
How disappointing and somewhat upsetting.  This community is much bigger than archlinux's, but not nearly as involved.I guess you get what you pay for (in this case pay nothing get nothing).  Back to arch for me.  Thank you all.

---

### Post by wiresquire on 2009-12-02
It's a big community, but you need to pick the right community.

You will find over at the [NvNews Linux forum](http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14) that there seems to be problems with enabling SLI on M1730 for all versions of the 185.x and 190.x series of drivers. Eg, you can see a post I started [here](http://www.nvnews.net/vbulletin/showthread.php?t=136630).

There *may* be fixes in the 195.x series, but the latest current beta  195.22 driver doesn't work for me for SLI.

You can try earlier versions from 169.04 through to 180.60 and they should work.

ws

---

