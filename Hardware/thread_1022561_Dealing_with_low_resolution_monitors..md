---
title: "Dealing with low resolution monitors."
date: 2008-12-26
forum: Hardware
---

### Post by cmat on 2008-12-26
I recently installed Xubuntu on a desktop. The PC it was installed on has a monitor with a really small screen size. The Nvidia driver restricted itself to 640x480 and xvesa allowed it to reach 800x600. This is okay but I lost hardware acceleration + some dialogues and forms go off screen making the user experience difficult. The PC isn't that old. The monitor can handle higher resolutions but the drivers wont allow for them.

Is there a way to override the set limits? I know this monitor also horribly corrupts the image of the usplash since it was installed on a PC with a regular sized monitor (to me at least). 

Questions:

0. How do I override the set limits of the driver?
1. How do I change the resolution of usplash?

---

### Post by cariboo on 2008-12-27
If the monitor in question is a crt type monitor you may have to set the horizontal and vertical refresh rate in /etc/X11/xorg.conf. You should be able to get the horizontal and vertical refresh rates by searching google for the monitor make and model.

Jim

---

### Post by cmat on 2009-02-07
I went back there today since the owners have been out of the country for a few weeks. It didn't work. The entries are there in xorg.conf however when I change them nothing happens.

Also my usplash resolution is really messed up. It works fine on shutdown but on boot-up it's a garbled mess.

---

### Post by 00b00nt00 on 2009-02-08
cmat,

Please post some more information about your system.

Things like:

Monitor size, model and manufacturer, graphics card model and manufacturer.

You say the monitor is small, allowing only 640*480. That would make it seem like a 12" monitor, which hasn't been made since the early 1990s or even earlier!

---

