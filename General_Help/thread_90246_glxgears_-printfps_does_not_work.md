---
title: "glxgears -printfps does not work"
date: 2005-11-14
forum: General Help
---

### Post by tig4 on 2005-11-14
Well,

To begin with I'm trying to install Cedega. I ran all the installs and when i try the OpenGL test, it returns that OpenGL is not working (or installed). Ihave an Nvidia ti4600 and I have installed all the drivers for it:

nvidia-glx
nvidia-settings

however it still will not work. So i was reading on the transgaming forums and they were saying to try to run glxgears -fpsprint. But when I do that, it returns an error:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


Any thoughts?

Tig

---

### Post by MichaelM on 2005-11-14
Just a thought: Does your xorg.conf include```
Load     "glx"
```

---

### Post by tig4 on 2005-11-14
[QUOTE=MichaelM]Just a thought: Does your xorg.conf include```
Load     "glx"
```[/QUOTE]

Yes it is in there.

---

### Post by MichaelM on 2005-11-15
OK, in the device section of your xorg.conf, what driver does it list for your video card?  If you've installed the drivers, it should be "nvidia".

---

