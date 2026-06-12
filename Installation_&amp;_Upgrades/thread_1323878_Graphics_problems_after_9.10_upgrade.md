---
title: "Graphics problems after 9.10 upgrade"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by arobson on 2009-11-12
I just upgraded to 9.10 and am having some graphics issues. If I boot normally everything loads fine and seems normal, but 15-20 seconds after fully booting up, the screen displays a bunch of weirdly colored pixels before going black with a blinking cursor (though no text shows up if I type here). If I move my mouse around I get strange pink boxes showing up as well as patches of white and black lines.

This problem doesn't occur if I boot in recovery mode and manually start X with gdm run (which is how I am typing right now). I tried purging fglrx and reinstalling radeon but that didn't fix anything. Anyone have any ideas?

---

### Post by Mark Phelps on 2009-11-12
You should check the link below to ensure that you did all the stuff necessary to replace the fglrx drivers with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by arobson on 2009-11-12
Did those steps and things actually got worse - now under a normal boot ubuntu informs me that I am running in a low-graphic environment because of missing drivers (EE). Choosing any of the options (continue in low-graphics, troubleshoot, reconfigure, etc.) allows me to boot but doesn't stop everything from going haywire. I'm running a Radeon HD 3200 - this doesn't work with the open source drivers, maybe?

I'm not 100% sure it is a graphics related issue - the entire system might be crashing when the screen starts displaying funky colours. Is there any way I can test this? Furthermore, why is this only an issue in a normal boot, but doesn't show up when I boot into the recovery prompt and run gdm from the command line?

---

