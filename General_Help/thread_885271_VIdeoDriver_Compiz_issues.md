---
title: "VIdeoDriver /Compiz issues"
date: 2008-08-09
forum: General Help
---

### Post by justinreeves16 on 2008-08-09
-I had some video issues , wiped system, reinstalled Hardy.
-Enabled Nvidia under restricted hardware drivers, gained resolutions up   to 1024*768. Desktop  effects worked
-(needed 1280*1024min.)used displayconfig-gtk to set monitor from Plug and play to  Current, Viewsonic E70fb.
-gained resolution over 1280*1024-Now no desktop effects work.
and seems some games and my 3D software(houdini) dosnt work(there all OpenGl dependent)

-Tried changing back to 1024*768, and setting monitor back to plug and play, still no Desktop effects.

-Compiz-check says install correct driver for video card, cant find it.

Leadtek Winfast A250 / GeForce 4 Ti4600

I thought the correct one was installed, confused, need help.

---

### Post by Mgiacchetti on 2008-08-10
you may wish to read this, just to see if there's anything in there you can try.
[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

You may have to go to the hardware drivers applet and reinstall it, (i have no clue how to do this mind you, just an idea)

Also if you can find the package, remove and --purge then try reinstalling might help   

I have a 6150 LE and am running nvidia-glx-new and nvidia-kernel-common

that may be a start for you.


Hope it helps.

---

### Post by semi-noob on 2008-08-21
I'm sure that this is a dumb question, but after searching the forums, I cannot figure out the correct key words to get the answers I need. I am running hardy heron 8.0.4, I finally got the nvidia driver to kind of work. The issue now; is that I set up the computer for 1024-768 resolution, and a quick check of the /etc/X11/xorg.conf file shows that I am set up for 1024X768 resolution. However, whenever the computer boots up, the main screen, and all of the windows are set to 800X600 resolution. The other part of this that might shed some insight into what is going on is that under system>preferences>screen resolution, I have a program that allows me to change the resolution, it shows that I am set on 800X600, and does not allow for anything higher. I have been fighting with this for almost two days now, so any input would be greatly appreciated.

---

