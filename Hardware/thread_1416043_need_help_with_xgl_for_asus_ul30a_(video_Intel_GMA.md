---
title: "need help with xgl for asus ul30a (video: Intel GMA 4500MHD)"
date: 2010-02-25
forum: Hardware
---

### Post by clocksmith on 2010-02-25
My ultimate goal is to get a fancier looking desktop for ubuntu 9.10 through

System > Preferences > Appearence

I am trying to use compiz-fusion.

I have compiz-fusion and xgl installed, but it seems that xgl is not working properly.

here is what i get when i type "glxinfo"

> 
name of display: :0.0
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
EDIT: I used to be able to select "Normal" and "Extra" Visual Effects, but now it is stuck on None
and if I try to change it it says "Desktop effects could not be enabled"

I am worse than I started

EDIT:

Nothing related to graphics works now.
I tried running a simple c program that draws points to the screen using glut and that won't even run

./new
freeglut (./new): OpenGL GLX extension not supported by display ':0.0'

How can I get my video card working like it was when I first installed linux?

---

### Post by EliasKesh on 2010-04-17
I'm in the same boat . Did you resolve the problem ?

Elias

---

### Post by Meizirkki on 2010-10-15
I had a same problem on my 50VT, it seems that the nvidia drivers must be uninstalled for intel 3D acceleration to work.

---

