---
title: "still having issues with no GLX"
date: 2010-02-09
forum: Hardware
---

### Post by mercury00 on 2010-02-09
I'm having issues with not being able to use opengl with my Quadro 4 580 xgl card in ubuntu 8.04 LTS. 

when I run glxinfo, I get a lot of:

Xlib:  extension "GLX" missing on display ":0.0".

this is after installing the nvidia drivers (hardware drivers section of administration), or after installing with envyNG, or after installing from command line, etc. etc. etc. and also etc.

The xorg log file gives me some of this too:

 Failed to initialize the GLX module; please check in your X log file that the GLX module has been loaded in your X server, and that the module is the NVIDIA GLX module.  If you continue to encounter problems, Please try reinstalling the NVIDIA driver.

Please someone help me, (goodgam this is really making me love ubuntu).

---

### Post by mercury00 on 2010-02-11
seriously?  there is no way for me to actually use this graphics card in an updated ubuntu?  what gives?

---

### Post by mercury00 on 2010-02-18
OK I temporarily got it working by completely uninstalling and deleting a bunch of files from compiz*.  And reinstalling a bunch of system files.  I had all my glxinfo stuff showing up good, but after a reboot I'm back to square one.  Does anyone read these forums?

---

