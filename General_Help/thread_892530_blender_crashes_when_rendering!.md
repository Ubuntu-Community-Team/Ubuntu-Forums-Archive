---
title: "blender crashes when rendering!"
date: 2008-08-17
forum: General Help
---

### Post by eerojms5 on 2008-08-17
and all i get is:

eero@eero-desktop:~$ blender -d
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.45 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Color depth r 8 g 8 b 8
Aux buffers: 0
read file 
  Version 242 sub 4
read file /home/eero/.B.blend
  Version 245 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/eero/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 471
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 470
Software fallback:ctx->Line.StippleFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_mem.c function r300_mem_alloc line 225
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting


any help would be appreciated!

---

