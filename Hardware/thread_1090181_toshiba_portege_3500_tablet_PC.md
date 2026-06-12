---
title: "toshiba portege 3500 tablet PC"
date: 2009-03-08
forum: Hardware
---

### Post by evilgold on 2009-03-08
Does anyone here have a protege 3500 tablet with the stylus and everything working in ubuntu?

I picked up one at the freegeek thrift store today, its running 8.04 which i am currently upgrading to 8.10. I've seen a few posts and done some googling to try to modify the Xorg.conf into working with the stylus, but no luck so far. Most of what i've found is dated. Some things i came across say that it should "just work" with 8.04 and 8.10, but it doesnt seem to for me.

anyone who has this particular model and can help me out? Perhaps all i need is a (known working) xorg.conf, or is there some other trick to getting this thing working? Any help would be greatly appreciated.

:D

---

### Post by Favux on 2009-03-08
Hi evilgold,

If you read through this thread (before you do anything) you should be able to get the Wacom stuff set up:

[http://ubuntuforums.org/showthread.php?t=1029397]("http://ubuntuforums.org/showthread.php?t=1029397")
I would install the 0.8.1-6 linuxwacom deb.s at Loic2's Wacom wiki.

Unfortunately we're having a problem with rotation.  See this thread:

[http://ubuntuforums.org/showthread.php?t=1053210]("http://ubuntuforums.org/showthread.php?t=1053210")

You could post on the bug report and join the rest of the folks in trying to solve it.  Or maybe your chipset will be different and it will work.

---

### Post by evilgold on 2009-03-08
Favux,

Thank you, after fallowing that post and upgrading to 8.10 and the newest wacom my stylus seems to be working. I still have one issue though, as the stylus does not work on 100% of the screen. This is a second hand laptop that was donated to freegeek, so its quite possible something is just wrong with the machine itself, but im not sure if there might be some other things i can test, or if perhaps someone else may have a similar issue.

I attached an image i did in gimp by trying to fill the entire screen using they stylus. red areas are where it would work. When i go over white areas it will simply jump to the next usable (red) one.

---

### Post by Favux on 2009-03-08
Hi evilgold,

That is a new one to me.  It does look like a hardware problem.  The wacom digitizer is a fine grid built into the LCD.  The blank spots could be areas where the grid has lost conductivity and is not sending signals.

Does the stylus have a battery?  Maybe its low.

That said have you tried to calibrate with wacomcpl?  Type "wacomcpl" in a terminal and a calibration gui will pop up.  Another possibility is that the linuxwacom driver isn't working correctly for you.

---

