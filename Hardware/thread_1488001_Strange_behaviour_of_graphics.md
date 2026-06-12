---
title: "Strange behaviour of graphics"
date: 2010-05-19
forum: Hardware
---

### Post by Guyik on 2010-05-19
Hello, everybody.

I have always had this problem since I installed Ubuntu 8.04 in my Acer Extensa 5220 with a Mobile Intel X3100 (i965) graphic card.

It consist of some things:


[LIST=1]
[*]When video is being played and I move the window where it is, the film goes on playing where it were, and doesn't move with the window until I stop moving it.
[*]Sometimes, I think only when 3D acceleration is in use, the image stands where it was although I move the window. It's not removed until I put another window on where the static image is. I cannot use pymol because of this.
[*]GnomeChess doesn't work in 3D mode. It uses a lot of CPU, when I click the 2D view appears, and after a few moves the chess game disappear (the screen gets soft blue).
[*]I cannot watch a video with totem (neither with VLC) if I have YouTube opened on a Firefox window. The video player stands on seccond 0, and plays frame per frame (I think 1 frame per sec) and it turns slower. I have to be very careful, because if this happens, I have to reboot before I can play a video again. Music cannot either be played.
[*]A lot of CPU is used when some advertisements are being shown in a web that is opened with Firefox, and the PC is very slow when this occur.
[/LIST]
I have been looking for solutions for my graphic card, and I found this:
    In order not to have to install "**xserver-xgl**", which is supposed to make a lot of bugs, I deleted the black list from **/usr/bin/compiz **and used the **X Window System (No Xv)**  option in "**gstreamer-properties**" (executing it in a terminal). Nothing got better, instead, videos were seen in big pixels.

Any ideas?

Thank you very much.

---

