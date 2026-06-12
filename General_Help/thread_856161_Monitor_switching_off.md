---
title: "Monitor switching off"
date: 2008-07-11
forum: General Help
---

### Post by ZaM0 on 2008-07-11
Hello!
Recently I tried to boot the Ubuntu Live CD(7.10). It seems that it loads the kernel, but when it goes to the graphical environment, I hear the welcome sound and the monitor switches off (by the way, in the beginning, I see the background and the mouse, it stands for few seconds)

I tried the same with VMWare. It looks like the GUI is in larger resolution than my monitor supports. Whatever resolution I choose(the VGA menu), it's all the same.

Probably when I boot it, Ubuntu uses too large resolution and my monitor goes off.

Here are my specs: 
AMD Sempron 3300+ 64
RAM DDR400 1 GB
NVIDIA GeForce 7300LE 256MB

Screen: Philips 170s (max resolution: 1280x1024)

How could I boot the Live CD with chosen screen resolution?

---

### Post by mzhb@mac.com on 2008-07-11
You have to manually set the xorg.conf file in /etc/X11/xorg.conf

---

### Post by ZaM0 on 2008-07-11
Could I do it w/o installing it on my hard drive?

---

### Post by MasterXandrex on 2008-07-11
Try this, when you boot the live CD and your monitor turns off press Crtl+Alt+F1 -- this should take you to a virtual terminal, if it doesn't there are further problems and you probably have a setup that does not work with the live CD and will need to use the alternate installer. Login and then run the following

```

sudo /etc/init.d/gdm stop

```
this kills the display. Then run

```

sudo dpkg-reconfigure xserver-xorg

```
and follow the wizard -- it's fairly simple. When you get the the resolution set, set only one resolution you know your monitor will support.

then run 
```

sudo /etc/init.d/gdm stop

```
to restart the display.


Xan

---

### Post by ZaM0 on 2008-07-12
Thank you for the help, but I recently tried to boot it - and it just went ok - the monitor didn't go off! The picture seemd moved a bit to right, and the resolution was the native one - 1280x1024, 60Hz. Maybe that's not the problem... I gonna try to boot it again later...

---

