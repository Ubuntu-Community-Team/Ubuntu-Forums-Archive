---
title: "Function keys on Samsung RC512 Laptop"
date: 2011-04-03
forum: Hardware
---

### Post by jmvizanko on 2011-04-03
Whenever I go to use the function keys on my samsung rc512 laptop in Ubuntu, it apparently gets stuck in a loop, and I cannot make it stop without shutting down the PC.  Does anybody know a fix to this, that a noob would be able to accomplish?  Thanks.

---

### Post by mkulon on 2011-04-04
This laptop has good specs, is light, nice form factor, but doesn't seem to be fully supported by Ubuntu 10.10 (64 bit) as of 4/4/2011.  Specifically:
- closing the lid freezes the system
- There is no linux driver for the Graphics card, Nvidia GeForce 525M.

If anyone has any experience getting Ubuntu working on it, please post your tips/experiences.

---

### Post by jmvizanko on 2011-04-05
Well its working pretty well for everything else.  Haven't tried closing the lid yet.  As for the graphics card, I don't really need it (yet), as I use Windows for CAD and games (and that's about it).  But the function keys would be nice.  Thanks for the heads up.

---

### Post by leclerc65 on 2011-04-05
Did you try [this]("http://www.voria.org/forum/viewtopic.php?f=3&t=296") ?

---

### Post by jmvizanko on 2011-04-07
I did try "that" and now some of the function keys do work (including mute and volume adjustment, which are really the only ones I care about the most).  Thanks for the suggestion, although I think I'll leave this open in case somebody knows how to get even more of them up and running.  This is assuming that I know what I'm doing with that (or any) PPA, which is not a good assumption.

---

### Post by jmvizanko on 2011-04-07
> **mkulon said:**
> - There is no linux driver for the Graphics card, Nvidia GeForce 525M.

Is this why every 3rd time or so that I start up Ubuntu, it has serious display problems, like horizontal lines are displaced on the desktop, or in programs and images?

Should I even be running Ubuntu on this machine?  (I hope I can)

---

### Post by mkulon on 2011-04-07
Initially, the Samsung RC512 laptop could not be put to sleep / suspend in Ubuntu (either by closing the lid, nor explicitly).  Reviewing the syslog, the problem was with USB3 immediately waking it up.  I found a post describing a similar problem with other laptops, and following their advice fixed it ( 1st post on [http://ubuntuforums.org/showthread.php?t=1634301]("http://ubuntuforums.org/showthread.php?t=1634301") )

I did not have a need to play with the function keys.

My biggest remaining sore is the graphics card (no acceleration, can't do Desktop Effects, scrolling is slow).  NVidia doesn't have a binary linux driver for the GeForce 525M yet.  Noveau doesn't seem to support it either.

---

### Post by zzztimbo on 2011-11-14
Has anyone made any progress on these RC512 issues? I've been considering buying one.

---

### Post by Jack-87 on 2011-12-02
My issue is getting the Nvidia Card to function properly and the wifi.  I seem to be getting less than 56k speeds when using wifi. I wonder if it has anything to do with the built in WiMax anyone else having issues with their Samsung RC512 ? mine is RC512-s01

---

