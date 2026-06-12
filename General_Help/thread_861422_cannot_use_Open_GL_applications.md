---
title: "cannot use Open GL applications"
date: 2008-07-16
forum: General Help
---

### Post by GSZX1337 on 2008-07-16
I just recently upgraded my distro to 8.04 and I haven't had any problems with it (My OpenGL problems was happening in 7.10 as well). I cannot open any application or game that uses OpenGL. I'll open Nexuiz and the screen will flash a few times and stop.

Here's the terminal output,
```
gszx1337@G-Man:~$ nexuiz
Nexuiz Linux 09:08:41 Mar 23 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
execing data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1440x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1440x900: Couldn't find matching GLX visual
Desired video mode fail, trying fallbacks...
Initializing Video Mode: fullscreen 1440x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1440x900: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1440x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1440x900: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1440x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1440x900: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x900x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x900: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Quake Error: Video modes failed

```

I also tried ZSNES,
```
gszx1337@G-Man:~$ zsnes32
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Could not set 1280x1024-GL video mode.

```
Although, for some reason, if I use sudo it starts up.

I also cannot use Compiz Fusion. Is there anything that I can do to save this install? I'd prefer not to have to format the partition and install Ubuntu again. 

Thanks in advance,
~GSZX1337

---

### Post by Bachstelze on 2008-07-16
Install your graphics card's drivers.

---

### Post by Viper666 on 2008-07-16
"Couldn't find matching GLX visual" means that the program tried to use a GLX visual that was not available on the X server. 
Might help if you change the color depth to something that's supported

---

### Post by GSZX1337 on 2008-07-23
After getting back to my 'buntu puter, I realized my Restrict driver was disabled. After re-enabling it, I was able to use my OpenGL apps again. :)

Thanks you all for your help,
~GSZX1337

---

