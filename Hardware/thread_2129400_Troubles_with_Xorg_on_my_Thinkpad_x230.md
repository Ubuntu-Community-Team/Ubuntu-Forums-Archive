---
title: "Troubles with Xorg on my Thinkpad x230"
date: 2013-03-26
forum: Hardware
---

### Post by Gorith on 2013-03-26
Hi,

I have some serious troubles with my X server. I use a Lenovo Thinkpad x230 with corei7 cpu and no additional graphics card, hence I use the intel HD4000 integrated graphics. I have installed Ubuntu 12.10 64 bit, everything is up to date. When I start up the computer, usually my X server crashes. I can switch though to the console using ctrl+alt+F1 and kill the process manually. Then it starts automatically again and works properly (I suppose in fallback mode).

Here is an excerpt of the last log-file:
[...]
[     4.710] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.710]     Entry deleted from font path.
[     4.710] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     4.710]     Entry deleted from font path.
[...]
[     4.715] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     4.724] (II) Module shadow: vendor="X.Org Foundation"
[     4.724]     compiled for 1.13.0, module version = 1.1.0
[     4.724]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.724] (==) Depth 24 pixmap format is 32 bpp
[     4.956] (==) FBDEV(0): Backing store disabled
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[     4.957] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

Yeah, and thats probably where it hangs.

Here is my installed driver:
ii  xserver-xorg-video-intel-lts-quantal           2:2.20.9-0ubuntu2~precise2                       amd64        X.Org X server -- Intel i8xx, i9xx display driver


I would appreciate any help on the issue.
Thx in advance.

---

### Post by ddrake_ on 2013-04-26
I just encountered the same problem. The (very unexpected) solution: resinstall gsettings-desktop-schemas. The root of the problem (for me, at least) was that lightdm was crashing -- look in /var/log/lightdm/x-0-greeter.log. Does it say "no gsettings schemas are installed on the system"?

These pages led me to the solution: 

[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2246](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2246)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

I hope this helps someone.

---

