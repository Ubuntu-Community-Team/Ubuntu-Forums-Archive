---
title: "Enemy Territory &quot;Received signal 11, exiting...&quot; and other errors"
date: 2008-08-01
forum: General Help
---

### Post by iJake on 2008-08-01
When running enemy territory, it crashes. The screen becomes distorted (almost like layered steps) and this comes up in Terminal:

```
ET 2.56 linux-i386 Sep 10 2003
----- FS_Startup -----
Current search path:
/home/jake/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3739 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon Xpress Series
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 2.1.7659 Release
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add  GL_EXT_compiled_vertex_array GL_S3_s3tc 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/jake/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/jake/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/jake/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa47a5bfc  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
ERROR: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27961
ERROR: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27962
Hostname: jake-laptop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Received signal 11, exiting...
DOUBLE SIGNAL FAULT: Received signal 2, exiting...
Shutdown tty console
```

What could be the solution? I tried updating it but I haven't go sufficient permissions to move the updated files to the /usr/local/games/enemy-territory folder.

---

### Post by betterhands on 2009-02-09
> **iJake said:**
> When running enemy territory, it crashes. The screen becomes distorted (almost like layered steps) and this comes up in Terminal:

```

Received signal 11, exiting...
DOUBLE SIGNAL FAULT: Received signal 2, exiting...
Shutdown tty console
```.

i get a similar issue after connecting successfully and playing for a bit...if i find what works for me, i'll post it here...
```

Received signal 11, exiting...
Shutdown tty console
[et-sdl-sound] info   : done
```

---

### Post by betterhands on 2009-02-09
unchecking everything in the WINE config was a hint someone gave and it did the trick.

---

### Post by hernol on 2009-02-10
Wow wow wow... same happening to me!
Can you please explain what *"unchecking everything in the WINE config"* means? I don't have wine installed, what should I do? Can't find a solution, and this same game works in my desktop pc (trying my vaio laptop now)

Thanks in advance.

Hernol

---

### Post by betterhands on 2009-02-21
well...after some update, i no longer have any sound and apparently the settings i unchecked in the WINE package was likely coincidence as that's not fixing the issue for me now.  if i get sound to work again for Enemy Territory, i'll be back.

---

