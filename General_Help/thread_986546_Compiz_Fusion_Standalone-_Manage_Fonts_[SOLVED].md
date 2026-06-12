---
title: "Compiz Fusion Standalone- Manage Fonts [SOLVED]"
date: 2008-11-18
forum: General Help
---

### Post by Locutus_of_Borg on 2008-11-18
I have just set up compiz fusion to run by itself without a desktop environment and would like to make my fonts look more like how I had them set up with xfce.

Is there any way to do this?

Thanks.


well, that was quick...

use lxappearance to manage gtk apps' fonts


Would delete this if given the option...

---

### Post by loomsen on 2008-11-18
But why? 

Share please... Interested in how/what you did actually...

---

### Post by Locutus_of_Borg on 2008-11-18
> **loomsen said:**
> But why? 

Share please... Interested in how/what you did actually...

Why?
To be able to use all the cool features of compiz without all the unnecessary bloat of xfce/gnome/kde. Also, it loads pretty damn fast without all the additional things being started by a full desktop environment- Think Openbox that spins around and wobbles.

I did it by creating these two files

/usr/local/bin/start-fusion.sh
```

#!/bin/bash
# Any programs run from this script MUST have an '&' EXCEPT the last line
# chmod 755 this script once you've created it
# You can use the panel of your choice or even compiz-deskmenu, depending on what you have installed.
# gnome-panel is  used here.
# Fusion-icon of course starts it's selected Window Manager, edit as you see fit but remember the rule above.

sleep2 && pypanel&
xterm&
fusion-icon
```

and   

/usr/share/xsessions/fusion.desktop
```
[Desktop Entry]
Encoding=UTF-8
# This is the name you'll see for the session in gdm
Name=Fusion
# This is the comment
Comment=Compiz Fusion Standalone
# The command
Exec=/usr/local/bin/start-fusion.sh
Type=Application
```

then choosing fusion from gdm login manager > sessions

Pretty awesome, but will have to do a few more things before it is quite right

---

### Post by loomsen on 2008-11-18
My why was related to

> 
Would delete this if given the option...


I'm aware why one would like to do this ^^ :)

Actually I'm going thinking to build a custom debian for my arch.
Just one thing tho, fusion-icon will start a shell-script for emerald as well. One major problem is to get fusion-icon start its window-manager and its window decorator at once. I noticed, if there's an item starting up after fusion-icon, but before compiz, this will massively increase startup time. 
See the shots:
[[img]http://www.ubuntu-pics.de/thumb/5963/screenshot_02_83MEOl.png[/img]](http://www.ubuntu-pics.de/bild/5963/screenshot_02_83MEOl.png)

And this was earlier today:
[[img]http://www.ubuntu-pics.de/thumb/5925/screenshot_14_K3FF25.png[/img]](http://www.ubuntu-pics.de/bild/5925/screenshot_14_K3FF25.png)

And after removing gnome-screensaver:
[[img]http://www.ubuntu-pics.de/thumb/5926/screenshot_15_25ABnd.png[/img]](http://www.ubuntu-pics.de/bild/5926/screenshot_15_25ABnd.png)


It's not the actual time it takes to show up and be available, but the time to fully initiate. I'm not sure how to figure this out, maybe some kind of postlogin / presession script or so, like I'd want to have for my nvidia-settings as well. Not the ones specified in xorg, but the per-user settings, like digital vibrance, antialiasing and such. 
Wouldn't be to bad to have these settings activated prior to launching fusion-icon too, cause fusion-icon would directly initiate screen with full settings. Stuff like that actually still keeps me thinkin instead of building...

---

### Post by gillamonster on 2009-03-06
Nice thanx.. any idea how to recover right click functionality to bring up XFCE menu?

---

### Post by flowheat on 2009-03-12
Try compiz-deskmenu.

[http://forum.compiz-fusion.org/showthread.php?t=7070]("http://forum.compiz-fusion.org/showthread.php?t=7070")

---

