---
title: "No nvidia drivers after upgrade to Maverick"
date: 2010-10-04
forum: Hardware
---

### Post by Masquerade on 2010-10-04
Hey there,

I recently upgraded to the Maverick RC that was promoted on the ubuntu.com front page by using the usual "update-manager -d" procedure.

There must have went something wrong while installing (I think my harddrive messed up at some point and I had to restart the installation, whatever) because I now can only boot in safe graphics mode. 

I have a nvidia GeForce 5200

According to the output, I lack of graphics drivers: 

```
benjamin@desktop:~$ glxinfo
name of display: :1.0
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
benjamin@desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't get an RGB, Double-buffered visual
benjamin@desktop:~$ 

```

```
benjamin@desktop:~$ compiz --replace
Xlib:  extension "GLX" missing on display ":1.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

Launching fallback window manager


```

However, I have 

nvidia-current nvidia-current-modaliases nvidia-common nvidia-settings

installed.

(nvidia-settings still talks about a xorg.conf. isnt that obsolete?)

So, whats going wrong here?
Thanks a lot in advance!

---

### Post by Masquerade on 2010-10-04
Never mind. Not possible yet. Nouveau drivers work for 2D though.

---

### Post by xvenom89 on 2010-10-05
-deleted-

---

### Post by EcliptuX on 2010-10-07
I have the same problem with compiz.
I can't use the 3D effects, and when I'm lauching by hand compiz, I have this :
```

$ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

---

