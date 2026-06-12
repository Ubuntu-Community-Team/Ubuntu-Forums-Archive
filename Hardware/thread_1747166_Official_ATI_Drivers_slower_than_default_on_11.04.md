---
title: "Official ATI Drivers slower than default on 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by BartjeNL on 2011-05-02
To begin with I'm pretty new to this, and I'm sorry if this has been asked a hundred times but I can't seem to figure this out.

When I install Ubuntu 11.04 (i have a HD5850), the 'default' video driver (whatever that might be) runs great, ran a benchmark (glmark02) and got 60fps on every test. Now the problem with this default driver is that i can't seem to run any really advanced applications/games (like the quake 4 demo, trine game). Also i see alot of artifacts when I run things like Spotify on Wine.

Now I installed the latest 11.4 ATI Driver, and the artifacts are gone in the Wine applications, and I can run the applications/games that I couldn't before but they are so damn slow! The whole gnome interface is alot slower too (I'm running classic) and the glmark02 benchmark gave me around 25fps this time.

So my question is, how the hell is that possible and is there any way to fix it? And why isn't it possible to play those games on the default driver thats installed?

I would really appreciate if someone could answer those questions for me.

---

### Post by BartjeNL on 2011-05-02
Solved it! For the people who were experiencing the same problem as me: download the compizconfig settings manager. Go to general/openGL and disable Sync to VBlank!

---

### Post by gcbzzzz on 2011-05-02
Didn't change anything to me disabling vsync.

With default drivers, i can only use 1024 resolution. anything bigger, gives me a 1024 square and garbled graphics around. but i have 3d.

enabling the ATI drivers enabled me to run at 1900x1600, but 3d is weird.

it's pretty decent with compiz.  hitting the keys for the scale (exposé) plugin, works fine. it's fast.  but running glxgears, gives me the weirdest results... it's like 1.5FPS visually, with lots of flickering in the window... but the program output says something like 68FPS...

also, ubuntu refused to let me use unity after i enabled the ATI driver. now i can only use regular gnome desktop (i was going anyway since unity does not respect ANY keyboard shortcuts and that a major indicator that it's not well tested)  but that only adds to the weirdness. since 3d in compiz works just fine.

---

### Post by gcbzzzz on 2011-05-02
```
export LIBGL_DEBUG=verbose

(0) ~
wrotenote-lx$ glxinfo 
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrastg_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrastg_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrastg_dri.so failed (/usr/lib/fglrx/dri/swrastg_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrastg_dri.so
libGL error: reverting to indirect rendering

```

now i'm trying the fix described here [http://ubuntuforums.org/showthread.php?t=1449620](http://ubuntuforums.org/showthread.php?t=1449620)

---

### Post by gcbzzzz on 2011-05-02
aaaaaaaaand it worked!

---

