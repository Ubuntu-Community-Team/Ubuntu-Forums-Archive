---
title: "I have to restart X to get a projector to work"
date: 2008-09-18
forum: Hardware
---

### Post by Doughy on 2008-09-18
Does anyone know why I have to restart X (CTRL+ALT+BKSP) to get a projector to work with Ubuntu?  I have to plug in the projector, then restart X, then re-login, then restart my presentation.  I was giving a talk at a professional conference and it was embarrassing that my linux machine didn't work right away when I plugged in the projector.  One judge even came up to me and said "Don't give presentations on Linux" when I was done.  Great....

Anyone know if this issue will be fixed?  Links to bugs or future plans?  Thanks.

---

### Post by chewearn on 2008-09-18
First obvious question is: what graphics card do you have (Intel, ATI, NVIDIA)?

If in doubt, run this command, post the output here:
```
lspci | grep VGA
```

---

### Post by Doughy on 2008-09-18
> **chewearn said:**
> First obvious question is: what graphics card do you have (Intel, ATI, NVIDIA)?

If in doubt, run this command, post the output here:
```
lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by chewearn on 2008-09-18
Ah, it should be relatively easy to hack around the problem for this Intel graphics.  Note: there are bugs filed for fixing all these, but it seemed to be slow going in the launchpad.

I found this webpage to be helpful in *fixing* Intel graphics: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Unfortunately, the Ubuntu screen resolution utility doesn't work so well, so it is better to use command line xrandr.

First you define a large virtual screen.  I recommend the current "working" max, which is 2048x2048.  You have to edit xorg.conf and add these lines under: Section "Screen":

```
SubSection "Display"
     Vrtual 2048 2048 
EndSubSection
```You only need to do this once.  Restart Xorg after changing the file.

Now, you can set dual screen dynamically.  Some example commands:

Find out detected displays:
```
xrandr -q
```Set dual screens; external screen to the right of internal screen:
```
xrandr --output LVDS --auto --output VGA --auto --right-of LVDS
```Set back to single screen:
```
xrandr --output LVDS --auto --output VGA --off
```It just happened I was mucking around with the same thing yesterday, and was planning to write a comprehensive blog post about this fix.  Look out for it, if you are interested.

---

