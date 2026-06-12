---
title: "libGL, mesa &amp; nvidia"
date: 2011-04-16
forum: Hardware
---

### Post by maxino on 2011-04-16
Hi,
Can someone advise about my system's set-up?
Here it is:

```
maxino@max-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
maxino@max-desktop:~$ glxinfo | grep "server glx vendor string"
server glx vendor string: NVIDIA Corporation
```

From this output I understand that hardware rendering is enabled.

But then, my libGL library points to the mesa ones:

```
maxino@max-desktop:~$ ll /usr/lib/libGL.so
lrwxrwxrwx 1 root root 13 2010-11-26 23:18 /usr/lib/libGL.so -> mesa/libGL.so
```

If I look under /usr/lib/nvidia-current I have another libGL.so:

```
maxino@max-desktop:~$ ll /usr/lib/nvidia-current/libGL.so
lrwxrwxrwx 1 root root 10 2010-10-12 17:48 /usr/lib/nvidia-current/libGL.so -> libGL.so.1
```

This one above should be the one provided by nvidia, right? But it is not the one pointed to by /usr/lib/libGL.so, meaning that if I compile any program containing openGL instructions, I am NOT linking the nvidia library, but the mesa one instead.

I would like to understand if this is the way things are supposed to be? Or should I change the symlink /usr/lib/libGL.so so that it points to the nvidia libGL library?

Thanks for the attention, I am just trying to better understand how this stuff works.

Cheers,

---

### Post by Yellow Pasque on 2011-04-16
Maybe this helps: [http://ubuntuforums.org/showthread.php?t=1730641](http://ubuntuforums.org/showthread.php?t=1730641)

---

### Post by maxino on 2011-04-16
Thanks.

I understand that there are two different sets of headers and libraries: one by mesa and one by nvidia.

```
maxino@max-desktop:~$ locate gl.h
[COLOR="Red"]/usr/include/GL/gl.h[/COLOR]
/usr/include/SDL/SDL_opengl.h
/usr/include/nvidia-current/CL/cl_gl.h
[COLOR="red"]/usr/include/nvidia-current/GL/gl.h[/COLOR]
/usr/include/python2.6/pygame/pgopengl.h
/usr/share/doc/libsdl1.2-dev/docs/html/guidevideoopengl.html
/usr/share/ubuntu-artwork/home/locales-ubuntu/index-gl.html

maxino@max-desktop:~$ locate libGL
/usr/lib/libGL.so
/usr/lib/libGLEW.so.1.5
/usr/lib/libGLEW.so.1.5.2
/usr/lib/libGLU.a
/usr/lib/libGLU.so
/usr/lib/libGLU.so.1
/usr/lib/libGLU.so.1.3.070900
[COLOR="Red"]/usr/lib/mesa/libGL.so[/COLOR]
/usr/lib/mesa/libGL.so.1
/usr/lib/mesa/libGL.so.1.2
[COLOR="red"]/usr/lib/nvidia-current/libGL.so[/COLOR]
/usr/lib/nvidia-current/libGL.so.1
/usr/lib/nvidia-current/libGL.so.260.19.06
```

But it seems that the default ones for compiling are the mesa ones.
Should I redirect my default headers & libs to the nvidia ones?

Just trying to understand how to set my system for the best performance...

Thanks,

---

