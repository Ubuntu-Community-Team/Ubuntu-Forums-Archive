---
title: "First Time User - Intel Video Drivers Installation"
date: 2010-07-14
forum: Hardware
---

### Post by woojoo on 2010-07-14
Hello Ubuntu Community,

I'm a second year Cal student (Go Bears!) who just got a new nettop for academic use and decided to run Ubuntu on it for performance and enhancements. I've been a long-time Mac user for the last five years and switching to Ubuntu has been OK so far.

I've run into some problems installing drivers for the graphics card and I'm wondering if you guys can help me out a little bit. It seems the default drivers with 10.04 only supports up to 832x624, which doesn't look so great on my 1080p monitor.

My nettop is a Foxconn NT510 with an Intel GMA5130 graphics card. I've googled solutions online and searched the forums, but to no end. I'm trying to install graphics drivers from [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/), and I've downloaded the 2D drivers on this page: [http://intellinuxgraphics.org/2010Q2.html](http://intellinuxgraphics.org/2010Q2.html)

I've then cd'ed to the downloaded directory and typed ./configure, it said that I'm missing xorg server, so I've googled that and typed in the following commands:

```
apt-get build-dep xserver-xorg-core
sudo apt-get build-dep xserver-xorg-video-sis
```

but now I'm stuck at a dead end, I'm still getting the following error:

```
checking for DRM... configure: error: Package requirements (libdrm >= 2.4.21) were not met:

Requested 'libdrm >= 2.4.21' but version of libdrm is 2.4.18

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRM_CFLAGS
and DRM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Can someone help me out here?

---

### Post by woojoo on 2010-07-15
I just solved the problem. For anyone who might have it in the future:

Download libdrm from here and follow the README instructions to install, then restart.

[http://dri.freedesktop.org/libdrm/](http://dri.freedesktop.org/libdrm/)

Then download the Resolution Changer GUI tool from Applications -> Ubuntu Software Center to restore to glorious 1080p. Good luck.

Thanks, Ubuntu community, for absolutely nothing. No, I'm serious. Your nonresponse has prompted me to look for solutions myself and now I've learned how to use make (a little bit). Horray for fixing things by yourself!

---

