---
title: "Mobility Radeon HD2600 + Catalyst 9.1, problems"
date: 2009-02-01
forum: Hardware
---

### Post by centos on 2009-02-01
Hello everyone, I've been experiencing problems with this card (and also with X1250 which is integrated in my Asus F3Ka laptop) since I first installed proprietary drivers. Now I use new 9.1 so I'll describe problems I have with it and hope that someone will help because it's driving me crazy.
First of all, I do not use Compiz.

1) I like subtitle quality in SMPlayer using SSA subs with gl output. But gl output  is not working well (not just here), video flickers and it is unwatchable while there's any other window over it. There's a "solution" in using X11 output and software upscaling of video but it increases CPU usage too much.

2) Google Earth does the same thing as videos in gl output so I think it is openGL-related problem too

3) with these new drivers (default proprietary drivers worked good in this) is also gstreamer unusable, it is not the same case as in gl output, it just creates black boxes all around an app that is using gstreamer. That means Totem and sadly also my favourite Gnome Subtitles.

I tried to add
```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "on"
Option "TexturedVideo" "off"
```
into xorg.conf (should correct flickering), caused just black screen after boot.

I tried radeonhd drivers from repositories, gl worked fine but performance was too low.

I'd like to know if anyone with this card is experiencing these problems too, also I'd like to know if anyone has same card and works fine for him and of course if anybody has solution for this. Thanks in advance.

---

