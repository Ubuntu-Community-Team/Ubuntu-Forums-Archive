---
title: "howto install dirextx ???"
date: 2008-09-09
forum: General Help
---

### Post by byglajs on 2008-09-09
Hi. I want install compiz-fusion, but it dont work directx. I have Kubuntu Hardy Heron remix with KDE 4. NB Acer Extensa 5210 with integrated intel graphics card.
If i use:
```
glxinfo | grep rendering
```
I will get :
> 
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

what is the problem ?? pls :?

---

### Post by ripps818 on 2008-09-09
First, Linux doesn't use DirectX, only Microsoft uses it. Linux uses OpenGL.

Second, it looks like OpenGL isn't working with your video card.

I've never used Kubuntu, or kubuntu remix, so I'm not sure how to install the proper drivers. I always thought intel cards should work out of the box. Just wait till someone else can help you, or install xchat and ask someone in the #ubuntu chatroom for help.

---

### Post by tuxxy on 2008-09-09
What is your video chip

---

### Post by ripps818 on 2008-09-10
Open gnome-terminal.
Type in "lspci -v >> output.txt".
Attach the ouput.txt to your next post.

This will tell us what your hardware is.

---

### Post by byglajs on 2008-09-10
Thank you for answers. There is lspci :
[http://rapidshare.com/files/144046928/output.txt.html](http://rapidshare.com/files/144046928/output.txt.html)

---

