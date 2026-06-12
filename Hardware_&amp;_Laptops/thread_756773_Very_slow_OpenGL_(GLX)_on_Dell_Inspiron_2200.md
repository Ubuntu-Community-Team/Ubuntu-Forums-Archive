---
title: "Very slow OpenGL (GLX) on Dell Inspiron 2200"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by Speels on 2008-04-16
Hello,
I am running Ubuntu 7.10, and everything is running fine except for 3d games like Warsow. These games run, but unplayably slow. 
I've followed these instructions: [http://wiki.linuxquestions.org/wiki/OpenGL#Troubleshooting_3D_hw_accel](http://wiki.linuxquestions.org/wiki/OpenGL#Troubleshooting_3D_hw_accel)
and all seems fine :confused:

When I run glxgears I got around 60fps

The only thing I can think of atm is either the drivers do not work well, or I need my bios flashed...
-edit- the videocard is an Intel 915, and the bios is revision 03

---

### Post by Speels on 2008-04-17
*bump*
Nobody? :confused:

---

### Post by aschiro on 2008-04-20
If you are getting 60fps on glxgears, then the drivers are behaving like they should.  Which games are you having trouble with?  I would look at those games and look to make sure that they are running in opengl mode.  For example, if you are running WOW in wine, you will have to have opengl set in the wtf/Config.wtf with the line SET gxApi "opengl", also if it is wow under wine, refer to this page....[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I hope some of this helps.

---

### Post by Speels on 2008-04-23
Not using wine, just playing games like Warsow

---

