---
title: "Ubgraded to Intrepid... Now my  twinview won't work"
date: 2008-11-01
forum: General Help
---

### Post by jondecker76 on 2008-11-01
I've been using Ubuntu for about 18 months now on the same hardware. I use an nVidia card and use twinview to have a large desktop across 2 monitors. I have done this setup many times with no problem until today.

I have a separate /home partition so I did a fresh install around my /home partition.
I installed nvidia-settings.  I run nvidia-settings from the terminal:
```
gksudo nvidia-settings
```

I apply the changes and everything will work until the next reboot, where I lose the twinview and  I'm at a grotesquely low resolution.

While in nvidia-settings, the "Save to X configuration File" button appears to do nothing except exit the application. Checking my xorg.conf file after this shows that absolutely nothing was changed.

Is anyone else having similar problems?

thanks

---

### Post by jondecker76 on 2008-11-02
just giving this a bump hoping that someone can help me!

---

### Post by C.S.Cameron on 2008-11-02
I just gave twin view a try with 8.10.
Got the same results as you.
I took the Nvidia xorg.conf I was using in alpha 8.10 and replaced my current one.
Twin view is working ok now, but I think this is a Bug.

---

### Post by Sayne on 2008-11-02
Same issue here. I don't have any old xorg.conf files (dumb of me, I know) is this a bug in nvidia-settings, xorg with it's randr, both? Hope his gets resolved, or I'll have to go back to hand making my xorg.conf.... nooooooo! Heh.

---

### Post by jondecker76 on 2008-11-02
I didn't back mine up either - lesson learned


I think I just read somwhere that the bug only exists when trying to over-write an old xorg.conf. Supposedly, if you rename your xorg.conf to something else (xorg.conf.backup for example), and then use nvidia xsettings, then it will save a new xorg conf.

I'm at work right now so I can't try it at the moment, but definitely worth a try!

---

### Post by Sayne on 2008-11-03
The latest update to nvidia-settings fixed the save to xorg.conf file crash bug. So this morning I was able to save to xorg.conf and after a reboot, my twin view settings remained.

Thanks for the quick fix to this from all the devs involved. :guitar:

---

### Post by jml75 on 2008-11-13
Hi guys,

I have the same problem.

I can get twinview to work fine with nvidia-settings while in Gnome and I'm able to save it to file but I can't get X load start after that when I reboot or restart X.

Do you have any advice on this?

Thanx!

---

### Post by bedge on 2008-12-16
Try this:
[http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/)

-Bruce

---

### Post by XsCode on 2008-12-16
sounds like you had a similar problem to mine with nvidia-settings not saving the conf because it segfaults before writing.  I fixed this by updating to nvidia 180.16 drivers manually

---

