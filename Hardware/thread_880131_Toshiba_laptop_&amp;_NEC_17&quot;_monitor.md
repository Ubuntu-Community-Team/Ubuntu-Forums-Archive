---
title: "Toshiba laptop &amp; NEC 17&quot; monitor"
date: 2008-08-04
forum: Hardware
---

### Post by Jonathan D Miller on 2008-08-04
I inherited a Toshiba laptop from my sister a few weeks ago. Her baby girl sat on the screen and broke it! Other than that it works great. She had it running XP and had a bunch of crap on it, so I decided, since I'm not a Windows user (I'm and OS X guy) that I would install Ubuntu. All that went off without a hitch.

The problem I am having is that I was using an NEC 17" monitor with the laptop when it was running XP, but now that the laptop runs Ubuntu it does not display on the external. I tried messing with the resolution settings in Ubuntu, but that did not work. (The laptop screen is not totally destroyed, so I can do some things on there.)

I'm now working under the assumption that it is a driver issue. Can someone please help me get what I need to make the display work?

---

### Post by K2712 on 2008-08-04
Have you tried to hit Fn+F5 to switch to the external monitor?

---

### Post by Jonathan D Miller on 2008-08-04
I tried fn + f5 but had no luck.

---

### Post by K2712 on 2008-08-05
I know it's probably a pain with a broken screen, but if you could post the contents of your xorg.conf, and the outputs of the following it would be helpful.

```
lspci
```
```
xrandr
```

---

### Post by kdb424 on 2008-08-05
What you should do is try to install ssh and work on it from somewhere else.

---

### Post by lisati on 2008-08-05
On the rare occasions I've had an external monitor hooked up to my Toshiba laptop while running Ubuntu (s-video & the monitor connection) a change to the screen resolution helped things. (this might be tricky if the main screen is damaged)

---

### Post by Jonathan D Miller on 2008-08-05
I can actually use the broken screen pretty well enough. I have tested every resolution and frequency available, but none have done the trick.

---

### Post by Jonathan D Miller on 2008-08-05
**@K2712**
As soon as I get home I will look for that and post its contents here.

thanks!

---

### Post by Norman Grahams on 2008-08-07
Try using xrandr
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")
[http://ubuntuforums.org/showthread.php?t=861643]("http://ubuntuforums.org/showthread.php?t=861643")

To just get the external screen working (cloned, not beside the laptop screen) I didn't need to edit xorg.conf at all.
I switched my laptop (Toshiba) screen off, and the external on, with

xrandr --output LVDS --off --output VGA --auto --same-as LVDS

the "--same-as LVDS" might not be necessary if only using the one screen. I've only just found this myself.

---

### Post by ibgeorgeb on 2009-03-14
Norman, thank a lot for your solution. I finally got an external LCD flat screen monitor to work with my Toshiba 205 tablet. gB

---

