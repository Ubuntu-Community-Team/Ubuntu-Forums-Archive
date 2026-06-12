---
title: "extension &quot;GLX&quot; missing on display &quot;:0.0&quot;"
date: 2010-07-21
forum: Hardware
---

### Post by Yoshiie-Bear on 2010-07-21
I recently installed Ubuntu studio onto my hp compaq nx9105 laptop and have been finding it really great, have got most of the things I need to work and have most of the drivers, I think.

Yesterday I downloaded UrbanTerror an online fps that works on Linux.
I got to the point of installing it using the terminal but it failed to install and gave me the error message:
SDL_SetVideoMode failed: Couldn't find matching GLX visual"

I googled the problem and it said to type "glxinfo | grep render" into the terminal to see if the GLX was installed.
It wasn't installed so I sudo apt-get and installed it, then I did the previous bit of code again to check.
And this is what it gave me:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I think the problem is that I do not have the graphics driver installed but as I am new to ubuntu I am uncertian.
Any ideas of solutions please?

Many thanks.

---

