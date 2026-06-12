---
title: "amdgpu-pro drivers not working - desktop only on embedded video"
date: 2018-02-13
forum: Hardware
---

### Post by nathanieltagg on 2018-02-13
Dear Community,
I've been searching for a resolution online, but nothing seems to fit.

I've got a fresh install of Ubuntu 16.04, and I have successfully installed the proprietary AMDGPU-PRO drivers (amdgpu-pro-17.50-511655).  
I have a Dell server machine with both a built-in video card and a PCI-e AMD HD 7700 series card set up for 6-monitor display. 

However, on graphical startup, I get only Ubuntu logos on the 6 AMD montitors, and the desktop appears on the built-in display monitor (the one monitor I _don't_ need). 

I can't seem to figure out how to get the desktop appearing on the other screens. I'd like to use opengl-enabled apps (specifically WebGL) to display some cool stuff.

Here is my Xorg.0.log file:
[https://gist.github.com/anonymous/0f510d0e166ebcd5c479d20558080ad3](https://gist.github.com/anonymous/0f510d0e166ebcd5c479d20558080ad3)
I can't figure out where the problem is.  It seems to recognize the device and all 6 monitors.. and then ignores it all and uses the builtin monitor afterward.

I've tried adding an xconf.org.conf file, but that just kills the internal screen. It's possible to disable the built-in video in BIOS, but previous attempts (with other installs) just caused the computer to be unusable and I had to hard-jumper the motherboard to recover (which is awkward given the 6-screen setup).

Any ideas how to proceed?

---

