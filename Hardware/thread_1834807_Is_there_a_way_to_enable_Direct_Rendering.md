---
title: "Is there a way to enable Direct Rendering?"
date: 2011-08-28
forum: Hardware
---

### Post by aksu_dude on 2011-08-28
So, my problem is that 'direct rendering' is disabled which causes errors when I try to start games on wine.

My GPU is ATI Radeon HD 3450 and I'm using the proprietary drivers which I installed trough the 'hardware drivers' thingy in the administration panel. 

Here's what glxinfo says:
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

This message usually displays when I try to run games trough terminal:
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly

Is there a way to enable direct rendering manually or do I need to install different drivers?

I don't know much about this stuff so I don't know if this was wise but I tried changing the enviroment variable 'LIBGL_ALWAYS_INDIRECT' to 0 but the glxinfo still said the same thing. Also I tried changing the drivers' location because in one case (can't remember the thread) it solved the problem. It didn't work for me though.  

[Here's]("http://ubuntuforums.org/showthread.php?t=310018&highlight=opengl") also another fix but the download link is corrupt.

---

