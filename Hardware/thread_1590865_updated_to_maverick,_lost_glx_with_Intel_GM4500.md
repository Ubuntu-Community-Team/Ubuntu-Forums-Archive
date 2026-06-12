---
title: "updated to maverick, lost glx with Intel GM4500"
date: 2010-10-08
forum: Hardware
---

### Post by spotter on 2010-10-08
I updated to maverick, and I lost GLX, unsure what happened.

```
spotter@dent:~$ glxinfo 
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
```

but it seems its using the right driver

```
spotter@dent:~$ xvinfo 
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 95
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
....
```

any ideas?

---

### Post by spotter on 2010-10-08
solved, baed on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/597967](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/597967)

seems the maverick upgrade pulled in nvidia drivers.

This is probably a bug somewhere, but don't know where.

---

