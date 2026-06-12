---
title: "HELP! Screen resolution default won't change!!"
date: 2008-11-06
forum: General Help
---

### Post by nbtrap on 2008-11-06
I'm running the nVidia 177 drivers, and for some reason, every time I restart X, I get an "input not supported" box on my monitor.

So I open a terminal with a shortcut key, type in "sudo xrandr -s 1440x900" and then I can see again (all of which I do without being able to see anything).

My default resolution in nvidia-settings is 1440x900, but for whatever reason, if I type in "sudo xrandr" before changing the resolution, it tells me that X is booting to 900x600, a resolution I guess my monitor doesn't support.  Also, my xorg.conf file doesn't have anything about 900x600 in it.  Please help.

---

### Post by jpoRS on 2008-11-06
Does this help?

[http://ubuntuforums.org/showthread.php?t=968856](http://ubuntuforums.org/showthread.php?t=968856)

jim

---

