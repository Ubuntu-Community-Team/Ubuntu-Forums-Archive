---
title: "libGLcore.so.1: cannot open shared object file"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by orcalover on 2007-02-09
I have followed all of the instructions from the user guide and these forums attempting to get my NVIDIA graphics card to work. However, no matter what I do, when I run:

```
glxinfo | grep rendering
```

I get this error:

```
glxinfo: error while loading shared libraries: libGLcore.so.1: cannot open shared object file: No such file or directory
```

This is the graphics card that I have installed:

e-GeForce 6200LE 128MB DDR P/N: 128-TC-2N27-SX

Can someone please tell me what I'm doing wrong.

---

### Post by orcalover on 2007-02-09
This is a section of the log file, not sure what it indicates, but it looks like everything is loading properly...

```
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy

```

---

### Post by orcalover on 2007-02-09
RESOLVED!

I resolved this issue by using the Envy script. Everything seems to be working fine. 

The script can be found here:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I found the above URL from this forum post:

[http://ubuntuforums.org/showthread.php?t=347934&page=2]("http://ubuntuforums.org/showthread.php?t=347934&page=2")

Sean

---

