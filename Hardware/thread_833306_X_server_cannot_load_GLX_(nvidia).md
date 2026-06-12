---
title: "X server cannot load GLX (nvidia)"
date: 2008-06-18
forum: Hardware
---

### Post by redsymbol on 2008-06-18
Hi,

I'm so far having trouble getting my graphics card to support 3D.  I think I have traced it down to some issue with GLX; the output of glxinfo contains many lines of the form:

```

Xlib:  extension "GLX" missing on display ":0.0".

```

Also one line says:
```

Error: couldn't find RGB GLX visual

```

It's an nVidia GeForce 8400M GS, installed in a Dell Vostro 1500:
```

amax@lucky:/etc/X11 lspci|grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)

```

I'm running Kubuntu 8.04 with a 64 bit kernel.

I found one interesting error line in /var/log/Xorg.0.log:
```

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

(I did not see any relevant warnings.)

I have tried many permutations of xorg.conf, with no progress yet.  Currently I am just using what dexconf created, via 'dpkg-reconfigure -phigh xserver-xorg' or 'dpkg-reconfigure -phigh xserver-xorg-core' (unfortunately I don't recall which - if needs be I can recreate it).

I have the following nvidia packages installed:
```

amax@lucky:/etc/X11 dpkg -l 'nvidia-*'  | grep '^ii'
ii  nvidia-glx-new                             169.12+2.6.24.13-19.42                             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                  NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1                              Tool of configuring the NVIDIA graphics driv

```


I'm able to use an external monitor and high resolution - the only
thing missing is the more advanced features of the video card,
including 3d acceleration.  Any advice or suggestions on what to look into next is appreciated.

Thanks,
Aaron

---

### Post by redsymbol on 2008-06-18
I've attached the Xorg.0.log and xorg.conf.

It appears that glx is being loaded - good:
```

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX

```

Apparently X is loading the "nv" module.  That's different from the "nvidia" (restricted) module, right?
```

(II) Matched nv from file name nv.ids in autoconfig
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.1.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0

```

---

### Post by hitmanh on 2008-06-19
I'm seeing the same issues on my vostro 1500 in 64 and 32 bit versions. I've tried multiple versions of the the nvida driver (including the latest from the nvidia website), and I've had no success in getting it working.

---

### Post by tenmoi on 2008-06-19
Read the last post on this thread. It may help you out.
[http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043)

---

### Post by hitmanh on 2008-06-19
> **tenmoi said:**
> Read the last post on this thread. It may help you out.
[http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043)

Yes, that worked :D Thanks :guitar:

Matt

---

