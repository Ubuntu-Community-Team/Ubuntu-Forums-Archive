---
title: "Intel 3000 graphics - Mini Display Port"
date: 2012-06-22
forum: Hardware
---

### Post by caf209 on 2012-06-22
Can someone who has this working post the output of inxi -G ([http://code.google.com/p/inxi/](http://code.google.com/p/inxi/))
```
inxi -G
```

or of
```

dpkg -l | \grep mesa
dpkg -l | \grep xserver

```

I've been trying to get my Intel HD 3000 graphics to support 1920x1080 on my external monitor through my Mini DisplayPort.

My output of inxi -G
> 
[HTML]Graphics:  Card: Intel Device 0126 
           X.Org: 1.7.6 drivers: intel (unloaded: vesa,fbdev) Resolution: 1360x768@59.8hz, 1400x1050@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GEM 20100330 DEVELOPMENT GLX Version: 2.1 Mesa 7.10.3[/HTML]


My output of dpkg -l | \grep mesa
> 
[HTML]obs@caf209-think-ubuntu:~$ dpkg -l | \grep mesa
ii  libegl1-mesa                             7.10.3-0ubuntu1~lucid3                          free implementation of the EGL API -- runtim
ii  libegl1-mesa-dbg                         7.10.3-0ubuntu1~lucid3                          free implementation of the EGL API -- debugg
ii  libegl1-mesa-dev                         7.10.3-0ubuntu1~lucid3                          free implementation of the EGL API -- develo
ii  libegl1-mesa-drivers                     7.10.3-0ubuntu1~lucid3                          free implementation of the EGL API -- hardwa
ii  libegl1-mesa-drivers-dbg                 7.10.3-0ubuntu1~lucid3                          free implementation of the EGL API -- driver
ii  libgl1-mesa-dev                          7.10.3-0ubuntu1~lucid3                          free implementation of the OpenGL API -- GLX
ii  libgl1-mesa-dri                          7.10.3-0ubuntu1~lucid3                          free implementation of the OpenGL API -- DRI
ii  libgl1-mesa-dri-dbg                      7.10.3-0ubuntu1~lucid3                          Debugging symbols for the Mesa DRI modules
ii  libgl1-mesa-glx                          7.10.3-0ubuntu1~lucid3                          free implementation of the OpenGL API -- GLX
ii  libglu1-mesa                             7.10.3-0ubuntu1~lucid3                          Mesa OpenGL utility library (GLU)
ii  mesa-common-dev                          7.10.3-0ubuntu1~lucid3                          Developer documentation for Mesa
ii  mesa-utils                               7.7.1-1ubuntu3                                  Miscellaneous Mesa GL utilities
[/HTML]


My output of dpkg -l | \grep xserver
> 
[HTML]
ii  x11-xserver-utils                        7.5+1ubuntu2.1                                  X server utilities
ii  xserver-common                           2:1.7.6-2ubuntu7.11                             common files used by various X servers
ii  xserver-xorg                             1:7.5+5ubuntu1.1                                the X.Org X server
ii  xserver-xorg-core                        2:1.7.6-2ubuntu7.11                             Xorg X server - core server
ii  xserver-xorg-input-all                   1:7.5+5ubuntu1.1                                the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-evdev                 1:2.3.2-5ubuntu1                                X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                 1:1.5.0-1                                       X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics             1.2.2-1ubuntu4                                  Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse               1:12.6.5-4ubuntu2                               X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-input-wacom                 1:0.10.5-0ubuntu4                               X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                   1:7.5+5ubuntu1.1                                the X.Org X server -- output driver metapack
ii  xserver-xorg-video-apm                   1:1.2.2-1                                       X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                   1:0.7.2-1                                       X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                   1:6.13.0-1ubuntu5                               X.Org X server -- AMD/ATI display driver wra
ii  xserver-xorg-video-chips                 1:1.2.2-1                                       X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                1:1.3.2-1ubuntu1                                X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                 1:0.4.1-1ubuntu1                                X.Org X server -- fbdev display driver
ii  xserver-xorg-video-i128                  1:1.3.3-1                                       X.Org X server -- i128 display driver
ii  xserver-xorg-video-intel                 2:2.15.0~lucid~ppa9                             X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-mach64                6.8.2-2                                         X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                   1:1.4.11.dfsg-2ubuntu1                          X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic              1:1.2.4-2                                       X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau               1:0.0.15+git20100219+9b4118d-0ubuntu5           X.Org X server -- Nouveau display driver (ex
ii  xserver-xorg-video-nv                    1:2.1.15-1ubuntu3                               X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome            1:0.2.904+svn827-1                              X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                  6.8.1-2ubuntu1                                  X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                1:6.13.0-1ubuntu5                               X.Org X server -- AMD/ATI Radeon display dri
ii  xserver-xorg-video-rendition             1:4.2.3-1                                       X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                    1:0.6.3-1                                       X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge               1:1.10.4-1                                      X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                1:2.3.1-1ubuntu1                                X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion         1:1.7.3-1                                       X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-video-sis                   1:0.10.2-2                                      X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                1:0.9.3-1                                       X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                  1:1.4.3-1                                       X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident               1:1.3.3-1                                       X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                 1:1.2.3-1                                       X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                   1:0.2.0-4                                       X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-video-vesa                  1:2.3.0-1ubuntu1                                X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                1:10.16.9-1                                     X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                1:1.2.3-1                                       X.Org X server -- Voodoo display driver
[/HTML]


---

### Post by archimedesmp on 2012-06-23
> **caf209 said:**
> 
I've been trying to get my Intel HD 3000 graphics to support 1920x1080 on my external monitor through my Mini DisplayPort.

Hi caf209, I can not see how your question is related to my original post.
You might want to create a new topic.

Edit:
I requested the mods to move your post to a new topic, as this seems the easiest thing to do.
This is *not* to be bad at you or something like that, this is just about keeping different discussion threads on different topics in, well, different topics/threads ;-)

@Mod: Can you create the tag "hd p3000" for this topic? This is the name of the graphics controller in some of the Xeon CPUs (note the additional p, that's for... uhm... professional?)

---

### Post by coffeecat on 2012-06-23
@caf209, I've moved your post, and the response, into its own thread and given it what I hope is a suitable title.  Your problem is not the same as the OP was posting about in the original thread - only the graphics card was the same. Please start your own threads.

---

