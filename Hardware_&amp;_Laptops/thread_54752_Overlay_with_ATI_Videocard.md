---
title: "Overlay with ATI Videocard"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by rogeriovinhal on 2005-08-05
I have a 9600XT Ati Radeon videocard fully configured, (fglrxinfo tells it is a 9600XT and glxgears and fgl_gears work fine with high FPS).

I have TV-out working, but for some reason I can't make videos appear in it. In Windows it should be configured just going in the Video-card settings and cheching Overlay in Fullscreen mode.

How can I do like that? Everytime I run a video in Ubuntu, I want it to go fullscreen on TV. If that can't be done, i should be happy just with it appearing in TV at all.

I have already tried control-panel, but that has nothing to do with Overlay.

---

### Post by rogeriovinhal on 2005-08-07
Help again, I am trying, but no results... No one ever done this?

---

### Post by rogeriovinhal on 2005-08-08
Up

---

### Post by vruum on 2005-08-09
I think it's a problem with ati and the Xv overlay, you could tryk changing the video output in your mediaplayer (xine/mplayer) to openGL or xshm. I don't know if there's a way to make ati and xv work together properly, but xine and OpenGL works for me.

---

### Post by rogeriovinhal on 2005-08-13
xshm works on TV, but doesn't maximize videos when I open then.
Just shows everything on TV like it is on monitor.

But even so, is there anyone that made it work on XV? I think xshm is a little slower and with worse graphics, and I have some problems with Vsync, because sometimes the image is "cutted" due to fast movement of the camera...

---

### Post by rogeriovinhal on 2005-08-22
Up.

---

