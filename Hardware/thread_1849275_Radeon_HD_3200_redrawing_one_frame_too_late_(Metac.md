---
title: "Radeon HD 3200 redrawing one frame too late (Metacity)"
date: 2011-09-24
forum: Hardware
---

### Post by mik01aj on 2011-09-24
Hi,

I'm using Ubuntu 11.04 (natty) with classic GNOME desktop. My windowmanager is Metacity with compositing enabled, and the problem is that when I use app which draws things on screen using OpenGL (for example GIMP, Blender or Hugin), the screen is drawn with a delay of one frame. And while this probably wouldn't matter in games, it is a problem in applications, which redraw their screen on demand. So, for example, I switch view to top in Blender, and then I have to do something on the screen to see the result. It is quite annoying.

I noticed that it happens only when I'm using Metacity's compositing. When I disable it, it works just fine. I also noticed that I didn't have this problem before I instaled propietary ATI drivers. (I don't know what drivers I used before, though).

My graphics card is ATI Radeon HD 3200, in my Lenovo X100e laptop.

My /etc/X11/xorg conf file is very short, and I'm not sure if it's really used by the X server. I can psate it here if needed.

---

