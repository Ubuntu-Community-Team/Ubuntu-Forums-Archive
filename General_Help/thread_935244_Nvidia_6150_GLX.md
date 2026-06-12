---
title: "Nvidia 6150 GLX"
date: 2008-10-01
forum: General Help
---

### Post by auggy74 on 2008-10-01
Okay, I'm...running into some problems with my video, and I'm hoping I can get an answer or a sense of direction.

The summary right now is I've done a lot of install/uninstall of the nvidia drivers, and somewhere along the way, I hosed glx. Here's the results of glxinfo, glxgears, and  dpkg -l | grep nvidia.

```

~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

~$ dpkg -l | grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.13-19.45                   NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  nvidia-glx-new-dev-envy                    173.14.12+2.6.24.503-503.30              NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  nvidia-glx-new-envy                        173.14.12+2.6.24.503-503.30              NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                        NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   169.12+2.6.24.13-19.45                   NVIDIA binary 'new' kernel module source
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1                  Tool of configuring the NVIDIA graphics driv


```

This is the part where you guys giggle at me. Feel free, I am.

Having said that, is the best option here "Blow it up and start over"? 

Many thanks.

---

### Post by auggy74 on 2008-10-01
Oh, and how do I kill a dupe?

---

### Post by briandu on 2008-10-01
OK to start off you have to consider installing NVIDIA. Then add it in again via the system/admin/hardware drivers.

So go to your synaptic and remove nvidia first

---

### Post by auggy74 on 2008-10-01
Interesting - hardware drivers is blank.

I did try installing the 173 drivers from the nvidia website, however when I rebooted, I got a black screen of death for my trouble.

---

### Post by fooman on 2008-10-01
have you tried envyng? its in synaptic or from a terminal:

```
sudo apt-get install envyng-gtk
```

after its installed,  find it in applications > system tools

---

### Post by auggy74 on 2008-10-01
Tried Envy....same result. It installs, but then when I start gdm, black screen of irritation.

---

