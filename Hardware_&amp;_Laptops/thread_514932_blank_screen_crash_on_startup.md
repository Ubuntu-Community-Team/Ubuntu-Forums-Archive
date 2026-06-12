---
title: "blank screen crash on startup"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by dogbox on 2007-08-01
hey guys
whenever i log into ubuntu, i get a blank screen and nothing works. sometimes a kernel-like thing would appear, taking up the whole screen and asking me for my user/pw. when i type em in, nothing happens...i just can't get into ubuntu. atm, i'm suspecting something wrong with my graphics...i think i changed some settings previously. before this, i had been having very similar problems...whenever i exited stepmania, closed the lid (which i set to put up a blank screen), or sometimes when i used rhythmbox, the blank screen would come up followed by streaks of colors. i know this isn't much info...i'll try to explore more...
any and all help is appreciated!

---

### Post by Ek0nomik on 2007-08-01
> **dogbox said:**
> hey guys
whenever i log into ubuntu, i get a blank screen and nothing works. sometimes a kernel-like thing would appear, taking up the whole screen and asking me for my user/pw. when i type em in, nothing happens...i just can't get into ubuntu. atm, i'm suspecting something wrong with my graphics...i think i changed some settings previously. before this, i had been having very similar problems...whenever i exited stepmania, closed the lid (which i set to put up a blank screen), or sometimes when i used rhythmbox, the blank screen would come up followed by streaks of colors. i know this isn't much info...i'll try to explore more...
any and all help is appreciated!

Did a recent change to your xorg.conf file perhaps mess it up?  Was Ubuntu *ever* running without this issue, or is it a continuous thing?

Are you able to get into Ubuntu *at all*?  Maybe not graphically, but can you at least get to a command line screen where you can enter commands?

---

### Post by wjp.reg on 2007-08-01
Sounds like video problems.

Try reconfiguring video by running the following after booting into rescue/safe mode:

```
sudo dpkg-reconfigure xserver-xorg
```

and select the video driver and supported resolution settings.  Everything should be ok by default.

Good luck!

---

### Post by dogbox on 2007-08-03
> **Ek0nomik said:**
> Did a recent change to your xorg.conf file perhaps mess it up?  Was Ubuntu *ever* running without this issue, or is it a continuous thing?

Are you able to get into Ubuntu *at all*?  Maybe not graphically, but can you at least get to a command line screen where you can enter commands?

i think it's probable that a change in my xorg.conf messed everything up, since i've kinda experimented with it a lot. usually i can get into ubuntu with only the command line screen. however, recently (right now), i've been able to get into ubuntu, but with a huge screen resolution. i still have graphics problems right now...my .avi's don't work, my computer crashes when i change resolutions, etc.

sorry 'bout the late response

---

