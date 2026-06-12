---
title: "IBM X31 screen problems with composite on Ubuntu 9"
date: 2010-03-16
forum: Hardware
---

### Post by kinsago on 2010-03-16
Hi Guys.
Just installed Ubuntu 9.1 on my IBM X31 ad I'm having problems running Xcompmgr and Compiz. 

Running Compiz causes certain windows (like the compiz config windows) to appear distorted and anything that requires a composite manager to do the same. When I run Xcompmgr (with or without compiz) the screen goes haywire - it seems like it's trying to run at an unsupported refresh rate, the screen is keeping the same resolution as I can 'access' the menus but the display is horribly interlaced. I'm trying to get avant-window-navigator running.

I know that the X31 only has a 16mb graphics card so it's not exactly 'new-tech' however I can use Xcompmgr under Debian lenny without a problem and even compiz runs albeit a little slowly.

If I install Ubuntu from version 8, I can update to 9.04 and everything seems to run ok. It's only once I get to 9.1 that everything goes wrong. 

BTW I switched to Ubuntu from Debian because Ubuntu seems to have better support for my internal bluetooth card, a few nicer features and a little bit more user-friendly but if I can't get xcompmgr or compiz running I'll have to switch back.

Cheers

Kinsago

---

### Post by joonR on 2010-03-22
In terminal,

$ sudo gedit /etc/X11/xorg.conf

In my case the file was blank.
Paste the following and save the file:

```
Section "Device"
       Identifier "m6-radeon"
       Driver "radeon"

       # Enabling EXA fixes the notifications
       Option "RenderAccel" "false"
       Option "AccelMethod" "EXA"

       # Xorg will gobble CPU unless you add...
       Option "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       Identifier "laptop-panel"
       Device "m6-radeon"
       DefaultColorDepth 24
       SubSection "Display"
           Depth   1
           Modes "1024x768"
           #Virtual 1024 768
       EndSubSection
EndSection

Section "Extensions"
        # I don't use the compositing settings, so off!
        Option "Composite" "Disable"
EndSection

```

Worked for me. 

from [http://ubuntuforums.org/showthread.php?t=1305279&highlight=x31+graphics&page=3](http://ubuntuforums.org/showthread.php?t=1305279&highlight=x31+graphics&page=3) thread (see #22)

Hope this is helpful.

Joon.

---

