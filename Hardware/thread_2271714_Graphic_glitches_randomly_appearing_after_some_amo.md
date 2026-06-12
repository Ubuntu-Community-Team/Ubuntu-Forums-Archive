---
title: "Graphic glitches randomly appearing after some amount of time"
date: 2015-04-01
forum: Hardware
---

### Post by Barteks2x on 2015-04-01
Recently I noticed that after my laptop is running for some time weird graphic glitches appear. It's visible mostly in games, steam GUI and google chrome/chromium. It works correctly when using bumblebee (optirun), but because of other bug I can't use it after some time from (re)booting. Everything works on windows, even after long time, so it doesn't seem to be damaged GPU. The effect is not noticable with glxgears. Reboot always fixes it for some time.

It's Lenovo Ideapad Z510 laptop.
CPU: Intel core i5-4200M 2.50GHz
GPU: Intel + Nvidia Geforce GT 740M (optimus)

Xubuntu version: 14.10

//Update 10th may 2015: If anyone has the same problem and is looking for help: it's still not fixed. Nobody seems to know what causes it. Sometimes it disappears for a few weeks only to appear a few minutes after restart. In this situation it's pointless to bump it again. If someone has a solution, unless it's fixed by some update - post it or at least PM me, even if it's one year later.

//UPDATE 10th June 2015: I discovered that my HDD isn't in very good state. SMART shows 12 End-to-end errors right now. It was probably the root cause of this problem, but I will probably never be sure. Any package could be corrupted. I don't think it makes sense to try to repair it. As the laptop is still under warranty I'm going to return it after I backup all my data.

---

### Post by kerry_s on 2015-04-01
you try disabling composting in windows tweaks ?

---

### Post by Barteks2x on 2015-04-01
It's already disabled

---

### Post by bolvan on 2015-04-02
What window manager do you use ? Try temporary replace it with some basic one. Like openbox.
Try switching between proprietary nvidia drivers and nouveau

---

### Post by Vladlenin5000 on 2015-04-02
> **bolvan said:**
> What window manager do you use ? Try temporary replace it with some basic one. Like openbox.
Not really a good idea...

> Try switching between proprietary nvidia drivers and nouveau
This could be a good idea (for troubleshooting only) *if* the system _wasn't_ one of those with hybrid graphics...


The following may or may not solve it and considering it can be easily reversed it's worth trying:
- Install *ccsm* then find the solutions button and select the "Force full redraw..." option.

---

### Post by Barteks2x on 2015-04-03
Nothing changed. Or do I need to restart to see effects? (there was no "apply" button, or any onformation about when will I see effects, so I assume it should be instant).
Any other ideas? Sometimes I'm running it only on battery and using nvidia gpu just to use web browser isn't a good idea.

---

### Post by Barteks2x on 2015-04-09
bump

---

