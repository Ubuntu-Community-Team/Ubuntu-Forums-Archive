---
title: "[SOLVED] Ach! OpenGL support fried"
date: 2008-09-11
forum: General Help
---

### Post by rerendered3 on 2008-09-11
This seemingly came out of nowhere...
It seems that my OpenGL configs (dependencies, something) are out of whack. I tried running Wolfenstein: ET, it crashed and I removed it. I tried running OpenArena and got this

```
rice@rice-laptop:~$ openarena
ioQ3 1.33+oa linux-i386 Oct 28 2007
----- FS_Startup -----
Current search path:
/home/rice/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (76 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3573 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

Any ideas?

---

### Post by overdrank on 2008-09-11
Hi and the error shows you are using Mesa. What is the model of the graphics card and did you install the drivers?

---

### Post by rerendered3 on 2008-09-11
I have an ATI Raedon Mobility U1 graphics card and yes, I have the drivers installed.

---

### Post by rerendered3 on 2008-09-12
I rebooted my machine and the problem was fixed. I'll search the log files to see what happened.

---

