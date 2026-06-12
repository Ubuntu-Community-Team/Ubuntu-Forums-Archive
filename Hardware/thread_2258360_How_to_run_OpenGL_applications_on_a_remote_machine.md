---
title: "How to run OpenGL applications on a remote machine with no physical graphics card?"
date: 2014-12-27
forum: Hardware
---

### Post by hzhou1 on 2014-12-27
I want to run OpenGL applications on Amazon EC2 t2.micro ubuntu instance. This type of instance has no physical graphics card installed. I installed latest mesa from source but I always got errors when running OpenGL applications. For example:

If I run glxinfo, I got:
```
name of display: :1.0
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig
```

If I run glxgears, I got:
```
 Error: couldn't get an RGB, Double-buffered visual
```

If I run glmark2, I got:
```
Error: GLX version >= 1.3 is required
Error: Error: Could not get a valid XVisualInfo!
Error: Error: Couldn't create X Window!
Error: main: Could not initialize canvas
```

I checked the log in /var/log/Xorg.0.log using grep "(EE)" /var/log/Xorg.0.log, the output results are:
```
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.259] (EE) open /dev/dri/card0: No such file or directory
[     8.261] (EE) open /dev/fb0: No such file or directory
[     9.633] (EE) AIGLX: reverting to software rendering
```

As expected, the absence of physical graphics card (represented in Linux as file /dev/dri/card0) 
prvents OpenGL from running and in turn the GLX and X server fails to load these OpenGL applications.
So my questions are:

(1) mesa boasts that it has a module for software simulation of OpenGL operations -- swrast. Does this 
software simulation module only work on a ubuntu machine having a physical graphics card? If not 
(swrast can run without physical graphics card), how should I configure to make mesa work? PS: I build mesa 
with --enable-glx-tls because otherwise swrast_dri.so will fail to be dynamically loaded.

(2) Is there any virtual graphics card software that can feint a graphics card to cheat mesa to
believe that there is a graphics card in the ubuntu system so that it can run properly?

(3) Is there any chance to redirect OpenGL commands issued by these OpenGL applications to another computer (could be Windows)
in the network which installed an nVidia grphics card, have this another computer process the commands and 
return the resulting display back to me (either indirectly through the ubuntu where there is no physical graphics
card or directly to me, bypassing the ubuntu)?

Looking forward for any hint and help. Thank you.

---

