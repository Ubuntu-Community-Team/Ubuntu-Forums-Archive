---
title: "[SOLVED] I can't watch  a video with Compiz"
date: 2008-11-05
forum: General Help
---

### Post by qwe99 on 2008-11-05
I can't watch a video when Compiz is active. When the compiz disabled I can watch the videos.(I try it with a lot of different codecs and different players). The video is flashing evertime (2 times per second :( ) . I had not the same problem with 8.04. My vga ( ATI Radeon HD 3850 ) was installed automatically (It had found it from internet) . I try to open the player from terminal and I start a video, I looked to terminal if give an error but no...

command :

glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 3850
--------------------------------------
lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV670PRO [Radeon HD 3850]

---

### Post by qwe99 on 2008-11-05
I solveD the problem. But just for VLC. From the setting of video modules, I cahnge the onput in "X11 video onput". and the problem solved for VLC

---

### Post by sdowney717 on 2008-11-05
you can change it to x11 for other players as well

---

### Post by sisco311 on 2008-11-05
> **qwe99 said:**
> I solveD the problem. But just for VLC. From the setting of video modules, I cahnge the onput in "X11 video onput". and the problem solved for VLC

for totem:
press Alt+F2 and type:
```
gstreamer-properties
```

go to video tab -> Default output -> Plugin and select x11

for mplayer:
edit the *~/.mplayer/config* file:
```
gedit ~/.mplayer/config
```
and add this line:
> vo=x11or
> vo=gl
or
> vo=gl2

---

