---
title: "Intel integrated graphics: 3D acceleration doesn't work."
date: 2015-01-11
forum: Hardware
---

### Post by rewolff on 2015-01-11
I have a new system on which I installed 14.10. But some 3D stuff doesn't work or is very slow. When I go to the Intel site for graphics drivers, they have a driver 1.0.7 that is for 14.04, and when asked they say: that's because 14.10 already has the latest intel drivers. 

lspci shows: 
```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

```
and glxinfo shows lots of "mesa". 
```
assurancetourix:~# glxinfo |grep string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.0
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.3.0
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.3.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0

```So... What am I missing? What package do I need to install? I thought the "fresh install" would detect my graphics and install the right drivers, but apparently that didn't happen quite well enough....

---

### Post by buzzingrobot on 2015-01-11
Yes, an active Intel GPU is detected on install and the appropriate driver is used.  For 14.10, the current driver (xserver-xorg-video-intel) is 2:2.99.914-1~exp1ubuntu4.1.  Mesa is at 10.3.0 on 14.10, so you have the appropriate packages there.

The Intel Haswell GPU is fine for desktop environments and some games, but more demanding 3D needs call for using an Nvidia or AMD card.

---

### Post by rewolff on 2015-01-11
I work with simple things in openscad. Previously (on 14.04, other harddrive, other video system), that worked just fine. Now I get the initial view from openscad, but changing the view doesn't ... change the view. 

Previously, google earth would work. It now shows me a black "sky" (no earth). 

In the old days if you got "mesa" in GLXinfo output, you'd be using software rendering, This is no longer the case? 

Together with the new system I got a new video card, but I haven't installed it. Thinking the current setup should work "reasonable" and I have a bit of an aversion of having to take things apart again... :-)

---

### Post by buzzingrobot on 2015-01-11
I *think*, not sure, you'd see 'llvmpipe' showing up if software rendering was in use.

In Unity, Systems Settings->Details will tell you what graphics the system thinks it's using.

Here, with Intel Haswell, on the Ubuntu Gnome 15.04 development release, I see this from glxinfo:
```
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.2
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.3.2
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.3.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0

```

---

### Post by Yellow Pasque on 2015-01-11
The glxinfo is correct. You used to see "Mesa" in the OpenGL vendor string when you didn't have hardware acceleration, but "Mesa DRI" is what you want to see for an Intel GPU. What you're describing sounds like bugs :(

If you want to try updated drivers, see: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=utopic](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=utopic)

---

