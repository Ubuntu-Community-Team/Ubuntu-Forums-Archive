---
title: "Nvidia GeForce FX5200"
date: 2009-08-03
forum: Hardware
---

### Post by jpcjr on 2009-08-03
I am trying to install the Nvidia driver for my graphics card and get errors, I already closed X.

The log is below:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug  3 12:27:17 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '2647'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com]("http://www.nvidia.com").
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").

---

### Post by realzippy on 2009-08-03
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200)

---

### Post by jpcjr on 2009-08-03
Thanks I will try it, I am waiting for it to download the drivers.

UPDATE: It worked, thanks.

---

### Post by ckchappell on 2009-12-24
Rather than starting a new thread I guess I'll continue with this one since it's open.

I have the same card and cannot get even the "Normal" effects. I tried the link in the previous thread and still nothing.

I'm trying really hard to enjoy Ubuntu but this is getting very frustrating. I know even though the computer is a little old, I've upgraded the RAM and video card and it should handle even the Extra visual effects.

Not sure what to post here to get some help:

EnvyNG shows I have 173.14.20 driver installed

In the BIOS, I have disabled the onboard video, but "lspci | grep VGA"shows: 

[I]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

01:02.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)[/I]

xorg.conf seems pretty bare:

[I]Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

[/I]

Any help would be appreciated.

Merry Christmas

---

