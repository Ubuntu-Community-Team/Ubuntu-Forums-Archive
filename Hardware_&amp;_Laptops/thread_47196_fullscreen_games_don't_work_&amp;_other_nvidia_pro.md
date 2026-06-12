---
title: "fullscreen games don't work &amp; other nvidia problems"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by bernardfrancois on 2005-07-07
I have a few problems with my nvidia driver (official one, for gforce4 ti4800se).
I've three metamodes set (**"NULL, 1280x1024; 1280x1024, 1280x1024; 1280x1024, NULL"**).
If I set it to one of the metamodes with one screen disabled, I get a desktop of 2560x1024 on one of the monitors, which scrolls when I move the mouse pointer to the side of my screen. To avoid that problem, I can change my screen resolution in the gnome menu. There I can choose between 2560x1024 and 1280x1024. If I set it to 1280x1024, I cant reach the metamode with both monitors enabled; therefore I have to change the screen resolution in the gnome menu.
Also, the login screen is always set to 2560x1024 on one screen if I use a metamode with one of the monitors disabled.

This is not really the biggest problem, but whats irritating me most is that I can't play any games in full screen.

This is the console output that I get for some games:
```

bernardfrancois@ubuntu:~$ trackballs
Welcome to Trackballs. 
Using /usr/share/games/trackballs as gamedata dir
Attempting to open mixer...open /dev/sequencer: No such file or directory
successfull
Trackballs initialization successfull
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xce
  Serial number of failed request:  131
  Current serial number in output stream:  133


bernardfrancois@ubuntu:~$ armagetron
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
Couldn't set video mode: Couldn't find matching GLX visual
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xce
  Serial number of failed request:  116
  Current serial number in output stream:  118


bernardfrancois@ubuntu:~$ frozen-bubble -fs
        [[ Frozen-Bubble-1.0.0 ]]

  http://www.frozen-bubble.org/

  Copyright (c) 2000, 2001, 2002, 2003 Guillaume Cottenceau.
  Artwork: Alexis Younes <73lab at free.fr>
           Amaury Amblard-Ladurantie <amaury at linuxfr.org>
  Soundtrack: Matthias Le Bidan <matthias.le_bidan at caramail.com>
  Design & Programming: Guillaume Cottenceau <guillaume.cottenceau at free.fr>
  Level Editor: Kim and David Joham <[k|d]joham at yahoo.com>

  Sponsored by MandrakeSoft <http://www.mandrakesoft.com/>

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License version 2, as
  published by the Free Software Foundation.

[SDL Init] SDL_Init 65535
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xce
  Serial number of failed request:  98
  Current serial number in output stream:  100


bernardfrancois@ubuntu:~$ ltris
LTris 1.0.6
Copyright 2002-2004 Michael Speck
Published under GNU GPL
---
Looking up data in: /usr/share/games/ltris
Mode 640x480x16 Window valid
Mode 640x480x16 Fullscreen valid
open /dev/sequencer: No such file or directory
Saving highscore chart in: /var/games
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xce
  Serial number of failed request:  123
  Current serial number in output stream:  125
bernardfrancois@ubuntu:~$ 

```

---

