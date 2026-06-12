---
title: "[SOLVED] Getting PPRacer and ETRacer to run"
date: 2008-07-11
forum: General Help
---

### Post by phantomjoker on 2008-07-11
Very trivial I know - basic also -

I was wondering what the error

> PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de) 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

[COLOR="Red"]*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)[/COLOR]


mean when I try and run all of the penguin racing games...

Thanks guys

---

### Post by hal8000 on 2008-07-11
It means that you havent got a graphics card that is compatible with the Open Graphics Library of accelerated drivers.
If you have an Nvidia or ATI card then you can follow the instructions to install OpenGL support.


Type the following at a terminal
glxinfo | grep "render"

You need direct rendering, a feature of the OpenGL drivers, and you will
probably get information about your graphics card.
Example below:

anc@orac:~$ glxinfo | grep "render"
direct rendering: Yes
OpenGL renderer string: GeForce 7600 GS/AGP/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---

### Post by phantomjoker on 2008-07-11
> **hal8000 said:**
> 
Type the following at a terminal
glxinfo | grep "render"

You need direct rendering, a feature of the OpenGL drivers, and _[COLOR="Red"]you will probably get information about your graphics card[/COLOR]_.


Thanks for the advice - unfortuntly it did not work and instead of graphics information i got the following

> doc@ubuntu:~$ glxinfo | grep "render"
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

 
any more advice? im really stuck.

cheers

---

