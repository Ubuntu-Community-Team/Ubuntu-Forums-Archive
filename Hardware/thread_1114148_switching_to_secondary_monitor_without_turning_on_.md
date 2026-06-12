---
title: "switching to secondary monitor without turning on software opengl"
date: 2009-04-02
forum: Hardware
---

### Post by Los Frijoles on 2009-04-02
I have ubuntu 8.10 with netbook remix installed on my Acer Aspire One. Yesterday I needed to do a lab for one of my cs classes on a linux machine, so I decided to hook my 19" widescreen up to my aspire one and tried to make it work as the primary monitor. This ended up making the virtual desktop double in size and opengl go into software mode which greatly slowed down netbook-launcher and prevented me from opening any programs. I ended up having to go into xorg.conf and fix the display size before the computer would operate properly again.

How can I switch monitors (i.e. turning off the laptop panel and making the larger monitor the main monitor) or prevent opengl from going into software mode?

---

### Post by alfplayer on 2009-04-02
I have a Asus Eee Pc 1000 H with a Intel 945GME video controller (very similar to yours)
 I can't get desktop effects if the width or height of the virtual resolution is higher than 2048 (this is set in /etc/X11/xorg.conf). This is really bad because it means that the sum of the widths and the sum of the heights of the displays can't be higher than 2048 and this means that I can't set my 17 inches monitor at 1280x1024 next to the netbook at 1024x600 (10 inches screen).
 I believe this is a limitation in the maximum texture size of the video controller and that it can't be solved with this hardware (no software solution). This is what I get:
 ```
> glxinfo -l | grep GL_MAX_TEXTURE_SIZE
    GL_MAX_TEXTURE_SIZE = 2048
``` To find out your video controller run *lspci*. It should be the same or similar to mine.
 You can try running compiz from a terminal, you should get something like this:
 ```
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
```You can also try to run *SKIP_CHECKS=yes compiz* to force compiz to run and have the desktop effects available in most of the virtual desktop (there is a way to make it permanent) but I get a white screen in both displays (btw, I hope someone can tell me  why).
 My workaround to have desktop effects with both display at max resolution is to place the monitor above the netbook. This way the virtual display is not so flat and I avoid going over the 2048x2048 limit.
On Easy Peasy (based on Intrepid) I can have the laptop screen and the external screen on or one of them turned off using a keyboard shortcut (the panel is on the external display when both are on).

---

