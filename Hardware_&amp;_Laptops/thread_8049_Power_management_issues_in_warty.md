---
title: "Power management issues in warty?"
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by word_virus on 2004-12-13
I'm really quite smitten with Ubuntu linux but am having a problem with power management.

After initial install, the screen saver would come on after ten minutes, run for ten minutes, and blank.  Afterwards no amount of mouse-shaking or keyboard pounding would wake up the machine.  Both the box and monitor still on, but no HD status lights, nothing.  Had to hit reset switch to reboot machine (will not respond to Ctrl-Alt-Del).

Disabled the disply power management features in Computer -> Screen Saver -> Advanced .  This helped.  Now, screen saver comes on after ten minutes, will cycle several times (up to about an hour) and blank.  But still same problem as before - can't wake it up and have to reset.  

Are there additional power management features I need to disable that I'm just not seeing in the Gnome menu?  Anyone experienced this?

Spec:
ASUS P4P800
Intel 2.4Ghz P4
512MB 133Mhz DDR DIMM
ATI Radeon 8500
15" NEC Flatscreen CRT

---

### Post by jdong on 2004-12-13
Did you try please and thank you? LOL, j/k!


Hmm, try taking out "Option DPMS" from /etc/X11/XF86Config-4, from the Monitors section.

---

### Post by Averatec5400 on 2004-12-15
I thought Imight have this issue,but hit Ctrl+Alt+f7 and your GUI will come back.

Dunno if that will work for you, but it did for me (I use the f2 terminal for folding@home, so I am used to switching anyway)

---

### Post by word_virus on 2004-12-26
[QUOTE=jdong]Hmm, try taking out "Option DPMS" from /etc/X11/XF86Config-4, from the Monitors section.[/QUOTE]

Thanks for the tip!  Gave that a try, but unfortunately it didn't help.  Eventually had to just turn off the xscreensaver daemon, which seems to have fixed it.

---

