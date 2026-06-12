---
title: "ATI x1300 radeon mobility fgl_glxgears dosn't work"
date: 2008-11-02
forum: General Help
---

### Post by Hrobak on 2008-11-02
Hey! 
i've installed ubuntu's ati driver,it seems work well but when i try to do fgl_glxgears it says : 

*******@desktop:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Segmentation fault
*******@desktop:~$ 

so i cant test my FPS. is here any other  way to make sure that opengl is working?

---

### Post by FaizanKazi on 2008-11-13
Same here... using Ubuntu 8.10 with an x1400 and I enabled the Ati Restricted Drivers

---

### Post by houn2000 on 2008-11-18
Still nothing on this?  I had fglrx working perfectly, then had to reinstall due to a grub issue.  Now, the ati driver does not work at all.  I've tried reinstalling twice, both the same way as before, still nothing.  Getting ready to smash this video card into dust, and buy something of the nvidia flavor.

---

### Post by houn2000 on 2008-11-18
Hrobak: another way to test opengl is to type fglrxinfo at the command line.  Your output should look something like this:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 1.4 (2.1.8087 Release)

What terminal are you running fgl_glxgears from?  I am getting seg faults when running from gnome-terminal (the default in Ubunutu) but everything works fine with xterm.

---

### Post by Marius Derekus on 2008-11-18
Check this out, it has list of a bunch of ati drivers. Maybe yours is in here. I downloaded my graphics driver form here and i don't have any problems (exept for the fact that i also downloaded compiz-switch to easily enable/disable compiz since it will interfere with your graphics sometimes. It causes mine to blink a little.)

---

### Post by Marius Derekus on 2008-11-18
houn2000 just showed me that they have his driver (ATI Radeon HD 4800 series.) They have that graphics card driver at the link i gave you.

---

