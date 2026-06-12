---
title: "gnome/xorg freeze/crash"
date: 2008-08-23
forum: General Help
---

### Post by pippo_jedi on 2008-08-23
hello everybody,
I have a problem: sometimes, it seems at random, gnome disappears and I'm left with a blanck screen with "@l" or something like that on it.
it seems to hang randomly, sometime after 10 minutes sometimes after several hours nothing bad happens...

switching to the other consoles works and I have terminal access, but
ctrl+alr+backsp doesn't reboot the graphical interface.

running top I see tha xorg is working at 99%cpu usage and that the time since is up goes faster than normal (is my xorg traveling in the future?), trying to kill it doens't work and i'm forced to reboot. 

I do not know well the inner workings of xorg and gnome, so I don't know what to look for in the logs and the like...

anyone can help me?

pippo_jedi

---

### Post by pippo_jedi on 2008-08-24
anyone can help me?

---

### Post by gjoellee on 2008-08-24
this might help: [http://kshoster.net/?c=tipsandtricks&h=xfix](http://kshoster.net/?c=tipsandtricks&h=xfix)

---

### Post by pippo_jedi on 2008-08-24
> **gjoellee said:**
> this might help: [http://kshoster.net/?c=tipsandtricks&h=xfix](http://kshoster.net/?c=tipsandtricks&h=xfix)

thank you for your time, but I' don't undestand: the code on the page just turns off the pc... and the text says something about removing the graphic card, it says nothing about discovering errors...

bye bye

---

### Post by pippo_jedi on 2008-09-20
sorry for the bump, but the problem persists.

from my experience I'd say it's something with flash:
when surfing when I hit a page with flash sometimes gnome stops working...
I have terminal access tough, so if anyone has a tip to see what's happening, what processes are working or not, HOW to make gnome restart, it wuold be very helpful

I mean: i'm living with an instable linux env.! I CAN'T STAND IT! ;)

---

### Post by cicatrix1 on 2008-10-08
I'm having the exact same problem.  Sometimes I'm fine for days.  Are you still having the same issues?  I know this is 2 weeks old, but it's the only thread I've found on these forums that seems to describe exactly what's happening to me.

Let's try to establish a list of common items.

My setup:
-Lenovo Thinkpad T60 with ATI mobile x1300
-fglrx drivers installed from envy
-compiz-fusion, slightly customized via ccsm, running fusion-icon
-pulse-audio

Xorg errors:

$ egrep 'WW|EE' /var/log/Xorg.0.log
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx(0): GetVBEMode failed
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(WW) fglrx(0): Probed monitor is 340x270 mm, using Displaysize 305x228 mm
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
. . . (more just like the above 2 with different hex values)

---

