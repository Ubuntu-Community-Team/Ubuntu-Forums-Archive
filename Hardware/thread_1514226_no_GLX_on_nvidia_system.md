---
title: "no GLX on nvidia system"
date: 2010-06-20
forum: Hardware
---

### Post by leptogenesis on 2010-06-20
Several months ago while my box was (I think) Jaunty, I was running compiz fine using my nVidia Geforce 260M.  I then disabled compiz and uninstalled the nVidia driver I got through ubuntu's hardware drivers, replacing them with drivers supporting nVidia cuda.  Those drivers are gone now--I'm now using nvidia-current (which is apparently version 195.36.24, though I'm not sure if that's nVidia's version or a number the Ubuntu devs came up with; I also have nvidia-glx-185 instaled which is also listed as version 195.36.24).  

However, it's two upgrades later and I've found a need to use Blender, but this is what I get when I start it:

```
Compiled with Python version 2.6.5.
Checking for installed Python... got it!
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x4f53492e
  Serial number of failed request:  33
  Current serial number in output stream:  34

```

'compiz --replace' now gives me:

```
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

And finally, 'glxinfo' gives me:

```
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

I can use vdpau with mplayer just fine, so my drivers can't be *that* screwed up.  What the heck is going on here?

---

### Post by leptogenesis on 2010-06-23
bump

---

### Post by leptogenesis on 2010-06-30
Fixed it.  I guess the drivers from nvidia's website don't quite clean up after themselves.  Answer was here:

[http://ubuntuforums.org/showthread.php?t=1505486](http://ubuntuforums.org/showthread.php?t=1505486)

---

