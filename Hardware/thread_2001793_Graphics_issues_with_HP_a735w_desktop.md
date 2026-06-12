---
title: "Graphics issues with HP a735w desktop"
date: 2012-06-11
forum: Hardware
---

### Post by SketchMan3 on 2012-06-11
I've tried running supertuxkart on my HP pavilion with Ubuntu 10.04 installed, but the fonts are all messed up on some items, and the text doesn't show up at all on the menu buttons. It also crashes whenever I go to a screen with 3D graphics.

Also, I tried playing Assault Cube, and it crashes right after the loading screen, once it begins to load the 3D game environment.

I decided to try running Assault Cube from terminal to get the error message, and this is what came up:


```
Using home directory: /home/sketchman3/.assaultcube_v1.04
current locale: en_US.utf8
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
init: video: misc
init: gl
Renderer: Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE (VIA Technology)
Driver: 1.2 Mesa 7.7.1
init: console
init: sound
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Audio devices: PulseAudio Software, ALSA Software, OSS Software
Sound: PulseAudio Software / OpenAL Soft (OpenAL Community)
Driver: 1.1 ALSOFT 1.12.854
init: cfg
init: models
init: docs
init: localconnect
read map packages/maps/official/ac_sunset.cgz rev 7 (240 milliseconds)
Sunset Reserve - By R4zor
loaded textures (995 milliseconds)
loaded mapmodels (120 milliseconds)
loaded mapsounds (1401 milliseconds)
game mode is "TDM"
init: mainloop
Welcome to AssaultCube
Developed by 'Rabid Viper Productions'

Use the below menu to change some necessary settings...

Further help & information can be found in your README, which is inside your AssaultCube directory.
stacktrace:
/usr/lib/games/assaultcube/ac_client(_ZN12signalbinder11stackdumperEi+0x26) [0x814b456]
[0xd08400]
/usr/lib/dri/unichrome_dri.so(+0x144cc5) [0x113ecc5]
/usr/lib/dri/unichrome_dri.so(+0x1468c3) [0x11408c3]
/usr/lib/dri/unichrome_dri.so(_mesa_CopyTexSubImage2D+0x21c) [0x10a3c1c]
/usr/lib/games/assaultcube/ac_client(_Z11drawminimapii+0x519) [0x80e1169]
AssaultCube error (11) ()
OpenAL Error (A004): invalid operation, line 352
OpenAL Error (A004): invalid operation, line 352
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 16 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 4 Buffer(s)
```

---

