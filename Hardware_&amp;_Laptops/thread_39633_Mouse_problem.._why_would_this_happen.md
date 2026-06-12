---
title: "Mouse problem.. why would this happen?"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by VincentP on 2005-06-05
I had Ubuntu installed before, no problems whatsoever.  Then I tried a few other distros, didn't like them at all.  This included MEPIS.  When I installed MEPIS, it wouldn't load my mouse when X started.  The cursor would be there, but it wouldn't move.  The way I got it working was to unplug and replug the mouse.  Then it worked fine.  When I reinstalled Ubuntu, I started to have the same problem.  I dont use a USB mouse, it's the normal mouse port.  Last time I had Ubuntu, it worked fine, but now every time X starts I have to replug the mouse.

On another note: apt cannot find w32codecs, or gstreamer0.8-lame.  I know this is the wrong section, but it seems weird, because those are in the ubuntuguide, and this worked fine before too.  

Any ideas?

---

### Post by Mez on 2005-06-06
open up a console (ctrl +alt+ f1) then login..

do the folowing

```
sudo cat /etc/input/mice
```

Input your password,, as it asks for, then move yuour mouse.

Hopefully you should see some sort of output on the screen

hit ctrl+c to finish this

If you see outut on the screen, it means that your mouse is being detected properly, and all you need to do is reconfgiure X to use it

```
sudo dpkg-reconfigure xserver-xorg
```

When it gives you the option to slect which device your mouse is connected to, use /dev/input/mice and all should work once you restart X

Hope this helps!

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=VincentP]I had Ubuntu installed before, no problems whatsoever.  Then I tried a few other distros, didn't like them at all.  This included MEPIS.  When I installed MEPIS, it wouldn't load my mouse when X started.  The cursor would be there, but it wouldn't move.  The way I got it working was to unplug and replug the mouse.  Then it worked fine.  When I reinstalled Ubuntu, I started to have the same problem.  I dont use a USB mouse, it's the normal mouse port.  Last time I had Ubuntu, it worked fine, but now every time X starts I have to replug the mouse.

On another note: apt cannot find w32codecs, or gstreamer0.8-lame.  I know this is the wrong section, but it seems weird, because those are in the ubuntuguide, and this worked fine before too.  

Any ideas?[/QUOTE]
 For gstreamer-lame: do you have backports repositories enabled? (See latest version of ubuntuguide)

---

