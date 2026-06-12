---
title: "Nexuiz Issue"
date: 2008-08-16
forum: Hardware
---

### Post by Unanimated on 2008-08-16
I really don't think this belongs in this forum, but it is game-related.

Whenever I open Nexuiz (from the site or repos), the menus all work fine. However, once I start the game, I only get about 6-7 fps, my weapon doesn't show up, none of the enemies show up, and there's no sound. Is there a remedy for this?

---

### Post by jpeddicord on 2008-08-16
That sounds like a direct rendering issue (your current driver doesn't support it). I'm moving this to Hardware as you will probably get better answers here.

To start, open a terminal, and post the output:
```
glxinfo | head
```

Also run ```
glxgears
``` for about 30 seconds and post the average framerate it outputs.

---

### Post by Unanimated on 2008-08-16
Here's my glxinfo output:
```
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 96.43.07.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample
client glx vendor string: NVIDIA Corporation

```

And my glxgears average FPS was 14291.833333333.

---

### Post by Unanimated on 2008-08-17
I'm going to try updating the drivers real quick, and see what happens.

---

### Post by Unanimated on 2008-08-17
I just updated them, and the output is the same.

---

### Post by Unanimated on 2008-08-17
bump

---

### Post by Unanimated on 2008-08-17
bump

---

